---
title: "Installation trouble Dual boot- Help"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by 987a654 on 2008-08-06
Hi 

My computer doesn&#8217;t boot from CD/DVD drive, I tried UBUNTU live CD, Gparted live CD, and WINDOWS installation DISK. All the disks are working fine because they run without any glitch in my laptop. It&#8217;s got Gigabyte GA-73PVM-S2H, I even flashed the BIOS to F6, that&#8217;s the latest. I have changed the boot sequence order, it doesn't make any difference, I have even put all three boot devices as CDROM, no use. It checks the floppy and goes to the harddrive to boot vista.

I believe it&#8217;s got something to do with the boot manager, Ubuntu or any other bootable CD will not boot form the CD drive. I wanted to try UBUNTU live CD so I accessed it inside vista and there was an option in it > &#8220;Help me to boot from the CD&#8221;. This worked , my guess is that it loaded WUBI and during start up there was an option to load vista or ubuntu (from CD drive). Any way everything seemed to work fine until I used Gparted in Ubuntu to create partitions for proper dual boot install. After creating the partitions I rebooted and ubuntu will not load. One of the partitions I shrunk contained ubuntu files.
I get the following error:

File: \ubuntu\winboot\wubildr.mbr
Status: 0xc0000225
Info: the selected entry could not be loaded because the application is missing or corrupt. 

I would appreciate very much if I could know two things:
1	why isn&#8217;t any disk booting form the CD drive?
2	How to fix the boot manager.

Please, help.  
Rahul

---

### Post by wpshooter on 2008-08-06
Maybe I missed this somewhere in what you said but you do have the CD-Rom drive as the **FIRST BOOTABLE DEVICE** in the BIOS, don't you ?

---

### Post by HotCupOfJava on 2008-08-06
It does sound like your CD drive is not being checked for an OS before the hard drive is checked. When you FIRST start the computer, you should see an option to enter the BIOS setup (usually it says to hit escape or F-something). You should see some sort of textual interface (you'll have to use your arrow keys and/or TAB to navigate the menus). There should be a menu/options where you can change the boot device order. Change it so that the BIOS checks your CD drive BEFORE it checks your hard drive. (Presuming that is the problem).

---

