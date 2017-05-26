# timedatectl

This template provides high level based monitoring of ntp based on the timedatectl command.

It is used to get a quick overview of the state of time synchronization independent of 
the underlying mechanism used to sync time.

This template is part of [RaBe's Zabbix template and helpers
collection](https://github.com/radiorabe/rabe-zabbix).

## Template App timedatectl active

### Items 
* NTP enabled (`rabe.timedatectl.ntp.enabled`)
* NTP synchronized (`rabe.timedatectl.ntp.synchronized`)
### Macros

* `{$TIMEDATECTL_MAX_NO_SYNC_TIME}` (default: 60m)
### Triggers

* Warning: NTP not enabled (`{Template App timedatectl active:rabe.timedatectl.ntp.enabled.last()}=0`)

* Information: NTP not synchronized (`{Template App timedatectl active:rabe.timedatectl.ntp.synchronized.last()}=0`)

* Warning: NTP not synchronized for more than {$TIMEDATECTL_MAX_NO_SYNC_TIME} (`{Template App timedatectl active:rabe.timedatectl.ntp.synchronized.last(,{$TIMEDATECTL_MAX_NO_SYNC_TIME})}<1`)
## UserParameters

| Key | Description |
| --- | ----------- |
| rabe.timedatectl.ntp.enabled | "NTP enabled" yes/no value from timedatectl output |
| rabe.timedatectl.ntp.synchronized | "NTP synchonized" yes/no value from timedatectl output |

## License
This template is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, version 3 of the License.

## Copyright
Copyright (c) 2017 [Radio Bern RaBe](http://www.rabe.ch)
