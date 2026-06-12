---
title: "Can't Install Ubuntu on abit IP35-Pro"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by fairlady350z on 2007-09-18
Hi all,

I'm trying to install Linux MCE, but first need to install either Ubuntu or Kubuntu.
I downloaded both the GUI installer and the alternate version (text based) of Ubuntu and Kubuntu, all end with the same result:

I hit the Install button, I see a preloader, after it reaches 100% I see a dash blinking on the top left corner but nothin happens after 5-10 mins of waiting. 

Here are a few steps I have taken before I decided to post in this forum.
1. Switch from IDE to AHCI (doesn't work)
2. Use the alternate version (ubuntu and kubuntu don't work)

Here's te new system (it has Vista on it)
Mobo: Abit IP35-Pro
CPU: Q6600 (GOStepping)
RAM: Patriot 2GB
Video Card: PNY 8800GTS 320mb

I'm pretty sure the disc is just fine, I tried them on my laptop, it loads alright.

Any ideas and suggestiosn are greatly appreciated!!

Thanks

---

### Post by fairlady350z on 2007-09-18
anyone?

---

### Post by DownTown22 on 2007-09-18
You might want to check out Pumalite's post (#6) on this thread:

[http://ubuntuforums.org/showthread.php?t=544806]("http://ubuntuforums.org/showthread.php?t=544806")

I haven't been able to give it a try yet though.

---

### Post by Zenham on 2007-09-18
Please read this for the solution. The long and the short: Either your HD and your CD/DVD drive need to both be SATA (AHCI on, Compatible mode) or running in IDE mode. half and half does not work.

[http://ubuntuforums.org/showpost.php?p=3372889&postcount=47]("http://ubuntuforums.org/showpost.php?p=3372889&postcount=47")

---

### Post by fairlady350z on 2007-09-18
Thanks all for the help.
I read the same solution in this forum last night.
But I haven't been able to try it out because the second HD (IDE) is quite crucial for me that's where all my work is in. Since I'm thinking to switch between Vista and Linux, I wonder if there's a work around this without literally unplugging the cable.

The third HD (external USB, it does eSATA as well) is to store all the recorded TV, since I'm going to use this box as an entertainment unit as well.

Oh also I just remember that my DVD drive is a USB external drive as well. So this is rather complicated.

---

### Post by crazedgremlin on 2008-03-15
Try booting up with the 'irqpoll' option.  Worked for me.

---

### Post by king vash on 2008-04-26
Two tricks

for the IP-35 enable AHCI mode or try irqpoll
for the IP-35E move the sata cords to the highest port number (6\5\2\1)

---

### Post by salvador24 on 2008-05-09
thanks a lot! I was bashing my head against the wall with this problem for a little while until i found this thread!  I have an IDE DVD-ROM and SATA drives...

---

### Post by Sb1 on 2008-06-03
I have a Floppy drive but I disabled it in Bios because I didn't think I'd really need it.  But after some reading some people said to enable it to see if that worked, it didn't.  

But I came across a suggestion to hit F6 and input:

all_generic_ide floppy=off irqpoll

and hit enter and this worked great.  

I still had floppy on I forgot to turn it off. But I don't know if the above --  floppy=off  --  needs it to be on for it to work or not. I had and planning to leave everything set to IDE in BIOS.   
I have 1 Samsung sata dvdrw on port 5 or 6. 1 Seagate sataII with Winxp already installed on sata port 1.  2nd hd is a 160gb sataI that was fully unallocated on port 2.
--
Abit IP25-Pro v1.1  Came with bios #14
Q6600 & GSkill Two - 2gb PC8000 sticks

---

### Post by nickv2002 on 2008-06-26
I have an Abit IP-35E that had this issue.  The fix was some combination of the following (not sure if one or both are required by I eventually got things working)

1) Moving the SATA drives to ports/channels 6 (for my Linux disk) and 5 (for my Windows Vista disk)
2) Putting both drives into IDE mode, done for each SATA channel in BIOS via 'Standard CMOS Features'  (in order to harmonize with my ATA/IDE DVD drive used for the installation)

After doing these things my BIOS features were all messed up however... so I did a CMOS reset and after that everything works as it should.

Be sure if you're dual booting to enable BIOS level USB keyboard and mouse support (assuming you're not using PS2 devices) so that you can select which OS you want to boot into in GRUB.  These options are in BIOS under Integrated Peripherals -> OnChip PCI Device -> USB Device Setting.

Thanks for everyone's help and advice here.

---

