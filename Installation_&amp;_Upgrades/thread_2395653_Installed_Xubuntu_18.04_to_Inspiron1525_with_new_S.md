---
title: "Installed Xubuntu 18.04 to Inspiron1525 with new SSD=many error msgs and long boot"
date: 2018-07-04
forum: Installation &amp; Upgrades
---

### Post by kirbo719 on 2018-07-04
Installed v18.04 64-bit, which resulted in many errors and very slow boot, then attempted the 32-bit ver. with same result. During install and during boots following install, obtained many error messages. After 4-1/2 minutes, the login screen finally presents, but the machine acts slow.

Hardware: 10-year-old Dell Inspiron1525, 3.6gb RAM, new Samsung 860 EVO sata SSD.

In past, have successfully installed many vers. of Xubuntu, Ubuntu, Mint, typically with few/any error messages, resulting in OS and hardware that seemed happy together - when the laptop had a hard disk drive.

I presume the files  syslog  and  debug  in  /var/log/installer  might diagnose the issues.  Those are attached as txt files.

NO they are not. Upload mgr reported SYSLOG as 4mb, too large to upload. DEBUG is attached. Please advise what other logs might be needed.


Very curious to know what's happening, if anyone has the time to scroll these logs. 

And thanks in advance.[ATTACH]280286[/ATTACH]

---

### Post by oldfred on 2018-07-04
Is drive set for AHCI?
What chip & video chip?

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Have you updated UEFI from Dell to latest available?
Note that updates reset UEFI to defaults. I keep a list so I can quickly update settings to those I want. 
I use OS type "Other" (really secure boot off), UEFI only, Drives to AHCI, USB full support, boot after abnormal shutdown to normal boot not fast boot. Not every UEFI has all those types of settings.

---

### Post by kirbo719 on 2018-07-07
Okay, I'm working through your response above.

You state "...use ppa version with your live installer or any working install, not older Boot-Repair ISO:"  I'm not certain I know what that means. I infer that you want me to attempt an OS install from within a running instance of Xubuntu, using ppa and installer - rather than creating a live disk, booting from that CD and installing that way. Yes?

No UEFI. This machine is a decade old., BIOS (latest BIOS A17) from Dell. Yes, AHCI set.

Pentium dual T2370
Vid: chipset family: mobile Intel 965 Express v.7.14.10.1409



Thanks, and please let me know if my assumption is correct as far as installing via "ppa version." After three years w/Lynux, I still consider myself a newbie.

---

### Post by oldfred on 2018-07-07
If you look at the instructions for using Boot-Repair, there are basically two ways.
One is download its own live ISO which has Boot-Repair pre-installed. But as ISO is is now an older version.
The ppa is another way to install Boot-Repair into any working or live installer. You just have to copy the lines one at a time into your terminal and then run Boot-Repair. Just run report and post link it gives.

---

