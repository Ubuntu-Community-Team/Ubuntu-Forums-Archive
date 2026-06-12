---
title: "ubuntu adsl configuration problem"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by shepard on 2005-08-11
hello everyone
this is my first linux experince so please bi gentle :grin: 

during instalation process i got this error:

Network autoconfiguration failed
Yoour network is probably not using DHCP protocol
Alternatively the DHCP server may be slow or some network hardver is not working properly.

i didnt now what to do so i skipped network autoconfiguration.

now i can get ADSL working. When i type "sudo pppoeconf" in terminal and follow instructions i always get this error:

[img]http://foto.volja.net/user_galleries/tine1234/fit/norm_screenshot-3.jpg[/img]


funny thing is that in  live version of ubunt everything is working fine....autodetection and pppoeconf.
Adsl working fine in windows xp (duaboot).

i hope i made myself clear so someone could help me.

---

### Post by questionasker on 2005-08-12
[QUOTE=shepard]hello everyone
this is my first linux experince so please bi gentle :grin: 

during instalation process i got this error:

Network autoconfiguration failed
Yoour network is probably not using DHCP protocol
Alternatively the DHCP server may be slow or some network hardver is not working properly.

i didnt now what to do so i skipped network autoconfiguration.

now i can get ADSL working. When i type "sudo pppoeconf" in terminal and follow instructions i always get this error:

[img]http://foto.volja.net/user_galleries/tine1234/fit/norm_screenshot-3.jpg[/img]


funny thing is that in  live version of ubunt everything is working fine....autodetection and pppoeconf.
Adsl working fine in windows xp (duaboot).

i hope i made myself clear so someone could help me.[/QUOTE]
 try installing dhcp with ```
sudo apt-get install dhcp
``` i dont think it is installed by default... then just try restarting the comp...

if theis works, you shoudl be good to go, or you can install pump with ```
sudo apt-get install pump
``` and then ```
 pump -i eth0
``` (-i may not be correct, use the man pag eif not)... let me know if this helps...

---

### Post by shepard on 2005-08-12
it is not working....when i type "sudo apt-get install DHCP" i get msg:

couldn't find package.


maybe this will help:

when i type "sudo ifconfig"

i get this:

[img]http://foto.volja.net/user_galleries/tine1234/pc_slike/norm_screenshot4.jpg[/img]

---

### Post by shepard on 2005-08-12
iam writing this from ubuntu live version in wich i have no problem configuring adsl.

can someone tell me what is diffrent between live and install version...

---

### Post by TTL3 on 2005-08-21
I'm having the exactly same problem. I'd really like to get some help for this.

---

### Post by Velox Letum on 2005-08-21
Did you type sudo apt-get install dhcp or DHCP? Package names are case sensitive.

---

### Post by TTL3 on 2005-08-21
[QUOTE=Velox Letum]Did you type sudo apt-get install dhcp or DHCP? Package names are case sensitive.[/QUOTE]
I tried both, neither one works.

---

