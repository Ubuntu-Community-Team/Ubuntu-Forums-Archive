---
title: "HD Ide NOT recognized during installation"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by KaMZaTa on 2006-10-30
It's long time that I want replace on my pc Suse Linux (now 10.1) with Ubuntu but without be able. The problem is that during the installation and more exactly during recognition of HD Ide: no-one of my 2 HD Ide is recognized and I can't install Ubuntu.

This is my PC:

[list]
[*] CPU Intel P4 550 (3.4GHz)
[*] MB Asus P5AD2-Deluxe
[*] 2 Gb ram DDR2 533MHz Transcend
[*] 1 HD Sata Maxtor 6B200M0 200Gb
[*] 1 HD Sata Maxtor 6B200M0 200Gb
[*] 1 HD Ide Maxtor 60Gb
[*] 1 HD Ide Wester Digital 40Gb
[*] Ati X700Pro (connect on DVI)
[/list]

etc.

During installation only 2 HD Sata are recognized.

Given that:

[list]
[*] I've tried to install all Ubuntu version (Breezy, Dapper, Edgy)
[*] I've tried all alternate CD installation
[*] HD Ide are perfectly recognized on Suse, Windows
[*] I've tried to disconnect HD Sata
[*] I've tried to change boot order by Bios
[*] I've tried to change Jumper (Master, Slave, Auto)
[*] ....
[/list]

I WANT install Ubuntu on my HD Ide but... at this point... How can I do? ](*,) 

Tnks to all in advance.

---

### Post by timgood on 2006-10-30
There is a problem with certain SATA drives being recognised by the new Edgy kernel. My system is broken following an upgrade. There does not appear to be any solution to this problem at the present. Good luck - maybe you will get more help with this than I did.

---

### Post by KaMZaTa on 2006-10-30
> **timgood said:**
> There is a problem with certain SATA drives being recognised by the new Edgy kernel. My system is broken following an upgrade. There does not appear to be any solution to this problem at the present. Good luck - maybe you will get more help with this than I did.

I've problem with Ide/Ata HD on Breezy, Dapper, Edgy. Sata HD are recognized.

---

### Post by KaMZaTa on 2006-10-31
:(

---

### Post by KaMZaTa on 2006-10-31
:(

---

### Post by KaMZaTa on 2006-11-02
:(

---

### Post by KaMZaTa on 2006-11-02
:(

---

### Post by KaMZaTa on 2006-11-03
:(

---

### Post by winter7 on 2006-11-03
I have the same problem. I am installing onto a computer with windows installed, but with available partitions.

Try opening the Gnome partition editor. In my case it sees the drives.

Also try this from a console:
sudo fdisk -l
That should list your partitions.

That should tell you if it's the installation program.

-Dino

---

### Post by KaMZaTa on 2006-11-03
> **winter7 said:**
> I have the same problem. I am installing onto a computer with windows installed, but with available partitions.

Try opening the Gnome partition editor. In my case it sees the drives.

Also try this from a console:
sudo fdisk -l
That should list your partitions.

That should tell you if it's the installation program.

-Dino

How can I open Gnome partition editor or type a command if Ubuntu isn't installed and Live cd dosn't start? :)

---

### Post by KaMZaTa on 2006-11-04
:(

---

### Post by KaMZaTa on 2006-11-04
:(

---

### Post by KaMZaTa on 2006-11-05
:(

---

### Post by KaMZaTa on 2006-11-05
I want install Ubuntu! Please help me!

---

### Post by KaMZaTa on 2006-11-06
:(

---

### Post by pattymnaish on 2006-11-06
Download the System Rescue CD iso from [http://www.sysresccd.org/](http://www.sysresccd.org/) , and boot into it. You can run QTParted (PartitionMagic clone) from the CD, and use console commands.

---

### Post by KaMZaTa on 2006-11-06
Tnk you very much. Now I'm downloading System Rescue CD. After boot into it how can I do to start installation of Ubuntu and install it on my hd ide?

---

### Post by pattymnaish on 2006-11-06
This CD doesn't let you install linux. What it does do is let you enter the command on the other page of this thread, and to check which hard-drives linux recognises. After you've found that out, then you can work out how to install Ubuntu.

---

### Post by KaMZaTa on 2006-11-06
Suse Linux 10.1 recognize my hd ide and I've installed it there. Anyway, now I'll try to type the command *fdisk -l* with System Rescue CD and after I'll paste here output.

---

### Post by KaMZaTa on 2006-11-08
Ok, command *fdisk -l* typed on System Rescue CD show me _all partition_ of _all my hd ide and sata_. Now how can I do? Tnks

---

### Post by KaMZaTa on 2006-11-08
:)

---

### Post by KaMZaTa on 2006-11-08
:(

---

### Post by KaMZaTa on 2006-11-09
:(

---

### Post by SRParda on 2006-11-09
**What kind of configuration have your BIOS related to hard disk ?**

Some BIOS can redirect some disk SATA to be recognized as IDE, and I think that could ocult your real IDE disks.

[COLOR="DarkRed"]But BE CAREFUL if you change your configuration, your SATAs DISK could not be detected in other operating systems if you have installed in SATA.[/COLOR]

In some Intel BIOS you can select SATA disks as IDE , Enhanced or RAID.

---

### Post by SRParda on 2006-11-09
Your motherboard specification for disk is this:

[COLOR="DimGray"]Intel® ICH6R South Bridge:
*1 x UltraDMA 100/66/33
*4 x Serial ATA with IntelR Matrix Storage Technology with RAID 0, 1 support
Silicon Image® 3114R RAID controller:
*4 x Serial ATA with JBOD, RAID 0, 1, 10, 5 (RAID 5 software patch available, no WHQL)
ITE IDE RAID controller:
* 2 x UltraDMA 133/100/66 with JBOD, RAID 0, 1, 0+1 support [/COLOR]

It's probable you have both IDE disks installed in the ITE raid controller.

Usually RAID controllers drivers in linux are provided by    **[COLOR="Navy"]fakeraid[/COLOR]** package in linux. You must check for support for ITE IDE RAID controller in it.
In ubuntu dapper you could load the driver getting fakeraid packages once you started the graphical installation (that loads like a LiveCD), then you can mount the disks and then install Ubuntu in them. ALternate install CDs should include RAID drives too.

But it will be easiest to connect your IDE drive to the one standard IDE UltraDMA controller of the 925X chipset. But your DVD units will not work in the  ITE controller. (You will have to install 1 HD and 1 DVD in that conector as master and slave)
Or reconsider install in a SATA disk partition.

---

### Post by KaMZaTa on 2006-11-09
I don't think that It's this the problem because I've already try to remove all Sata HD and the situation dosn't changed. Anyway, I've already installed in those HD Ide Suse Linux 10.1 that I'm using now. What i want do is substitute it with Ubuntu but I can't do this for this reason. Tnks the same for your interesting.

---

### Post by KaMZaTa on 2006-11-09
> **SRParda said:**
> Your motherboard specification for disk is this:

[COLOR="DimGray"]Intel® ICH6R South Bridge:
*1 x UltraDMA 100/66/33
*4 x Serial ATA with IntelR Matrix Storage Technology with RAID 0, 1 support
Silicon Image® 3114R RAID controller:
*4 x Serial ATA with JBOD, RAID 0, 1, 10, 5 (RAID 5 software patch available, no WHQL)
ITE IDE RAID controller:
* 2 x UltraDMA 133/100/66 with JBOD, RAID 0, 1, 0+1 support [/COLOR]

It's probable you have both IDE disks installed in the ITE raid controller.

Usually RAID controllers drivers in linux are provided by    **[COLOR="Navy"]fakeraid[/COLOR]** package in linux. You must check for support for ITE IDE RAID controller in it.
In ubuntu dapper you could load the driver getting fakeraid packages once you started the graphical installation (that loads like a LiveCD), then you can mount the disks and then install Ubuntu in them. ALternate install CDs should include RAID drives too.

But it will be easiest to connect your IDE drive to the one standard IDE UltraDMA controller of the 925X chipset. But your DVD units will not work in the  ITE controller. (You will have to install 1 HD and 1 DVD in that conector as master and slave)
Or reconsider install in a SATA disk partition.

Yes, my Ide HD are connected in ITE IDE RAID as "standard" Ide and not configured as Raid.

Now I take a look but, give that Suse and System Rescue CD recognize all HD without problem, I can't understand this. Tnks

---

### Post by KaMZaTa on 2006-11-09
Any other idea?

---

### Post by KaMZaTa on 2006-11-10
:(

---

### Post by KaMZaTa on 2006-11-10
:(

---

### Post by KaMZaTa on 2006-11-16
:(

---

### Post by KaMZaTa on 2006-11-17
:(

---

### Post by KaMZaTa on 2006-11-28
:(

---

