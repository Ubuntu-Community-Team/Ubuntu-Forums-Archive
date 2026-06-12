---
title: "Davinci Resolve Installation Fails to Start"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by notanxious on 2019-05-25
After installing the latest version 15 I receive the following core dump result in terminal

tim@tim-MS-7977://opt/resolve/bin$ ./resolve 
ActCCMessage Already in Table: Code= c005, Mode= 13, Level=  1, CmdKey= -1, Option= 0
ActCCMessage Already in Table: Code= c006, Mode= 13, Level=  1, CmdKey= -1, Option= 0
ActCCMessage Already in Table: Code= c007, Mode= 13, Level=  1, CmdKey= -1, Option= 0
ActCCMessage Already in Table: Code= 2282, Mode=  0, Level=  0, CmdKey= 8, Option= 0
PnlMsgActionStringAdapter Already in Table: Code= 615e, Mode=  0, Level=  0, CmdKey= -1, Option= 0
15.3.1 (#003) Linux/Clang
Main thread starts: 8DAD9540
[0x7fb78dad9540] | Undefined            | INFO  | 2019-05-25 10:27:25,791 | --------------------------------------------------------------------------------
[0x7fb78dad9540] | Undefined            | INFO  | 2019-05-25 10:27:25,791 | Loaded log config from /opt/resolve/configs/log-conf.xml
[0x7fb78dad9540] | Undefined            | INFO  | 2019-05-25 10:27:25,791 | --------------------------------------------------------------------------------
Aborted (core dumped)
tim@tim-MS-7977://opt/resolve/bin$

---

