---
title: "Ubuntu install on a Dell Vista laptop"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by glok_twen on 2007-03-03
hi. i bought a dell laptop that regrettably has vista. i want to dual boot ubuntu, or even scrap vista and use only ubuntu. trouble is i have used the 6.10 live cd as well as the alternate install cd and every time i get to the partition stage, it says it doesn't detect any disks. can you believe it?

so i hunted through the bios options seeing whether there was some sort of lock on the hard drive and didn't see anything.

has anyone gotten ubuntu installed on a dell vista laptop? did you encounter this?

---

### Post by ssavelan on 2007-03-03
Oh wow, that is horrible.  I'll keep my eye's peeled for vista laptops.

---

### Post by Gerard Barberi on 2007-03-03
> **glok_twen said:**
> hi. i bought a dell laptop that regrettably has vista. i want to dual boot ubuntu, or even scrap vista and use only ubuntu. trouble is i have used the 6.10 live cd as well as the alternate install cd and every time i get to the partition stage, it says it doesn't detect any disks. can you believe it?

so i hunted through the bios options seeing whether there was some sort of lock on the hard drive and didn't see anything.

has anyone gotten ubuntu installed on a dell vista laptop? did you encounter this?

See what happens if you use an XP CD.  

Also what edition of vista?  It might be the Business or enterpise one.  I think it's supposed to encrypt drives for security.

---

### Post by Prometheus.172214 on 2007-03-03
What Dell laptop are you using? Can you post the service tag for it? I can look up the system specifications on the support.dell.com website and find out what controller is in use. I have heard of Windows operating systems not detecting hard drives due to SATA / RAID Controller issues, however as far as I know, this issue has occured only on desktop systems that use various versions of RAID. I can give you more details if I get the Service Tag or the Model of the Dell notebook that you have. 

Also, if you can boot to the the command mode in the Live Disc, you can try this : 
ls /dev/hda it should give you some output or you can also try sudo fdisk -l /dev/hda

If it is not detected you would most probably get a "No such file or directory" error. Let me know what output you get.

I have something similar going on my laptop. Not the exact same though. But I got the suggestion of those commands from "kidders" in his / her reply to my post and I am guessing this should tell you what the hard drive is doing. I haven't given it a shot yet. Maybe in an hour, time will be merciful on my and I can pack for home and sit on my laptop and figure things out.

"Windows Vista Enterprise Or Business does use an encryption technology named BitLocker. I have never tried reading a Bitlocked partition from a Live Cd of Linux. However, I think I can give it a shot. I'll try an installation here and let you know. It sure sounds plausible".

---

### Post by glok_twen on 2007-03-03
hello all - thanks for your replies. it is running vista home premium. here is the hardware info easily available. the service tag says bblrkc1. also  will try the ls /hda0 tonight.

Inspiron 1501 
Mobile AMD Sempron™ 3500+ (1.8GHz/512KB), FREE Upgrade to Genuine Windows Vista™ Home Premium with 1GB of memory
Inspiron 1501  Mobile AMD Sempron™ 3500+ (1.8GHz/512KB) 
LCD panel  15.4 inch Wide Screen XGA Display with TrueLife™ 
MEMORY  1GB DDR2 SDRAM at 533MHz, 2 Dimm 
VIDEO CARD  ATI RADEON® Xpress1150 256MB HyperMemory™ (Integrated) 
HARD DRIVES  60GB Hard Drive 
OPERATING SYSTEM(s)  FREE Upgrade to Genuine Windows Vista™ Home Premium with 1GB of memory 
Network Card and Modem  Integrated 10/100 Network Card and Modem 
Combo/DVD+RW Drives  24X CD Burner/DVD Combo Drive 
Sound Card  Integrated Audio 
Wireless Networking Cards  Dell Wireless 1390 802.11g Mini Card (54Mbps)

---

### Post by Prometheus.172214 on 2007-03-03
All right. First the Home Premium version rules out any interference from the Bitlocker. Home Premium uses transactional NTFS Volumes and are detected by Linux the same way as in Windows XP. 

I would like to find out what output ls /dev/hda and sudo fdisk -l /dev/hda give you. 

I'll check on the controller details and keep you informed.

---

### Post by ssavelan on 2007-03-04
> **Prometheus.172214 said:**
> 

Also, if you can boot to the the command mode in the Live Disc, you can try this : 
ls /dev/hda it should give you some output or you can also try sudo fdisk -l /dev/hda

".

I have had great success with SCSI and SATA.  You might try the above commands replacing hda with sda.

---

### Post by x2breakoffate on 2007-03-05
hey! yeah this is one thing i had a problem with when i first made the switch to Ubuntu Linux (OMG I AM SO IMPRESSED) GO UBUNTU!
And this is pretty simple, when you boot the live cd you have to click f6 at the screen where it says other options, live cd, install with live cd etc, and when you click f6 type in pci=nomsi. It should pop up but i have had no luck with installing it on a second partition. Your better off backing up your files and erasing everything. Plus i'm trying to find a fix for wireless and i'm not sure if my sd reader works. Oh and if you do get the wireless working you have to download something to make mp3 work. So yeah, have fun! Regardless of how this sounds, its so amazing and it works so much better!!!!!!!!!

---

### Post by ssavelan on 2007-03-05
For wireless, the K network manager is unbelievably painless, in my experiences.

For mp3's, one easy way is to add libxine-extracodecs and play them with amarok or totem-xine.

:guitar:

---

### Post by agentstewie on 2007-03-05
i just got a vista laptop on hp, but i easily installed it.
shrink the vista partition using the vista tools administration software, then install ubuntu on the free partion

---

### Post by glok_twen on 2007-03-06
whoooo-rah! i got it working using the f6 command followed by pci=nomsi commands indicated above. ty all for the help!

---

