---
title: "raid server 7.04 installation question"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by andrewwk on 2007-06-22
Greetings all,

I am currently trying to install ubuntu server 7.04.  I have an Intel D6965WH motherboard that has six ports for SATA hard drives.  I want to do a hardware raid so that a raid 0+1 is intact when installing ubuntu server.

I would like to install the Raid drivers before/during the installation of ubuntu.  When I install ubuntu I get a prompt for language, then keyboard language, then partitioning the hard drives.  Is there anyway to install the drivers and if so, is there anyway to load them before the partitioning part of the installation?

Thanks,
WK

---

### Post by andrewwk on 2007-07-24
Thanks for all the help.  I found out that the motherboard has a fake hardware raid.  There was no way to do a true hardware raid with the motherboard.  I bought a 3ware 9650SE-4LPML to raid the hard drives together.  I created a Raid 0+1 in the 3ware Bios.  When I installed ubuntu 7.04, there was only one drive that showed up. That is what I wanted.

WK

---

### Post by andou on 2007-07-25
Well, perhaps no one answered your question, but it appears that you have answered mine.

Thank you for your post :)

I was trying to find out how to install ubuntu with Raid-0. I have 2x320GB SATA HDDs. I have an nForce-4 mobo, and was using the nVidia raid drivers in Windows.

What I am inferring from your post is that this is not a 'true' hardware Raid, and that in order to get a real Raid-0, I will need a PCI controller. Without that, it's not going to happen with Ubuntu. Is that correct?

---

### Post by andrewwk on 2007-07-25
That is correct.  You will need some raid card to obtain a true hardware raid. I recommend a 3ware card.  Most forums that I have looked at keep directing me to 3ware.  Here is the card I got: [ 3ware 9650SE-4LPML]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042").  The only down side is that they don't have support for ubuntu 7.04 yet.  This means that it is harder to install the CLI and the 3DM2 software.  CLI is needed for sending failure e-mails and lighting LEDs and 3DM2 is needed for hot swap.  What I like about the card is that after you install the hardware, you can go into the 3ware bios and create the raid without software installation.  Hope this helps.

WK

---

### Post by andou on 2007-07-25
Thanks for your advice. I have just decided to do a regular install; no raid for now.

I'm kind of wondering if it's worth the $350 for a Raid Controller. I have a couple of questions about that.

1) How much of a performance difference will you get versus no raid? (Of course, the inherent benefits of Raid-1 will not be measured in speed, so I'm referring completely to Raid-0)

2) Considering that the controller costs $350, money doesn't seem to be that large of a factor in deciding which hardware to get, why use S-ATA drives and not SCSI? What performance difference would be available from that.

3) Finally, would the performance difference between an install on an S-ATA drive (non raid) and a Raid-0 setup with a PCI-controller and S-ATA (or SCSI) drives be worth the costs involved?

---

### Post by strueb on 2007-07-28
Sorry about seeming to hijack your post since I'm not quite following in sequence, but...You guys are talking about hardware RAID, and faking a RAID configuration, so I have a question.  I have a bright, shiny, new HP m8120n with Vista and what it says is a RAID controller (not enabled), Intel designation :Intel (R) 82801 HR/HH/HO SATA RAID Controller.

On boot up I see two drives (both SATA, since they're the same type of drives, both Hitachi 320G drives.)

I absolutely cannot screw up my Vista installation (I've already had to restore to factory specs once!), since I need it for remote access to work.  I figured I'd just do a dual-boot installation with GRUB figuring everything out.  Until I started reading about RAID and ubuntu.

Just because I have the Intel controller installed, since I'm not (that I know of) running a RAID configuration, what are some of the potential problems?  (I mean, I've seen some, err, interesting posts here:), and...)  It seems to be getting scarier and scarier the more I read.

I've googled that "controller" and haven't found a whole lot of information, and it only became a concern because I *really* would like to get ubuntu installed on this beast.  From the LiveCD, I'm very impressed with how Feisty Fawn plays with my computer and its myriad devices.

Anyway, enough rambling - sorry.  Thank you very much!

---

### Post by iduriduridur on 2007-07-30
The 82801 HR/HH/HO SATA RAID sounds like it is a "software" raid device. A true hardware SATA raid device is usually a separate device like a PCI, PCI-e or PCI-X device with it own CPU and RAM on it. 

To see how your disk are setup without breaking anything try downloading systemrescue CD and running 
gparted. It will show your disks layout graphically.

---

