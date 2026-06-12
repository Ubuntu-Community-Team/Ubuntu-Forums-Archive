---
title: "linksys Ae1000 trouble"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by lumunofloginism on 2011-02-10
[http://ubuntuforums.org/showthread.php?t=1630358](http://ubuntuforums.org/showthread.php?t=1630358)

i followed all the instructions to a "T"
(except that the download was verison 5)
but when i try to get into the directory 
it says:


shanon@shanon-T3101:~$ /home/shanon/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO 
bash: /home/shanon/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO: Permission denied
shanon@shanon-T3101:~$ 

anyone have any ideas?

---

### Post by chili555 on 2011-02-10
Please try:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO 
```cd means 'change directories.'

Post back if you get stuck; I'll be happy to help.

---

### Post by lumunofloginism on 2011-02-10
> **chili555 said:**
> Please try:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO 
```cd means 'change directories.'

Post back if you get stuck; I'll be happy to help.


shanon@shanon-T3101:~$ cd /home/shanon/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO 
bash: cd: /home/shanon/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO: Not a directory
shanon@shanon-T3101:~$ 

whhhy

---

### Post by chili555 on 2011-02-10
> whhhyBecause that's not what I said. Once again:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
```Your terminal prompt indicates you are already in */home/shanon*. The command you wrote wants to change to /home/shanon/home/shanon/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO 

It makes a difference.

---

### Post by lumunofloginism on 2011-02-11
alright so i figured that part out (just renamed the file so i could find the directory)
but not i cannot connect to my wireless network...
a windows pops up everyonce in awhile asking me to put in the password for the connection...and then nothing happens.

I inputed as much info as i could into the:
wireless
ipv4
and ipv6
settings and it says that it connects but there is no internet still..

---

### Post by chili555 on 2011-02-11
> it says that it connects but there is no internet still..Where does it say it's connected? A pop-up? When it says it's connected, when you try to open Firefox, what happens? What settings did you put here?> wireless
ipv4
and ipv6
settingsDid you specify an IP address or DHCP? If you specified an address, try DHCP under IPv4.

---

### Post by lumunofloginism on 2011-02-11
i did:

ssid under the wireless tab

ip address netmask dns servers and gateway under the ipv4 settings

and set ipv6 to automatic, dhcp only

and dont see anything about dhcp anywhere except the 
ipv6 and ipv4 "method" dropboxes

---

### Post by lumunofloginism on 2011-02-11
> **chili555 said:**
> Where does it say it's connected? A pop-up? When it says it's connected, when you try to open Firefox, what happens? What settings did you put here?Did you specify an IP address or DHCP? If you specified an address, try DHCP under IPv4.

a pop up tells me that its connected.
when i open firefox it says server not found

---

### Post by chili555 on 2011-02-11
> ip address netmask dns servers and gateway under the ipv4 settings
I think you'll have better luck if you drop down and select DHCP and let the router hand out an address and DNS nameservers. Do you especially require a static IP address?

---

### Post by lumunofloginism on 2011-02-11
> **chili555 said:**
> I think you'll have better luck if you drop down and select DHCP and let the router hand out an address and DNS nameservers. Do you especially require a static IP address?

im really not sure if i need one, i dont know what there for.

what about the "mode" dropbox under the wireless tab?
its set to infrastructure.

---

### Post by chili555 on 2011-02-11
If you are not sure if you need a static IP address, then you don't. Infrastructure is correct for computer to router. So, does it connect?

---

### Post by lumunofloginism on 2011-02-11
> **chili555 said:**
> If you are not sure if you need a static IP address, then you don't. Infrastructure is correct for computer to router. So, does it connect?

no it doesnt, AND i accidently deleted my gnome-panel...and i dont have internet on the computer so.....
im gonna have to move my comp across the house and try to fix this.

(and i Un-installed it as well so there is no way to bring it back, unless you know of a way)

---

### Post by chili555 on 2011-02-11
> i Un-installed it as well so there is no way to bring it back, unless you know of a wayNot if you uninstalled it. I will check back after pizza with GF.

---

### Post by lumunofloginism on 2011-02-11
> **chili555 said:**
> Not if you uninstalled it. I will check back after pizza with GF.

thank you.
i got to eat and get ready for work anyway.

---

