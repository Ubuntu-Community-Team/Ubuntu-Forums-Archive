---
title: "Java firefox trouble installing"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by free10 on 2007-01-31
I am running Dapper and have Java 1.5.0_06 installed but can not get the java plugin for firefox to install. Ran automatix to try a reinstall of the Firefox plugin and it said installed but its not--Dwight

---

### Post by taurus on 2007-01-31
Do you know where you installed java?  You probably have to copy the plugin to /usr/lib/firefox/plugins or ~/.mozilla/plugins

Applications -> Accessories -> Terminal
```
locate java
```

---

### Post by free10 on 2007-01-31
This is what I get

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Tokyo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Dubai
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Colombo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Qatar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Bishkek
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Manila
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Karachi
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Thimphu
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Hovd
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Yerevan
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Baku
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Oral
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Ulaanbaatar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Jakarta
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Beirut
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Pyongyang
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Bahrain
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Phnom_Penh
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Saigon
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Jerusalem
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Shanghai
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Kuwait
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Damascus
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Nicosia
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Hong_Kong
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Riyadh
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Almaty
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Harbin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Gaza
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Dhaka
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Vientiane
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Dushanbe
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Macau
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Singapore
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Samarkand
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Taipei
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Muscat
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Amman
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Calcutta
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Jayapura
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Tehran
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Sakhalin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Irkutsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Novosibirsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Omsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Krasnoyarsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Kamchatka
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Magadan
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Vladivostok
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Anadyr
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Yakutsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Riyadh87
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Riyadh88
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Asia/Riyadh89
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/ZoneInfoMappings
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Melbourne
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Brisbane
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Adelaide
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Broken_Hill
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Lindeman
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Perth
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Darwin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Lord_Howe
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Sydney
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Hobart
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Australia/Currie
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/CET
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/EET
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+7
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-8
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+8
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/UTC
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/UCT
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-3
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+12
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-11
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-7
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+6
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+11
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-14
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+2
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-5
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-13
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+3
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-4
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-12
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+4
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+9
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-1
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+5
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-2
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-6
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-9
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT+10
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Etc/GMT-10
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Chisinau
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Moscow
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Paris
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Riga
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Lisbon
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Vaduz
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Belgrade
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Berlin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Luxembourg
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Oslo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Uzhgorod
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Istanbul
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Madrid
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Minsk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Rome
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Warsaw
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Tirane
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Helsinki
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Vilnius
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Stockholm
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Amsterdam
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Dublin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Vienna
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Prague
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/London
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Tallinn
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Kaliningrad
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Samara
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Malta
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Sofia
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Zurich
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Zaporozhye
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Gibraltar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Budapest
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Simferopol
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Athens
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Copenhagen
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Monaco
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Andorra
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Bucharest
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Brussels
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Europe/Kiev
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/GMT
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Antananarivo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Reunion
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Mauritius
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Mahe
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Mayotte
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Comoro
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Kerguelen
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Chagos
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Maldives
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Cocos
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Indian/Christmas
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/MET
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Kwajalein
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Kosrae
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Port_Moresby
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Marquesas
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Tongatapu
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Wallis
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Truk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Wake
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Funafuti
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Pago_Pago
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Norfolk
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Midway
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Guadalcanal
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Tarawa
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Noumea
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Fakaofo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Fiji
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Johnston
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Kiritimati
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Ponape
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Enderbury
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Guam
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Majuro
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Niue
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Tahiti
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Rarotonga
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Palau
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Chatham
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Auckland
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Pitcairn
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Gambier
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Apia
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Efate
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Saipan
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Nauru
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Honolulu
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Easter
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/Pacific/Galapagos
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/zi/WET
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/charsets.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/jce.jar
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/COPYRIGHT
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/README
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7-gcc29
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/desktop
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/desktop/sun_java.desktop
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/desktop/sun_java.png
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/javaws
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/javaws/javaws
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/LICENSE
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/THIRDPARTYLICENSEREADME.txt
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/ControlPanel
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/i386
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/i386/native_threads
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/unpack200
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/javaws
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/pack200
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/servertool
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/orbd
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/tnameserv
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/rmid
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/rmiregistry
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/ktab
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/klist
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/kinit
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/policytool
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/keytool
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/rmiregistry
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/gcj-dbtool
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/gij
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man/man1
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man/man1/rmiregistry.1.gz
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man/man1/gcj-dbtool.1.gz
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man/man1/jar.1.gz
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/man/man1/java.1.gz
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/security
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/security/java.security
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/i386
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/i386/libjawt.so
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/jdbc-stdext.jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/jsse.jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/rt.jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/jndi.jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/jaas.jar
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib/i486
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/rmiregistry
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/jar
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/lib-gnu-java-awt-peer-gtk.so.7.0.0
/usr/lib/mozilla-firefox/plugins/libjavaplugin.so
/usr/lib/j2se/1.4/bin/javaws
/usr/lib/j2se/1.4/bin/java
/usr/lib/j2se/1.4/jre/javaws
/usr/lib/j2se/1.4/jre/javaws/javalogo52x88.gif
/usr/lib/j2se/1.4/jre/javaws/javaws-l10n.jar
/usr/lib/j2se/1.4/jre/javaws/javaws.policy
/usr/lib/j2se/1.4/jre/javaws/readme_fr.html
/usr/lib/j2se/1.4/jre/javaws/readme_de.html
/usr/lib/j2se/1.4/jre/javaws/readme_es.html
/usr/lib/j2se/1.4/jre/javaws/readme_ja.html
/usr/lib/j2se/1.4/jre/javaws/readme_zh_TW.html
/usr/lib/j2se/1.4/jre/javaws/javaws
/usr/lib/j2se/1.4/jre/javaws/sunlogo64x30.gif
/usr/lib/j2se/1.4/jre/javaws/readme_sv.html
/usr/lib/j2se/1.4/jre/javaws/readme_ko.html
/usr/lib/j2se/1.4/jre/javaws/resources
/usr/lib/j2se/1.4/jre/javaws/resources/messages_zh_TW.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_it.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_ja.properties
/usr/lib/j2se/1.4/jre/javaws/resources/miniSplash.jpg
/usr/lib/j2se/1.4/jre/javaws/resources/copyright.jpg
/usr/lib/j2se/1.4/jre/javaws/resources/messages_sv.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_zh_CN.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_fr.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_de.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_ko.properties
/usr/lib/j2se/1.4/jre/javaws/resources/messages_es.properties
/usr/lib/j2se/1.4/jre/javaws/resources/JavaCup.ico
/usr/lib/j2se/1.4/jre/javaws/resources/messages.properties
/usr/lib/j2se/1.4/jre/javaws/resources/splash.jpg
/usr/lib/j2se/1.4/jre/javaws/readme_zh_CN.html
/usr/lib/j2se/1.4/jre/javaws/cacerts
/usr/lib/j2se/1.4/jre/javaws/readme_it.html
/usr/lib/j2se/1.4/jre/javaws/javawsbin
/usr/lib/j2se/1.4/jre/javaws/readme.html
/usr/lib/j2se/1.4/jre/javaws/javaws.jar
/usr/lib/j2se/1.4/jre/lib/security/java.security
/usr/lib/j2se/1.4/jre/lib/security/java.policy
/usr/lib/j2se/1.4/jre/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo
/usr/lib/j2se/1.4/jre/lib/i386/libjava.so
/usr/lib/j2se/1.4/jre/lib/i386/libjavaplugin_jni.so
/usr/lib/j2se/1.4/jre/plugin/desktop/sun_java.desktop
/usr/lib/j2se/1.4/jre/plugin/desktop/sun_java.png
/usr/lib/j2se/1.4/jre/plugin/i386/netscape4/libjavaplugin.so
/usr/lib/j2se/1.4/jre/bin/java_vm
/usr/lib/j2se/1.4/jre/bin/java
/usr/lib/j2se/1.4/jre/bin/javaws
/usr/lib/lib-gnu-java-awt-peer-gtk.so.7
/usr/lib/openoffice/program/javaldx
/usr/lib/openoffice/program/libjava_uno.so
/usr/lib/openoffice/program/javaloader.uno.so
/usr/lib/openoffice/program/javavm.uno.so
/usr/lib/openoffice/program/sunjavaplugin.so
/usr/lib/openoffice/program/java-set-classpath
/usr/lib/openoffice/share/registry/modules/org/openoffice/Office/Writer/Writer-javamail.xcu
/usr/lib/openoffice/share/Scripts/javascript
/usr/lib/openoffice/share/Scripts/javascript/ExportSheetsToHTML
/usr/lib/openoffice/share/Scripts/javascript/ExportSheetsToHTML/exportsheetstohtml.js
/usr/lib/openoffice/share/Scripts/javascript/ExportSheetsToHTML/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/javascript/HelloWorld
/usr/lib/openoffice/share/Scripts/javascript/HelloWorld/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/javascript/HelloWorld/helloworld.js
/usr/lib/openoffice/share/Scripts/javascript/Highlight
/usr/lib/openoffice/share/Scripts/javascript/Highlight/ButtonPressHandler.js
/usr/lib/openoffice/share/Scripts/javascript/Highlight/ShowDialog.js
/usr/lib/openoffice/share/Scripts/javascript/Highlight/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/java
/usr/lib/openoffice/share/Scripts/java/HelloWorld
/usr/lib/openoffice/share/Scripts/java/HelloWorld/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/java/HelloWorld/HelloWorld.java
/usr/lib/openoffice/share/Scripts/java/HelloWorld/HelloWorld.jar
/usr/lib/openoffice/share/Scripts/java/Highlight
/usr/lib/openoffice/share/Scripts/java/Highlight/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/java/Highlight/HighlightText.java
/usr/lib/openoffice/share/Scripts/java/Highlight/Highlight.jar
/usr/lib/openoffice/share/Scripts/java/MemoryUsage
/usr/lib/openoffice/share/Scripts/java/MemoryUsage/parcel-descriptor.xml
/usr/lib/openoffice/share/Scripts/java/MemoryUsage/MemoryUsage.java
/usr/lib/openoffice/share/Scripts/java/MemoryUsage/MemoryUsage.jar
/usr/lib/openoffice/share/config/javavendors.xml
/usr/lib/gcj-4.1/lib-gnu-java-awt-peer-gtk.la
/usr/lib/kde3/kjavaappletviewer.la
/usr/lib/kde3/kjavaappletviewer.so
/usr/lib/libkjava.so.1
/usr/lib/libkjava.so.1.0.0
/usr/lib/mozilla-snapshot/plugins/libjavaplugin_oji.so
/usr/lib/mozilla-snapshot/plugins/libjavaplugin.so
/usr/sbin/update-java-alternatives
/home/dwight/.local/share/applications/X-Debian-Apps-System-sun_java_5.0_plugin_control_panel-usercustom.desktop
/home/dwight/.java
/home/dwight/.java/deployment
/home/dwight/.java/deployment/deployment.properties
/home/dwight/.java/deployment/tmp
/home/dwight/.java/deployment/tmp/si
/home/dwight/.java/deployment/cache
/home/dwight/.java/deployment/cache/javaws
/home/dwight/.java/deployment/cache/javaws/muffins
/home/dwight/.java/deployment/cache/javapi
/home/dwight/.java/deployment/cache/javapi/v1.0
/home/dwight/.java/deployment/cache/javapi/v1.0/jar
/home/dwight/.java/deployment/cache/javapi/v1.0/file
/home/dwight/.java/deployment/cache/javapi/v1.0/ext
/home/dwight/.java/deployment/cache/javapi/v1.0/tmp
/home/dwight/.java/deployment/cache/tmp
/home/dwight/.java/deployment/log
/home/dwight/.java/deployment/security
/home/dwight/.java/deployment/security/deployment.certs
/home/dwight/.java/deployment/security/deployment.jssecerts
/home/dwight/.java/deployment/ext
/home/dwight/.java/.deployment
/home/dwight/.java/.deployment/deployment.properties
/home/dwight/.java/.deployment/javaws
/home/dwight/.java/.deployment/javaws/cache
/home/dwight/.java/.deployment/javaws/cache/http
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RTnotepad.gif
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RTdraw.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RMdraw.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RMnotepad.gif
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RTmg.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RMmg.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RTswingset2.small.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/DMimages/RMswingset2.small.jpg
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/RCmg.jar
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/ATmg.jnlp
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/AMmg.jnlp
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/RTmg.jar
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/RMmg.jar
/home/dwight/.java/.deployment/javaws/cache/http/Djava.sun.com/P80/DMproducts/DMjavawebstart/DMapps/ALmg.jnlp
/home/dwight/.java/.deployment/javaws/cache/lastAccessed
/home/dwight/.java/.deployment/javaws/cache/splashes
/home/dwight/.java/.deployment/javaws/cache/splashes/splash.xml
/home/dwight/.java/.deployment/javaws/cache/splashes/splash10678.jpg
/home/dwight/.java/.deployment/javaws/cache/indirect
/home/dwight/.java/.deployment/javaws/cache/indirect/indirect17100.ind
/home/dwight/.openoffice.org2/user/config/javasettings_Linux_x86.xml
/home/dwight/.gnome/mime-info/java-archive.keys
/home/dwight/.gnome/mime-info/java-archive.mime
/home/dwight/.gnome/mime-info/java-web-start.keys
/home/dwight/.gnome/mime-info/java-web-start.mime
/home/dwight/.gnome/application-info/java-archive.applications
/home/dwight/.gnome/application-info/java-web-start.applications
/home/dwight/jre1.5.0_09/bin/java
/home/dwight/jre1.5.0_09/bin/java_vm
/home/dwight/jre1.5.0_09/bin/javaws
/home/dwight/jre1.5.0_09/lib/i386/libjavaplugin_jni.so
/home/dwight/jre1.5.0_09/lib/i386/libjavaplugin_nscp.so
/home/dwight/jre1.5.0_09/lib/i386/libjava.so
/home/dwight/jre1.5.0_09/lib/i386/libjava_crw_demo.so
/home/dwight/jre1.5.0_09/lib/i386/libjavaplugin_nscp_gcc29.so
/home/dwight/jre1.5.0_09/lib/security/java.security
/home/dwight/jre1.5.0_09/lib/security/java.policy
/home/dwight/jre1.5.0_09/lib/security/javaws.policy
/home/dwight/jre1.5.0_09/lib/locale/de/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/es/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/fr/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/it/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/ja/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/ko/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/ko.UTF-8/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/sv/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/zh/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/zh.GBK/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/zh_TW/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/zh_TW.BIG5/LC_MESSAGES/sunw_java_plugin.mo
/home/dwight/jre1.5.0_09/lib/locale/zh_HK.BIG5HK/LC_MESSAGES/sunw_java_plugin.mo/home/dwight/jre1.5.0_09/lib/images/icons/sun-java.png
/home/dwight/jre1.5.0_09/lib/images/icons/sun-java_HighContrast.png
/home/dwight/jre1.5.0_09/lib/images/icons/sun-java_HighContrastInverse.png
/home/dwight/jre1.5.0_09/lib/images/icons/sun-java_LowContrast.png
/home/dwight/jre1.5.0_09/lib/javaws.jar
/home/dwight/jre1.5.0_09/lib/javaws
/home/dwight/jre1.5.0_09/lib/javaws/miniSplash.jpg
/home/dwight/jre1.5.0_09/lib/javaws/messages.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_zh_TW.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_de.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_es.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_fr.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_it.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_ja.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_ko.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_sv.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_zh_CN.properties
/home/dwight/jre1.5.0_09/lib/javaws/messages_zh_HK.properties
/home/dwight/jre1.5.0_09/lib/javaws/Java1.5.ico
/home/dwight/jre1.5.0_09/man/man1/java.1
/home/dwight/jre1.5.0_09/man/man1/javaws.1
/home/dwight/jre1.5.0_09/man/ja_JP.eucJP/man1/java.1
/home/dwight/jre1.5.0_09/man/ja_JP.eucJP/man1/javaws.1
/home/dwight/jre1.5.0_09/plugin/i386/ns7/libjavaplugin_oji.so
/home/dwight/jre1.5.0_09/plugin/i386/ns7-gcc29/libjavaplugin_oji.so
/home/dwight/jre1.5.0_09/plugin/desktop/sun_java.png
/home/dwight/jre1.5.0_09/plugin/desktop/sun_java.desktop
/home/dwight/jre1.5.0_09/javaws
/home/dwight/jre1.5.0_09/javaws/javaws
/opt/swiftfox/plugins/libjavaplugin_oji.so
dwight@toyforce:~$

---

### Post by taurus on 2007-01-31
Just want to make sure.  What's the output of this command from a terminal?

```
ls -la /usr/lib/firefox
```

---

### Post by free10 on 2007-01-31
Well its a shorter output LOL

dwight@toyforce:~$ ls -la /usr/lib/firefox
total 2300
drwxr-xr-x   5 root root   4096 2007-01-27 14:58 .
drwxr-xr-x 175 root root  45056 2007-01-27 15:22 ..
lrwxrwxrwx   1 root root     26 2007-01-27 14:58 chrome -> ../../share/firefox/chrome
drwxr-xr-x   2 root root  12288 2007-01-27 14:58 components
lrwxrwxrwx   1 root root     28 2007-01-27 14:58 defaults -> ../../share/firefox/defaults
drwxr-xr-x   4 root root   4096 2006-07-03 21:37 extensions
-rwxr-xr-x   1 root root   7732 2007-01-26 14:36 firefox
-rwxr-xr-x   1 root root  72184 2007-01-26 14:36 firefox-bin
-rw-r--r--   1 root root     42 2007-01-26 13:57 firefox.cfg
-rwxr-xr-x   1 root root    457 2007-01-26 13:57 firefox-xremote-client
lrwxrwxrwx   1 root root     28 2007-01-27 14:58 greprefs -> ../../share/firefox/greprefs
lrwxrwxrwx   1 root root     25 2007-01-27 14:58 icons -> ../../share/firefox/icons
-rw-r--r--   1 root root   7816 2007-01-26 14:36 libgfxpsshar.so
-rw-r--r--   1 root root 114988 2007-01-26 14:36 libgkgfx.so
-rw-r--r--   1 root root  76852 2007-01-26 14:36 libgtkembedmoz.so
-rw-r--r--   1 root root  14324 2007-01-26 14:36 libgtkxtbin.so
-rw-r--r--   1 root root  89100 2007-01-26 14:36 libjsj.so
-rw-r--r--   1 root root 625028 2007-01-26 14:36 libmozjs.so
-rw-r--r--   1 root root 239688 2007-01-26 14:36 libnssckbi.so
-rw-r--r--   1 root root    476 2007-01-26 14:31 libsoftokn3.chk
-rw-r--r--   1 root root  97012 2007-01-26 14:36 libxpcom_compat.so
-rw-r--r--   1 root root 630488 2007-01-26 14:36 libxpcom_core.so
-rw-r--r--   1 root root   9996 2007-01-26 14:36 libxpcom.so
-rw-r--r--   1 root root   7568 2007-01-26 14:36 libxpistub.so
-rw-r--r--   1 root root      7 2007-01-26 14:36 pkg-ver
drwxr-xr-x   2 root root   4096 2007-01-30 21:36 plugins
-rwxr-xr-x   1 root root  30856 2007-01-26 14:36 regxpcom
lrwxrwxrwx   1 root root     23 2007-01-27 14:58 res -> ../../share/firefox/res
lrwxrwxrwx   1 root root     33 2007-01-27 14:58 searchplugins -> ../../share/firefox/searchplugins
-rwxr-xr-x   1 root root  20524 2007-01-26 14:36 xpcshell
-rwxr-xr-x   1 root root  28852 2007-01-26 14:36 xpicleanup
-rwxr-xr-x   1 root root  76304 2007-01-26 14:36 xpidl
-rwxr-xr-x   1 root root  27240 2007-01-26 14:36 xpt_dump
-rwxr-xr-x   1 root root  21212 2007-01-26 14:36 xpt_link
dwight@toyforce:~$

---

### Post by taurus on 2007-01-31
Close down firefox and do

```
sudo  cp  /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so  /usr/lib/firefox/plugins
```

Now, start up firefox again and see if you have java plugin.

---

### Post by free10 on 2007-01-31
Still doesn't show it when I check about plugins and the browser was closed before I gave the command. Weird huh.

---

### Post by taurus on 2007-01-31
Or copy the plugin to your own $HOME directory.

```
cp  /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so  ~/.mozilla/plugins
```
Now, start firefox again and see if there is a java plugin on the menu.

```
about:plugins
```

---

### Post by free10 on 2007-01-31
Nope but I have an idea. I will find all plugin folders for Firefox using search and see if the plugin is missing in one of them and then use the other command used earlier with a new location to get it into any firefox plugin folder that is missing it, and maybe that will work. I sure thank you for the help and with your help I think I now can get it working, if not I will post again but I hope I have got it figured out now with your help--Dwight

---

### Post by taurus on 2007-01-31
Looks like you also have swiftfox installed on your machine and I see there is a java plugin in the plugins directory, /opt/swiftfox/plugins/libjavaplugin_oji.so.  Does java plugin works at all with swiftfox?

---

### Post by free10 on 2007-01-31
> **taurus said:**
> Looks like you also have swiftfox installed on your machine and I see there is a java plugin in the plugins directory, /opt/swiftfox/plugins/libjavaplugin_oji.so.  Does java plugin works at all with swiftfox?

Yes, I just checked in the /opt/swiftfox/plugins/ folder and it shows there, but not in the about:plugin when I checked swiftfox. Sorry to be delayed in answering but I had leave the computer when I did my last post and I have not had a chance yet to try my idea on looking at the various plugin folders and see if it is missig the file yet and commanding a copy to any browser folder, so I don't know if that will work and solve the problems.---Dwight

---

### Post by free10 on 2007-01-31
Ok did a firefox search of my files looking at different folders for plugins and found libjavaplugin.so in /usr/lib/mozilla-firefox/plugins.

In /usr/lib/firefox/plugins I find libjavaplugin_oji.so

In /opt/firefox/plugins no java plugin at all

Doing the same search for swiftfox I find libjavaplugin_oji.so in /opt/swiftfox/plugins but it and the other plugins in that folder have the lock symbol on them. I am not sure why or what that lock symbol means.


Did the search again for mozilla looking for plugin folders and found /usr/lib/mozilla/plugins and it has the libjavaplugin.so. In the /usr/lib/j2se/1.4/jre/plugin/i386/mozilla it shows nothing.

These were all the plugin folders and the java versions I found in them for mozilla..firefox..and swiftfox--Dwight

---

