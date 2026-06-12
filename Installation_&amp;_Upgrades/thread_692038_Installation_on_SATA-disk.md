---
title: "Installation on SATA-disk"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by yc2 on 2008-02-09
I sometimes see problems appear when installing Ubuntu on SATA-disks. It often happens to people installing Ubuntu for the first time and I don&#8217;t know how to help them.

If there are multiple disks in the system it sometimes helps to simply disconnect other disks and install Ubuntu first and then add the other disks. (GRUB makes an error in assigning numbers hd(0, 1 &#8230; )? This problem can also be solved by mapping in GRUB.

**However, when a single SATA-disk system does not install properly. What should one do? **

I think the traditional way of repairing GRUB is seldom successful in solving this particular SATA-problem??  (i.e. grub> root (hd0,1), setup (hd0))

I have sometimes read the advice to update BIOS and to use &#8221;legacy ATA-option&#8221;, but I am not sure if it is always successful? "Rebuild the kernel to support your particular SATA-chipset!" sounds very tricky and I am not sure it is always the right thing? At least it is definitely not what you want to tell a person who is installing Ubuntu for the first time.

Sometimes the installation works properly but the system will not boot at all or will only boot from a floppy or from the Live CD (using option &#8221;boot from first hard disk&#8221;). I have no idea how this can occur. If the SATA-controller is not supported, how come it works during the installation?

---

### Post by martindandersson on 2008-02-10
I am currently having the same problem.

I am switching from running XP to only Ubuntu. I have two disks, one PATA and one SATA. Since the SATA disk i faster I would like to install ubuntu on that one. I boot from the live/cd and start the installation. I manually select which partition to install on, a logical partition with ext3 in the beginning of the SATA disk. Create additional swap space on the same disk. When I reboot the BIOS or grub says that there are no operating system to boot.

I have not yet tried to disconnect the PATA disk but I am pretty sure it will solve the issue. I remember having to do so when installing XP.

Why have this issue not been solved yet? SATA disks have been around a while and the combination of SATA and PATA disks are probably not at all uncommon.

---

### Post by yc2 on 2008-02-10
I just add one more thing I have heard that could be of interest:
The SATA-connectors (on the motherboard) are not equal. One of them could be "master" and if you use a single SATA-disk it must be plugged into this particular connector?

---

### Post by Caps18 on 2008-02-15
I'm going to be doing this tomorrow, I have Mythbuntu 7.1 on a 40 GB IDE drive right now, but will be upgrading to SATA.  I have to go buy a SATA controller in order to use my 'external' usb drive as an internal one.  The external drive + SATA PCI controller still cost less than buying an internal drive to start with, try to figure that one out...

This 750GB one will be the only hard drive in this system for now.  I might add in a 160 GB (IDE) & some other IDE drive in the future, but I doubt it will be necessary. 

Now to find a SATA controller that won't have any problems with Linux...

---

### Post by yc2 on 2008-02-16
> **Caps18 said:**
> I'm going to be doing this tomorrow, I have Mythbuntu 7.1 on a 40 GB IDE drive right now, but will be upgrading to SATA.  I have to go buy a SATA controller in order to use my 'external' usb drive as an internal one.  The external drive + SATA PCI controller still cost less than buying an internal drive to start with, try to figure that one out...

This 750GB one will be the only hard drive in this system for now.  I might add in a 160 GB (IDE) & some other IDE drive in the future, but I doubt it will be necessary. 

Now to find a SATA controller that won't have any problems with Linux...

I am definitely no expert in this area. I am not sure if this page can be of help?
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

Maybe the most important thing is to make the shop selling the controller write on the receipt: "If this does not work with Mythbuntu 7.10 (and your hardware), we will immediately refund it"? Or maybe simpler just giving you one week trial period?

---

### Post by Caps18 on 2008-02-19
[http://www.5oclock.com/Online/product.asp?SubCatID=508&ProductID=CON-PS300TX2P&PriceID=1&mscssid=5K9FFJSVWBU58L6C6H9A31AX9SV86MH6](http://www.5oclock.com/Online/product.asp?SubCatID=508&ProductID=CON-PS300TX2P&PriceID=1&mscssid=5K9FFJSVWBU58L6C6H9A31AX9SV86MH6)

Here is the one I bought.  It is nice having a local computer shop that is run by geeks.  :)

It is a Promise Technology, Inc SATA 300 TX2plus (2-Port) Serial ATA 3G Plus 1-Channel Parallel ATA PCI Host Bus Adapter, and it works perfectly in Linux.  It even says so on the back of the box it works with Red Hat, SuSE and Linux open source code.

The only thing I had to do was change the BIOS to boot from a SCSI disk.

---

