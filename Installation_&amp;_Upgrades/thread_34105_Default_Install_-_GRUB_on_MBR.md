---
title: "Default Install - GRUB on MBR"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by Caoimhan on 2005-05-13
Okay, I have a gripe about the install.

hda = 200GB drive using Dynamic Drive Overlay from Western Digital with Windows 2000 professional installed.

hdb = 30 GB drive for installing Hoary.

During the install from CD, I choose to erase the entire hdb drive for my Ubuntu install.  I expected to be asked how I want my bootloader installed, but no... Hoary installer decided automatically that I wanted GRUB on the MBR of hda, and it wiped out my DDO.

I did end up going back and installing Lilo to the MBR of hdb (I can choose which drive to boot to from a firmware boot menu), however, now my Windows is hosed, because Hoary didn't respect my choice of install drives, or give me an option to change its default behavior.

Does anyone know of any good tools I can try to use to re-create the DDO on hda?  Or at least access the data in any way?  I was using NTFS.

Edit: Oh yeah... I'd really want the tool to recreate the DDO without wiping the data on the drive.

Thanks,
Caoimhan

---

### Post by nad on 2005-05-13
This is a major pitfall of ubuntu. Not only is the choice 'use entire hard drive' the default install, you have also discovered the hard way that unless you use the 'expert' install, no choice or mention is given regarding the bootloader.

I don't know how to re-create the DDO. Perhaps a diagnostic or utilities disc from wd.

---

### Post by harryc on 2005-05-13
I agree, since it's a proprietary DDO, you'll need to go to WD and ask. Don't want to sound like an armchair quarterback here, but this is a good reason not to use DDO's. If you had just used the Windows disk to partition/format, one quick fdisk /mbr and you would not be having this conversation. But maybe you had a good reason to use a DDO...perhaps your BIOS does not support large drives?

According to this howto from WD, you may be in luck if you backed up your original MBR...

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1117&p_created=1069371912&p_sid=HcCHxkFh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OCZwX3Byb2RzPTg1LDAmcF9jYXRzPTAmcF9wdj0xLjg1OzIudTAmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1mZGlzayAvbWJy&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1117&p_created=1069371912&p_sid=HcCHxkFh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OCZwX3Byb2RzPTg1LDAmcF9jYXRzPTAmcF9wdj0xLjg1OzIudTAmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1mZGlzayAvbWJy&p_li=&p_topview=1)

If you didn't backup the original, you could try this howto, then run a fdsik /mbr, then pray. 

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1103&p_created=1067451021&p_sid=HcCHxkFh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OCZwX3Byb2RzPTg1LDAmcF9jYXRzPTAmcF9wdj0xLjg1OzIudTAmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1mZGlzayAvbWJy&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1103&p_created=1067451021&p_sid=HcCHxkFh&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OCZwX3Byb2RzPTg1LDAmcF9jYXRzPTAmcF9wdj0xLjg1OzIudTAmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1mZGlzayAvbWJy&p_li=&p_topview=1)

If the data is critical, you may want to consult with a data recovery specialist before you touch anything.

---

### Post by Caoimhan on 2005-05-13
Well, I found some more info on the web on how I might be able to recover it.

If not, I don't have the financial resources to go with professional data recovery.  I'll just have to sacrifice it.

Fortunately, most of my creative work has been e-mailed to someone in the past, and I use web-mail/IMAP, and have lots of e-mail box space on my e-mail servers that I use.  Most of that stuff is in a "SENT" box somewhere.

Mostly, I'm bummed out about all the stuff I've downloaded over the last year. *sigh*

So what about configuring a 200 GB drive on a system that only recognizes up to 137 GB?  Can Ubuntu do that?

---

### Post by harryc on 2005-05-13
It's not a problem provided that your boot partition is located within the first 1024 cylinders. After Linux boots, it can see your whole drive.

[http://www.tldp.org/HOWTO/Large-Disk-HOWTO-5.html#ss5.4](http://www.tldp.org/HOWTO/Large-Disk-HOWTO-5.html#ss5.4)


5. Booting

When the system is booted, the BIOS reads sector 0 (known as the MBR - the Master Boot Record) from the first disk (or from floppy or CDROM), and jumps to the code found there - usually some bootstrap loader. These small bootstrap programs found there typically have no own disk drivers and use BIOS services. This means that a Linux kernel can only be booted when it is entirely located within the first 1024 cylinders, unless you both have a modern BIOS (a BIOS that supports the Extended INT13 functions), and a modern bootloader (a bootloader that uses these functions when available).

This problem (if it is a problem) is very easily solved: make sure that the kernel (and perhaps other files used during bootup, such as LILO map files) are located on a partition that is entirely contained in the first 1024 cylinders of a disk that the BIOS can access - probably this means the first or second disk.

Thus: create a small partition, say 10 MB large, so that there is room for a handful of kernels, making sure that it is entirely contained within the first 1024 cylinders of the first or second disk. Mount it on /boot so that LILO will put its stuff there.

Most systems from 1998 or later will have a modern BIOS.

---

