---
title: "Installation Error Message"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Korrath on 2010-09-26
I am brand new to Linux and wanted to give it a try and start learning.  I heard raving reviews on how Ubuntu is so install friendly.  So I got a brand new WD 320GB Internal HD (old one crashed), put in the live CD, and allowed it to use the entire disc to install.  After many attempts and tinkering, I keep getting this message at 5%:  
[I]
The attempt to mount a file system with type ext4 in SCSl1 (0,0,0), partition #1 (sda) at / failed.[/I]

This seemed very vague to me and I haven't had any success searching for answers.  

On a possibly unrelated note, the hard drive comes up in GPartitioner and the Disc Utility, but does not come up under "Computer".  

I am somewhat decent with computers, but some of this is a little over my head!  Thanks in advance! :)

---

### Post by presence1960 on 2010-09-26
sorry wrong thread

---

### Post by endotherm on 2010-09-26
when the drive shows up in gparted and diskutility, does it show an ext4 partition?

this tutorial may help you to manuallly partition your disk. this may allow you to avoid the error, and to create a seperate home partition, which is very useful when you reinstall or upgrade to the latest ubuntu. [http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

---

### Post by Korrath on 2010-09-26
Thanks for the reply.  I used the guide to create my own partitions.  It made it one step further, but unfortunately, I received this message....

[I]

The installer encountered an error copying files to the hard disk:

[Errno 30] Read-only File system: '/target/bin'

This is often due to a faulty hard disk.  It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/I]



This has to be bad..Perhaps my power supply is zapping my hard drives?  Or I just got a faulty hard drive from Best Buy...ACK!

---

