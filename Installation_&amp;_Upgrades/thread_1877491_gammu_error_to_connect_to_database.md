---
title: "gammu error to connect to database"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by arturo322 on 2011-11-08
I've typed in the command:
gammu-smsd


and I've got this error:
gammu-smsd[2214]: Error connecting to database!
gammu-smsd[2214]: Error code: 1045, Error: Access denied for user 'root'@'localhost' (using password: YES)
gammu-smsd[2214]: Initialisation failed, stopping Gammu smsd: Unknown error. (UNKNOWN[27])


This is my gammu-smsdrc
# Configuration file for Gammu SMS Daemon

# Gammu library configuration, see gammurc(5)
[gammu]
# Please configure this!
port = /dev/null
connection = at
# Debugging
#logformat = textall

# SMSD configuration, see gammu-smsdrc(5)
[smsd]
Service = mysql
PIN = 1234
Logfile = syslog
User = root
Password = rmbv322
PC = localhost
Database = smsd


Ive tried loading my mysql client via the command
mysql -u root -p
password: rmbv322

currently using Ubuntu10.10
Lampp(xampp for linux) for my php mysql and apache
using Hwawei usb modem(Globe tatoo as gsm modem)

and it connected successfully is there by anychance a mistake upon my set up help me please

---

