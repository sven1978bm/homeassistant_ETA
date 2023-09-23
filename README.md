# ETA

ETA Heizkessel in Home Assistant integrieren:

1. Die ETA Heizung einbinden in das eigene Netzwerk
2. Teste die Freischaltung von der ETA Rest mit der URL: http://192.168.178.XXX:8080/user/menu (URL von der ETA Heizung)

# Vorbereitung Home Assistant

1. HACS installieren (wenn der Editor nicht verfügbar ist)
   - installiere den "Config Editor" in Integrationen
     # Neustart Home Assistant, nach fehlerfreier Konfigurations Prüfung
   - installiere den "Config Editor Card" in Frontend
     # Neustart Home Assistant, nach fehlerfreier Konfigurations Prüfung
   - Ergänze in der configuration.yaml den Eintrag: config_editor:
     # Neustart Home Assistant, nach fehlerfreier Konfigurations Prüfung
   - Erstelle das "Editor" Dashbaord
     # Neustart Home Assistant, nach fehlerfreier Konfigurations Prüfung

Jetzt kann die configuration.yaml bearbeitet werden im Editor Dashboard

# Sensoren über den Editor in die configuartion.yaml hinzufügen:

sensor:
  - platform: rest
    name: "ETA Abgas Temperatur"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//48/10391/0/11110/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Warmwasser"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10251/0/11129/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Ladezustand"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10251/0/0/12528
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "%"
  - platform: rest
    name: "ETA Puffer oben"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10251/0/11153/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Puffer mitte"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10251/0/11053/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Puffer unten"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10251/0/11155/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Aussentemperatur"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//48/10241/0/0/12197
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Vorlauftemperatur Heizkreis"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10101/0/11060/0
    value_template: '{{ value_json.eta.value["@strValue"] | replace(",", ".") | float }}'
    unit_of_measurement: "°C"
  - platform: rest
    name: "ETA Heizung"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//120/10101/0/0/12090
    value_template: '{{ value_json.eta.value["@strValue"]}}'
  - platform: rest
    name: "ETA Zündung Automatik aktiviert"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//48/10391/0/0/13205
    value_template: '{{ value_json.eta.value["@strValue"]}}'
  - platform: rest
    name: "ETA Zündung"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//48/10391/0/0/12163
    value_template: '{{ value_json.eta.value["@strValue"]}}'
  - platform: rest
    name: "ETA Frischwasser"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//79/10531/0/11148/2002
    value_template: '{{ value_json.eta.value["@strValue"]}}'
  - platform: rest
    name: "ETA Kessel"
    scan_interval: 120
    resource: http://192.168.178.XXX:8080/user/var//48/10391/0/11108/2002
    value_template: '{{ value_json.eta.value["@strValue"]}}'

# Neustart Home Assistant, nach fehlerfreier Konfigurations Prüfung

