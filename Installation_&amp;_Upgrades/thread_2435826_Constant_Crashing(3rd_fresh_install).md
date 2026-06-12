---
title: "Constant Crashing(3rd fresh install)"
date: 2020-01-27
forum: Installation &amp; Upgrades
---

### Post by robotik2 on 2020-01-27
Hello and thanks for checking in. I'll get straight to it then.
   
    I have recently installed Ubuntu 18.04 on a clean internal 250gb ssd(not m.2) with minimal installation and included third party software options selected, and after simply installing chromium and Microsoft visual code from the software app it does not remain stable (also downloaded Java JDK from oracle) and crashes frequently. I used install option of "something else" where I manually partitioned off sections of the ssd. They are as follows; 500(499)mb EFI, 16gb Swap, 10gb /home and the remaining 220+gb for the / directory.
I honestly have no idea if I am doing something wrong or if I am, what it is. As of now my overall experience with Ubuntu and Linux for that matter (as this is my first distro) is not going well, but I haven't given up on it yet. I have spent hours on Youtube and Google trying to figure out what I'm doing wrong and am here now at you ladies and gentlemen's mercies. Please Help! Apologize in advance if the thread is bloated I don't know whats wrong so trying to provide as much info as possible.

-Rig/Build Details-
Dual Booting with windows 10 on a 1Tb M.2 also have a 2Tb hdd for storage. 
16gb dd4 3200
TR2950x
RTX 2080
(and then the 3 storage's mentioned above)

Disk0 in photo is the drive with Ubuntu OS

I don't know if that is enough information to help me out or not but please lmk if you need anything else to go on as I don't want to give up on Linux quite yet but its not operable in this state.

---

### Post by CelticWarrior on 2020-01-27
First thing that stands out is the partitioning. Somehow you misunderstood the purpose of / (root) and /home. The latter is where your user are is and the default location for all your personal files whereas root with a separated /home will have only the OS and additional user installed software. By now you should understand that you selected the "wrong" size for those partitions, the "right" way would have been the other way around.

The above is concerning but likely not the cause of your reported issue. The problem is likely related with the Nvidia drivers that, supposedly, you installed (but better check anyway), but aren't being loaded if Secure Boot is active. So, things to do:
[LIST]
[*]Open Additional Drivers and confirm the Nvidia drivers are installed.
[*]Reboot, go to UEFI settings and assure Secure Boot is disabled.
[/LIST]

---

### Post by Impavidus on 2020-01-27
Your partitioning is indeed weird. 16GB swap is much more than you ever want to use. Most people suggest 2-4GB these days, but if you don't make any, the installer will create a decent swap file for you. Your /home partition of 10GB is tiny and your root partition of 220GB is huge. I'd make a root partition of about 25GB and /home as large as I need, keeping the rest unallocated and reserved for future use. You can squeeze the OS in 10GB, but you're not short on disk space, so make it 25GB to be sure. The easy way to fix is a fresh install.

But that's not causing your instability. Unless you already filled your /home partition; that could make your session crash. I don't have Chromium, anything from Microsoft or anything Java installed, so no experience with those matters. It may help if you tell us the exact names of the packages you installed. If they were standard deb packages you should find the details in the dpkg log: /var/log/dpkg.log.

Log files may contain clues about the crashes. Read them in /var/logs, but they are hard to read. All entries have a timestamp, look for entries made at the time of the crash. I don't know about proprietary graphics drivers and secure boot. Maybe it's a problem. I never used either of those.

---

### Post by slickymaster on 2020-01-27
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by robotik2 on 2020-01-27
Thanks for the help I'm going to do fresh install and change the partitions. I also discovered through more research that I actually installed the drivers incorrectly and so that's more then likely what caused the instability. Thanks again.

---

