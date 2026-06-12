---
title: "Install/live issue with SATA only system"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by brianjpugh on 2008-10-19
I'm having issues getting Ubuntu 8.04 (i386 desktop) to install or live demo on my computer.  Really, it is 2 computers that I'm having issues with.  The other computer is busy so I will focus on this one:

AMD 2700+
Abit NF7-S
No IDE devices
Sata 1: Lite-on CD-RW (IDE drive installed with sata->pata converter)
Sata 2: Maxtor Sata I (250gb)

This computer checks out with memtest and WinXP.  I have used this CD in other systems so I know it is good.  I have had other configurations of this box in the past (with IDE drives installed) and they worked with the Live demo.  The issue I'm having is during bootup the system dumps to busybox with the following error:

```

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: cmd a0/01:00:00:80:00/00:00:00:00:00/a0 tag 0 dma 128 in
ata1.00: status: {DRDY}
ata1.00: Revalidation failed (errno=-5)

```

I have seen in other places on the forum for the all_generic_ide boot option, but all that does is change the error messages from ata1 to ata3.  

I mentioned that I'm having this issue with 2 computers.  the other is a bit more modern:

AMD X2 6400+
Gigabyte GA-M57SLI-S4
No IDE devices
Sata 1: DVD-DL-R
Sata 2: Western Digital Sata II (160 GB)
Sata 3: Western Digital Sata II (320 GB)

The only thing I can think off (which I have yet to try out) is it is happening because my first Sata device in both computers is a optical drive.

Update 10/21/08:

I grabbed a copy of 8.04 x86_64 Desktop and the live demo worked on my Gigabyte Computer.

Update 11/8/08:

I grabbed a copy of 8.10 i386 Desktop and the live demo worked on my NF7-s board.  Will try installing it next.

Update 11/14/08:

Install worked fine, but still gives me the busy box ata1 error when I boot from the hard disk.

---

### Post by Dynamo_Joe on 2008-10-20
Hi brianjpugh, 

I was running Hardy (and Fiesty) on the same motherboard but with a 1.8GHz Athlon and 1GB of RAM. 

My issues with it was that whenever I plug anything into the onbaord SATA connectors I will loose my IDE optical drives on the second IDE channel (maybe the IOs are shared on this MB). 

In the end, I brought a PCI SATA controller and this resolves the issue. 

My only suggestion is to try and move the connections, maybe put the optical drives onto SATA1 instead of SATA0 and make sure the boot order is correct in the BIOS. 

Apologies but I've "dismantled" the old PC as I've just upgraded to a new PC.

---

### Post by Dynamo_Joe on 2008-10-20
Hi brianjpugh, 

Just noticed that you are using a SATA->PATA controller, try plugging your IDE optical drive directly onto the IDE connector on the MB. 

If it clashes with the IDE2 connector, then try it on the IDE1 connector and remember to set the boot order in the BIOS.

---

### Post by cariboo on 2008-10-20
Check and see if there is an AHCI setting in the bios. This is set to ide emulation mode as some version of XP can't deal with sata drives without installing extra drivers. If you have SP3  you shouldn't need to install the extra drivers.

Jim

---

### Post by brianjpugh on 2008-10-20
I have tried looking for the AHCI setting in both the motherboard bios and the sata controller bios, but I failed to find it.  Does it appear under a different name or is there a common location for it?

I have no problems installing XP on either motherboard.  Over the years I have used a basic install, sp2 and sp3 install disc.  I do have to pull out the driver floppy but it works great.  It even boots from the optical on the sata controller without any fuss.

---

### Post by brianjpugh on 2008-10-20
Dynamo_joe,

I plan on upgrading the IDE CD-R in my computer with a SATA DVD drive so I wanted to match it as close as I can.  I do believe though the reason that I put it on the SATA 0 connector was because the SATA controller bios boots from the first device it can.

---

### Post by soulster on 2008-10-20
I just had the same error on a brand new PC.

It's a Dell Inspiron 530s
Intel 2.2GHz Pentium Dual Core
SATA 320G Hard Disk

I corrected the problem by going into BIOS and switching the SATA mode from IDE to RAID.  After that, it boot with no problem and installed without issue.

I've read on other forums that this is an issue with the IDE controller, which my fix would seem to confirm.

---

### Post by Dynamo_Joe on 2008-10-21
Hi brianjpugh, 

There is no "AHCI" option on this MB's BIOS ... sorry. When I had the clash of the onboard SATA ports with the second IDE channel, I went out and bought a PCI SATA controller card to bypass the problem! 

The other thing that you could try is to use the SATA optical drive from your new PC and connect it to SATA1 and move your HD to SATA0 and see if that helps. 

If it comes good, then you will definitely need to get a new SATA optical drive sooner rather than later ... sorry that I can't help in actually testing it out on my MB as it is out of the computer after the upgrade.

---

### Post by brianjpugh on 2008-10-21
Dynamo_joe,

I did a swap of the drives last night and all I got was booting from the harddisk since the controller saw it first.  I do have a Rosewill PCI SATA controller I'm saving for a htpc build I might try out in it.  The controller on the NF7 is a Silicon Raid with a very limited bios.  I believe all it does is all you to manage RAIDS.  Know of any hidden menus in it?

On my Gigabyte board I grabbed a copy of x86_64 from the torrent server.  It worked a lot better this time.  Last time I tried that computer I had a i386 disk which gave me problems.  So I decided to grab the i386 image again and try to reburn the disk to see if it works better, maybe if I still have the issue I will try a 8.10 disc.

---

### Post by Dynamo_Joe on 2008-10-25
Hi brianjpugh,

You might be in luck as I need to rebuild the "old PC" to get my previous installations of Fiesty and Hardy (on separate HDs in a removable rack) working again to transfer some data held in them. 

Don't know when though as I'm a little bit busy out here in the real world. 

Can't remember if there were any messages during boot but with the Silicon Image SATA PCI Controller card, I had a boot message telling me to press "Ctrl S" for setup. 

I'll try to get back to you soon but it'll probably take me a week to put the old PC back together again ...

---

### Post by brianjpugh on 2008-11-08
Thanks for all the help on this.  However, I had time this weekend to grab a copy of 8.10 i386 Desktop and the live demo works with my setup.  I want to install it but the XP part of the box needs to finish some work I have tasked to it.  Then I will install it and let you know how it works.

---

### Post by brianjpugh on 2008-11-14
Sorry to bring bad news.  I did get to install, but when I boot from the hard disk it drops down into busy box with the same error I was having before.  This is odd to me since I figured it would work once I got it to the hard disk.

---

