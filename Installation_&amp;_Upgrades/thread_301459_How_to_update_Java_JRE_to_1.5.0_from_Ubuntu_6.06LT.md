---
title: "How to update Java JRE to 1.5.0 from Ubuntu 6.06LTS"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by BitLauncher on 2006-11-17
I want to update java from the preinstalled version 1.4.2
a the 1.5.xx version.
apt-get update works,
but apt-get install sun-java5-bin etc. complains
**"E: Couldn't find package sun-java5-bin"**:confused: 
(I am using a console logged in as root).
(Furthermore I want to install jdk and eclipse after this update)
[SIZE="2"][B]What is the right command?
Do I have to add some and which lines to 
/etc/apt/sources.list?[/B]
[/SIZE]

**Details:** Ubuntu 6.06 LTS installed as virtual machine in
VMWare Workstation 5.5.1 build-19175 on a laptop
Intel Core 2 CPU T7200 with
Win Xp Professional SP2
The Installation brings java 1.4.2 (gij version 4.1.0) with it
the file /etc/apt/sources.list is nearly empty
there is no line talking about java.

---

### Post by swamytk on 2006-11-17
Enable "multiverse" in /etc/apt/sources.list file.

---

### Post by BitLauncher on 2006-11-17
Thanks:) , with help of google :rolleyes: I understood what you meant, swamytk, because I am a Linux greenhorn.
There were two commented lines in the file, I uncomment it  and
appended 'multiverse' - at the moment sun-java5-run is downloading
and installing.:cool: 
I hope I won't get a conflict with the previous jre.

---

