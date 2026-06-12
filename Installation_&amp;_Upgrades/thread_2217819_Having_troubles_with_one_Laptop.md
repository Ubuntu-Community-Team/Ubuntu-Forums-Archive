---
title: "Having troubles with one Laptop"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Emmanuel_Gonzlez on 2014-04-18
Going to tell the long story.
I got a Toshiba Satellite from one friend with the Windows 7 and Horrible Viruses with (HOLY CRAP) 6 antivirus.. so I deleted all the OS, and I ask to make a reformat.
I Always worked with ubuntu, so I told her and she say yes to ubuntu, but windows 7 too.
So I installed the Ubuntu first... and it is going very good! I am updating all.. etc
but I insert in the CD Rom the Windows 7 Installer Disc (Original one) and I press F12 to enter in the CD boot. but, it dont boot in the disc, it enter in Ubuntu.
So I was reading and maybe and just maybe the BIOS its a little evil with me.... ](*,)
It has this Bios:
Toshiba Satellite: Bios InsydeH2O Setup Utility Rev 3.5

I know the next question: Why she want to install W7? she is not geeky.... and She dont has the patient to learn it at full.

hope and someone could help me.... (I am trying also to instal the VirtualBox VM.... )

---

### Post by oldfred on 2014-04-18
Is this system new enough to have UEFI? 
If you installed Ubuntu in UEFI mode, it also uses gpt partitioning.
Windows only installs to gpt partitioning with UEFI.
Windows 7 install DVD is BIOS only, but can be copied to a flash drive and updated to be a UEFI installer.

---

### Post by Emmanuel_Gonzlez on 2014-04-18
Done, I have the USB W7, and read a little of it... but no HDD (tip: NEVER accept to repair something when u dont have humor....)
so I enter to Ubuntu and I searched the Gnome Partition Manager, 14.04 LTS have not that... I open the Terminal and I put:
sudo apt-get install gparted
and know what.... 
"E: Unable to locate package gparted"
got the program... sorry... long time that i dont do this... but dam... cannot do a partition of the Disk T_T i wanna cry... screw W7

---

### Post by oldfred on 2014-04-18
You cannot use gparted from working system on mounted partitions. I do install it as I have several drives and then can only use it on my other drives. 
Normally you run gparted from live installer. 
But you should be able to install from terminal as you did??

---

