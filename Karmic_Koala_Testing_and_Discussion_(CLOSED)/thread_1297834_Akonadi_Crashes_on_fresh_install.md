---
title: "Akonadi Crashes on fresh install??"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Crowder on 2009-10-22
I just reinstalled Kubuntu 9.04 and got an error message from Akonadi at startup. No big deal, because i was in the process of upgrading to karmic - oh wait, IT'S STILL THERE.

This is a major pain because it seems that kontact and plenty of other apps won't really function without it.

I have the error message here:

```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration.
The following drivers are installed: QSQLITE, QMYSQL3, QMYSQL.
Make sure the required driver is installed.

File content of '/home/crowder/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
SizeThreshold=4096
ExternalPayload=false

[QMYSQL]
Name=akonadi
User=
Password=
Options="UNIX_SOCKET=/home/crowder/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=false
Host=

[Debug]
Tracer=null


Test 2:  SKIP
--------

MySQL server executable not tested.
Details: The current configuration does not require an internal MySQL server.

Test 3:  SKIP
--------

MySQL server error log not tested.
Details: The current configuration does not require an internal MySQL server.

Test 4:  SKIP
--------

MySQL server configuration not tested.
Details: The current configuration does not require an internal MySQL server.

Test 5:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.2.1


Test 6:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 7:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 8:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 9:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
distlistresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
microblog.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
distlistresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
microblog.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 10:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/home/crowder/.local/share/akonadi/akonadiserver.error'>/home/crowder/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/crowder/.local/share/akonadi/akonadiserver.error':
Unable to open database "Can't connect to local MySQL server through socket '/home/crowder/.local/share/akonadi/db_misc/mysql.socket' (2) QMYSQL: Unable to connect" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x6ac400]
3: [0x6ac422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x4224d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x425932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0x155f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0x1e80d5]
9: /usr/lib/libQtCore.so.4 [0x1f6ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x1f8298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x5b5) [0xe7a575]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0xe7b3c8]
14: akonadiserver(main+0x362) [0x804d032]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x40eb56]
16: akonadiserver [0x804cc01]
]
" 


Test 11:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/crowder/.local/share/akonadi/akonadiserver.error.old'>/home/crowder/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/crowder/.local/share/akonadi/akonadiserver.error.old':
Unable to open database "Can't connect to local MySQL server through socket '/home/crowder/.local/share/akonadi/db_misc/mysql.socket' (2) QMYSQL: Unable to connect" 
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8051f25]
1: akonadiserver [0x80523f6]
2: [0x66a400]
3: [0x66a422]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x51) [0x4254d1]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x182) [0x428932]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xad8f8c]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8052f54]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x85) [0xb6b0d5]
9: /usr/lib/libQtCore.so.4 [0xb79ed5]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0xb7b298]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x804dbf3]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x5b5) [0x15a575]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x58) [0x15b3c8]
14: akonadiserver(main+0x362) [0x804d032]
15: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x411b56]
16: akonadiserver [0x804cc01]
]
" 


Test 12:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 13:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```

To be honest, I haven't even read through it. I still consider myself a bit of a noob and since I have no idea what akonadi and mysql really are it's probably going to be over my head. Thanks in advance.

---

### Post by ianmillington on 2009-10-22
Akonadi is a work in progress and it would seem that the programs you refer to are not yet dependent on it.

You will find this helpful

[http://techbase.kde.org/Projects/PIM/Akonadi#How_do_I_completely_disable_Akonadi_startup.3F](http://techbase.kde.org/Projects/PIM/Akonadi#How_do_I_completely_disable_Akonadi_startup.3F)

---

