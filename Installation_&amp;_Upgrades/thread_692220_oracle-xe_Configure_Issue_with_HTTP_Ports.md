---
title: "oracle-xe Configure Issue with HTTP Ports"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by chrism3568 on 2008-02-09
I installed oracle-xe on Gutsy and received no issues during the install. I then tried to configure using the following command (as root): oracle-xe configure. The script runs, I hit enter to accept the default port and I get the following error: Specify the HTTP port that will be used for Oracle Application Express [8080]:
Invalid http port: 8080.

No matter what port  is entered I get the same error. If I run a port scan, 8080 is not being used. If I try a port that is in use the script reports an error saying the port is in use. 

Any help is much appreciated.

Thank you,

Chris

---

### Post by uebi on 2008-02-09
i have the same problem and i cant login with the user system and the password i´ve choosen in the configure menü with sql plus :(

---

### Post by ce41635 on 2008-02-12
I have the same problem with Ubuntu 7.10. The installation work fine and i can connected with sqlplus. But, when i tried to connect with the browser, [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex) i'm unabled to connect. Samething when i use this command :

telnet 127.0.0.1 8080
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Thank's for your help.

---

### Post by uebi on 2008-02-12
i traid in a virtualbox with a 32-bit unbuntu 7.10 edition -> there it worked at once with the .debs provide by oracle (oss.oracle.ccom) i think.

seems, that there is only a problem if you try to use the 32.bit XE on a 64-bit system

now waiting for 8.04 and then downgrading to 32-bit ;)

---

