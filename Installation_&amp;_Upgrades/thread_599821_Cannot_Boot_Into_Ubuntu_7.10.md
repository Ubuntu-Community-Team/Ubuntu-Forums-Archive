---
title: "Cannot Boot Into Ubuntu 7.10"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by mcquis88g on 2007-11-01
Hi chaps/chapess',

I am trying to install ubuntu after hearing much ranting and raving.

I already have vista installed on a SCSI drive.

And I had a spare 80Gb IDE drive lying around so I stuck it in and installed ubuntu to it.

ubuntu installs successfully, but when it asks about other OS's it fails to detect my vista OS, I can load file manager and mount all drives (including the vista NTFS drive partitions, I can see the darn Windows directory). But when I restart the PC no grub boot loader.

Could this be my jumper cable settings? I think my SCSI vista HD is set to Primary Slave, and my IDE Secondary master would that make a difference.

I loathe vista with a passion but want to keep it short term until I get internet etc fully setup on ubuntu.

Can anyone help, or am I going to have to stick with Bloatcrosoft.

I tried restoring GRUB Boot Loader but I don't even think its been installed on my linux partition.

---

### Post by flytier on 2007-11-01
I screwed up my bootloader on Windows when I installed Gutsy to an external drive.  I fixed Bootloader in just a few minutes on Windows with [Super Grub Disc]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), the program lets you customize the bootloaders or repair broken ones. Very cool, saved my Vista install, not sure if thats a curse or a blessing.:lolflag:

---

### Post by mcquis88g on 2007-11-02
I've already tried super grub disk, but everything i try it keeps giving me an error 15 unable to read file type.

Any other suggestions? I would like to use ubuntu but obviously installing and getting it to boot up would be nice.:confused:.

---

### Post by mcquis88g on 2007-11-02
I believe the problem may be because I have an Acer Desktop machine, and I believe that this uses the MBR differently.

I will keep me posted

---

### Post by ger_mulvey on 2007-11-02
I have a similar issue.
I have an sata and ide drive the sata being the primary boot device. It has xp on and three partitions two 100gb and a 35gb I installed ubuntu 7.10 32bit to the 35 gb partition and it installed ok and on reboot nothing. Straight into xp. Tried again on the other drive after trying a guide to setup grub again. Similar setup two 100gb and a 30gb partiton tried to install onto 30gb partition all went well. Rebooted and got the same windows booted no grub! Tried to run grub again from livecd but no go. Now I have had 7.04 on here previously. 
So I'll maybee try that again.

---

### Post by mcquis88g on 2007-11-05
Chaps I found out this was a problem with the SATA, IDE configuration.

the Grub Boot Loader assumes that the IDE is the bootable drive (even when it is isn't). I tried a partition off the SATA directly this did give me the grub boot loader option and detected VISTA, but knackered up the MBR.

By this time I was totally fed up and unplugged my IDE drive and wiped vista (ubuntu then loaded). Did have a mild panic attack when realised I had deleted all my kids pictures but then remembered I had backed up to omnidrive

However my motherboard bas a built in Nvidia 6100 graphcs card, and I didn't install the drivers, so after a restart I couldn't read the screen, so had to reinstall the OS and then the drivers.

All in all I'm not overly impressed with Ubuntu's installation at the moment, having said that the internet worked out of the box, I have a cool background, and also I can actually load applications pretty quickly considering I only have a small amount of ram(512Mb/Shared with Graphcs Card).

Even considering my installation experiences I still prefer ubuntu than vista.

Reasons Vista is rubbish:

1. Vista assumes everyone is a noob, and warns you about everything. Its like a digital version of my gran (god bless er).
2. When I tried to install SQL Server 2005 express, Vista warned me this wasn't compatable with Vista?????
3. I don't have 3Gb of Ram or a 400Gb Hard Disk to run it on.
4. SkyAnytime Doesn't work on it (although I did find a hack).
5. Nag screens (I know I can turn them off thru reg hacks, but why should I have to, I know I've clicked on a program now install the damn thing).
6. I have to wait 10 minutes for open office to load.
7. I had to go into windows explorer to allow me to download an ssl certificate from Windows E-mail (why????).
8. My windows menu bar disappears and reappears at the top of the screen but I have to still go to the bottom of the screen to use it (arrgghgghh)
9. Involuntary Screen Dimming (I hated this)
10. ie7 (pah)

Reasons Ubuntu is cool

1. Wireless internet worked out of the box (it even worked on LiveCD)
2. Cool Backgrounds
3. Innovative programs rather than churning out same rubbish
4. Its quicker.
5. Looks better.
6. Synaptic Programs manager (this is such a cool idea)
7. It is buggy but I can actually fix it myself if need be.
8. Firefox works identically, and same plugins are avaliable
9. Most of the programs are free or open source.

---

### Post by adrian15 on 2007-11-06
> **mcquis88g said:**
> Chaps I found out this was a problem with the SATA, IDE configuration.

the Grub Boot Loader assumes that the IDE is the bootable drive (even when it is isn't). I tried a partition off the SATA directly this did give me the grub boot loader option and detected VISTA, but knackered up the MBR.

Hello, have you finally solved your problem? SGD 0.9670 includes the EASY LIVE SWAP option that can be helpful in your case. 

Can you please give it a try and leave here your impressions?

Thank you.

adrian15

P.S.: If the drives boot order are bad detect you are advised to edit /boot/grub/device.map and to edit the groot line on /boot/grub/menu.lst and run update-grub again.

---

### Post by mcquis88g on 2007-11-06
Thanks Adrian I will take a look I just disconnected the IDE and installed ubuntu to the live partion overwriting Vista.

But thanks for the info.

---

