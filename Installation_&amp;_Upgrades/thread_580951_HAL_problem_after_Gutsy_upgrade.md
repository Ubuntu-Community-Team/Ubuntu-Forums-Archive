---
title: "HAL problem after Gutsy upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by jaezcurra on 2007-10-19
Hi, The upgrade from 7.04 to 7.10 went smooth, but after reinitialization I got an error message as HAL is not loaded; so first problem I have is that Network Connections are not running and I cannot fix it.

---

### Post by sune_cph on 2007-10-19
I too have hald problems in Gutsy but it only affects removeable drives detection, however I can fix it with a "$sudo hald" from a terminal (or better yet in /etc/rc.local)  

/Sune

---

### Post by jaezcurra on 2007-10-19
"I can fix it with a "$sudo hald" from a terminal"
I have done and nothing.  BTW, my USB external disk is missing too.  I must say that my upgrade was made from a 7.04 installed with Wubi in a Windows XP machine.  Nevertheless, everything had always worked 100% OK until now.

---

### Post by brujoand on 2007-10-19
I had the same problem with hal after upgrading to. I found that a boot tweak I did in feisty was causing trouble. I changed 

CONCURRENCY=shell           // (which is the boot tweak)

to 

CONCURRENCY=shell           // (which is the default)

in 

"/etc/init.d/rc "                    // (the script for your boot)

..and hal now workes fine as do network-manager. 
The boot is a little slower though but i guess thats ok. ;)
Hope that helps

       -Anders

---

### Post by Can+~ on 2007-10-19
> **GrimmVarg said:**
> I had the same problem with hal after upgrading to. I found that a boot tweak I did in feisty was causing trouble. I changed 

CONCURRENCY=shell           // (which is the boot tweak) (to)
CONCURRENCY=shell           // (which is the default)


I think you misspelled something there. "CONCURRENCY=none"?

---

### Post by Shako73 on 2007-10-19
Exact same problem as "jaezcurra", I always have HAL error when booting, USB hard drives and USB CD/DVD-RW not recognized, I updated from Feisty Wubi installation.

in /etc/init.d/rc
Tried **CONCURRENCE=none** + reboot
Tried back to **CONCURRENCE=shell** + reboot
Nothing more... didn't work... But everything else works very fine, except KTorrent.
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by brujoand on 2007-10-19
> **GrimmVarg said:**
>  
CONCURRENCY=shell           // (which is the default)

should be 

CONCURRENCY=none

sry ;)

---

### Post by jaezcurra on 2007-10-21
This change from CONCURRENCY=none to CONCURRENCY=shell does not work for me either.
The HAL error makes me not having USB disks, ATAPI DVDs and, above all, the network card, so I do not have internet.
I will be forced to make a Gutsy Wubi installation from the scratch, forgetting about upgrading from Feisty 
:(

---

### Post by jaezcurra on 2007-10-21
I could find this in the wubi forum:

> **xiang said:**
> Hi

Here I describe a type of "failed to initialize HAL" problem and its solution. (There are so many types of  "failed to initialize HAL", so please check whether your symptom is the same as mine first).

symptom:
install ubuntu 7.04 by wubi
when login, a pop-out window said "internal error, failed to initialize HAL". You will also found "no network connection" on the network icon at the systemtray. In addition, you can't open "power management" and "hardware information" in "preference".

solution:
search "hal" in synaptic, you will find  the below packages
hal
hal-device-manager
libhal-storage1
libhal1

check the properties of them, you can notice they have 2 versions. !!! force them to the old version. Everything will be OK.

(BTW, I also do a little other changes. I am not sure whether they also have effects but you can try if something goes wrong.
force kdebase-kio-plugins to old version
install hal-cups-utils libopenexr2c2a initscripts)

conclusion
This problem is due to the upgrade of HAL related packages. It seems that this problem just occurs in the systems installed by wubi but not in standard systems. I also encountered other problems (slow system) when upgraded, I am not sure what caused them, ubuntu itself or wubi? So my experience is if your system run well, do not upgrade.

Maybe this can help somebody.  As for me, I uninstalled my Feisty wubi and I am trying to install a fresh Gutsy wubi.

---

