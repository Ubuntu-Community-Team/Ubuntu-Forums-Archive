---
title: "Ubuntu Studio install freezes!"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by fipoo on 2008-09-25
I don't know what more to try!
Since yesterday I'm trying to install Ububtu Studio in my new laptop... But every time the installation program freezes! It hangs in different, but nearly, times, but all of them in the early start of boot period.

As you may ask, my DVD is ok, I had tested it, and also I had installed Window$ Vi$ta on my first partition with all success!

I had also tried other distros like 64studio, Kurumin7 (a Brazillian good one!), and other... All of them seems to don't accept my hardware, as all of them hangs in some part of the boot or don't recongnize my HDD...

Ok... talking about my hardware:
Pentium Dual Core T2370
2Gb DDR2 memory
ECS Mother board with Sis 671 chipset
Sata 250Gb Western Digital HDD
ATI Mobility Radeon HD 2400 with 128Mb DDR3
Card Reader USB Hub
1.3Mp USB Webcam

Any help will be great!
Thank's!

---

### Post by trksh22 on 2008-09-25
Ok, I am very very new to Ubuntu (like less than a week!) but I was having trouble reinstalling it on my husbands laptop. I had 4 failed attempts where it kept hanging. Finally, I just went into a live session (rather than from the the main menu (where you are given the choice to install, boot from live cd, boot from hard drive, check disk for errors, etc). I went into a live Session, clicked on the install icon and it worked! Extremely fast install too. Maybe that will work for you??? :)

---

### Post by fipoo on 2008-09-25
> **trksh22 said:**
> Ok, I am very very new to Ubuntu (like less than a week!) but I was having trouble reinstalling it on my husbands laptop. I had 4 failed attempts where it kept hanging. Finally, I just went into a live session (rather than from the the main menu (where you are given the choice to install, boot from live cd, boot from hard drive, check disk for errors, etc). I went into a live Session, clicked on the install icon and it worked! Extremely fast install too. Maybe that will work for you??? :)

Are you saying that you installed ubuntu with a ubuntu live cd? It's possible?

---

### Post by fipoo on 2008-09-25
My laptop comes with a Linux called Insigne Linux and it works!
All other distros I tried are not working!
Can it be a HW problem?

---

### Post by Bibek on 2008-09-25
> **fipoo said:**
> Are you saying that you installed ubuntu with a ubuntu live cd? It's possible?
 
The Live CD is also a install CD. You can boot using the ubuntu Live CD, try ubuntu and then click install icon on the desktop to install ubuntu.

---

### Post by fipoo on 2008-09-26
> **Bibek said:**
> The Live CD is also a install CD. You can boot using the ubuntu Live CD, try ubuntu and then click install icon on the desktop to install ubuntu.

Not working too!
Neither Knoppix Live CD is working!
Could it be a HW problema? I had only sucess with Vista and Insigne Linux...

---

### Post by fipoo on 2008-09-26
Ok... I made four attempts to make it work and all the four attempts gave me differents stack points... here they are:

Attempt 1:
[	45.536271] hub 3-0:1.0: USB hub found
[	45.536340] hub 3-0:1.0: 4 ports detected
[	45.558038] usb 1-6: new high speed USB device using ehci_hcd and address 2

Attempt 2:
[	38.569727] usb usb2: configuration #1 chosen from 1 choice
[	38.569839] hub 2-0:1.0: USB hub found
[	45.569908] hub 2-0:1.0: 4 ports detected

Attempt 3:
[	37.868065] ata1.00 ATAPI: TSSTcorp CDDVDW TS-L632H, TMC0, max UDMA/33
[	37.899852] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/seio4/input/input2
[	37.901106] usb 1-4: configuration #1 chosen from 1 choice

Attempt 4:
[	49.189588] Synaptics TouchPad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[	49.226593] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/seio4/input/input2
[	49.409365] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, TMC0, max UDMA/33

Seems like it is a kind of random problem....
I'll ask you gently... please help me solving this! I tried a lot of distros and none of them worked! This makes me think it is a a hardware problem!
So ANY opinion and help will be great!

---

### Post by fipoo on 2008-09-26
Solved the problem using clocksource=jiffies cheatcode!
Now I'm installing it! Let me see if everything goes ok!
Thank's

---

