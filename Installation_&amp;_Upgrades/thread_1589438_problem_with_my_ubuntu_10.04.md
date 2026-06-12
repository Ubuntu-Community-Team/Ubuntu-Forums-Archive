---
title: "problem with my ubuntu 10.04"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Chancier on 2010-10-06
Hi guys,i'm a newbie to linux please help me...
 i upgraded my ubuntu 9.10(karmic) to ubuntu 10.04 (lucid) by executing the commands "
apt-get update
apt-get dist-upgrade"
one at a time in terminal after finishing upgrade ,i restarted my system, after restarting  i can't access GUI (interface)  in UPGRADED version ,it prompts me to terminal interface ...
plz help me to rectify my problem..:confused:


hi! guys, as a newbie i don't know how to enable proprietary drivers..,can u please give me help about enabling proprietary drivers! and also i used startx command it prompts me to gui but i can't access my keyboard and mouse or any other input devices ..... please help me to find solution...

---

### Post by andrewthomas on 2010-10-06
Did you have proprietary drivers enabled?

What kind of graphics card to you have?

---

### Post by sikander3786 on 2010-10-06
In addition to andrewthomas's post above, can you start the gui by typing

```
startx
```

Any error messages?

---

### Post by Chancier on 2010-10-07
hi! guys, as a newbie i don't know how to enable proprietary drivers.:confused:.,can u please give me help about enabling proprietary drivers! and also i used startx command in shell mode  it prompts me to gui but i can't access my keyboard and mouse or any other input devices in gui mode ..... please help me to find solution...
i've no graphics card in my system, my config is
Intel Motherboard: DG41RQ
Processor:E7500(core 2 Duo)
RaM:2gb
Hardisk:500gb (seagate)

---

### Post by Chancier on 2010-10-07
> **Chancier said:**
> hi! guys, as a newbie i don't know how to enable proprietary drivers.:confused:.,can u please give me help about enabling proprietary drivers! and also i used startx command in shell mode  it prompts me to gui but i can't access my keyboard and mouse or any other input devices in gui mode ..... please help me to find solution...
i've no graphics card in my system, my config is
Intel Motherboard: DG41RQ
Processor:E7500(core 2 Duo)
RaM:2gb
Hardisk:500gb (seagate)

hi guys i found partial solution but still facing some problems ,i used 
" sudo apt-get upgrade --fix-missing " in my console it installed missing updates but finally i got an error as 
" /var/cache/apt/archives/qdvdauthor_common_|%3az.|.0+dfsg_0ubuntu3_all.deb " 
with message stated
" E:Sub-Process /usr/bin/dpkg returned an error code ",
and also by default i can't accees my gui login screen , whenever i started my system it prompts me to console interface for login, everytime i need to give startx command for gui ,so please find me the better solution ...

---

### Post by Chancier on 2010-10-08
> **Chancier said:**
> hi guys i found partial solution but still facing some problems ,i used 
" sudo apt-get upgrade --fix-missing " in my console it installed missing updates but finally i got an error as 
" /var/cache/apt/archives/qdvdauthor_common_|%3az.|.0+dfsg_0ubuntu3_all.deb " 
with message stated
" E:Sub-Process /usr/bin/dpkg returned an error code ",
and also by default i can't accees my gui login screen , whenever i started my system it prompts me to console interface for login, everytime i need to give startx command for gui ,so please find me the better solution ...
  Hi guys ,finally  i got solution for my problem:P , my upgrades failed to install gnome & kde desktop, so i installed them manually, for gnome i used  
"sudo aptitude install ubuntu-desktop"
 for kde i used
"sudo aptitude install kubuntu-desktop"
 now my system works fine in both the environments.... 
thanks a lot :lolflag:.......

---

