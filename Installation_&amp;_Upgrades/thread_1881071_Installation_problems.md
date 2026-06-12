---
title: "Installation problems"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by balch4 on 2011-11-14
I'm attempting to install the current Ubuntu distribution, v. 11.1 I believe.

Here's my problem.  I'm using a desktop PC with two HDD's, one devoted to Microsoft XP Pro, and the other one devoted to Ubuntu 6.1 Edgy.  (The Microsoft HDD is currently totally disabled, totally controlled by a Microsoft Security forced request to buy their new security package in order to remove various viruses.  I'm not going to be held up by Microsoft, so the HDD is unusable, TOTALLY unusable.)

I installed the GRUB when I installed the 6.1 Edgy back sometime in 2006, I think, before putting the desktop PC in storage.

I've now maxed out the RAM on the desktop PC, so the PC is very usable.  And I've created a separate CD with the Ubuntu 11.1 on it.

How do I reboot from the CD-ROM drive (or from the CD-RW drive) and load the Ubuntu 11.1 onto the HDD devoted to the Ubuntu?  Changing the boot sequence to the CD-ROM drive hasn't worked.  Do I need to change the GRUB to the 11.1 version or what?

I'm really stuck and don't know what to do.  I appreciate any help.

--Bob Balch

---

### Post by hansdown on 2011-11-14
Hi, balch4.

Can you tell us, what hardware you are using?

It will help the helpers.

---

### Post by Quackers on 2011-11-15
Is it a USB CD-ROM? If so, did you select USB CD-ROM or internal CD-ROM in your bios?

---

### Post by balch4 on 2011-11-15
The PC is a Dell Optiplex GX270 Series.

The Setup BIOS reveals the following:

Drive Configuration
     Diskette Drive A.....3.5 inch, 1.44 MB
     SATA Primary Drive........Hard Drive
     SATA Secondary Drive.........Hard Drive
     Primary Master Drive......OFF
     Primary Slave Drive......OFF
     Secondary Master Drive.....CD-ROM Device
     Secondary Slave Drive......CD-ROM Device
     IDE Drive UDMA....On

Hard-Disk Drive Sequence
     1. System BIOS boot devices
     2. USB device (not installed)

Boot Sequence
     1. Hard-Disc Drive C:
     2. IDE CD-ROM Device [I've tried booting using this choice and it doesn't appear to 
         recognize this IDE CD-ROM Device, whether the Ubuntu CD with v. 11.1 is in the 
         CD-ROM drive or the CD-RW drive]
     3. Diskette Drive
     4. Integrated NIC (disabled)

Installed System Memory.....2560 MB DDR SDRAM

Fast Boot....Off

OS Install Mode.....Off

When I go to the Boot Menu rather than the Setup BIOS, and select "IDE Drive
Diagnostics," this is what it shows:

IDE Drive Diagnostics, running, please wait.....

Primary SATA:  ST3120026AS - Pass
Secondary SATA:  Maxtor 6V200E0 - Pass
Primary IDE
     Drive 0: No device
     Drive 1: No device
Secondary IDE
     Drive 0: SAMSUNG DVD-ROM SD-616T - Diagnostics not supported
     Drive 1: NEC DVD+RW ND-2100AD - Diagnostics not supported

Nothing else from the many line items in the Setup BIOS seem relevant.  But let me know if there's additional information needed.

Thank you for any help you may provide!!!!!!

---

### Post by darkod on 2011-11-15
If you tried booting from cd-rom why isn't it first in the boot sequence? Or did you try pressing F10 F12 or similar and just using a boot menu outside the BIOS?

Just in case, can you set cd-rom as first boot device and try?

Also, you burned the cd properly using the ubuntu image, you didn't simply copy the ISO on the cd as a file, right? It's a stupid question, but it has happened. :)

---

### Post by balch4 on 2011-11-15
Oh yes, I've tried many many combinations using the F12 key to open the Boot Menu, and none of them work.

Also I've checked the CD after burning it with the Ubuntu v. 11.1, using my Ubuntu Edgy v. 6.1, and the entire nearly 700MB of data is on the CD.

So I'm still stuck.

---

### Post by darkod on 2011-11-15
Do you have another computer to check if the cd will boot on it?

Also can you try another bootable cd in the Dell to see if it boots?

It all points that it doesn't even try booting from the cd-rom. Try making a usb stick with ubuntu on it and boot the Dell with it. It has the option to put USB Device before System Boot devices.

---

### Post by balch4 on 2011-11-15
Yeah, I put the cd with the Ubuntu 11.1 in my laptop and it shows the files, with 695MB of volume.  So the cd is OK I believe.

I don't have a USB stick, or a thumb drive, but I'll have to go buy one, I guess, and give it a try after loading Ubuntu 11.1 on to it.

---

### Post by darkod on 2011-11-15
> **balch4 said:**
> Yeah, I put the cd with the Ubuntu 11.1 in my laptop and it shows the files, with 695MB of volume.  So the cd is OK I believe.

I don't have a USB stick, or a thumb drive, but I'll have to go buy one, I guess, and give it a try after loading Ubuntu 11.1 on to it.

No, not just whether it shows the files. If you set the laptop to boot from cd-rom can you boot with the ubuntu cd?

There is difference between showing the files and booting. Did you butn the cd with option like "burn image on cd" or simply created it as data cd and copied the iso file? In both cases it will show 700MB full but it only works if you burn it as image.

Try booting your laptop with it.

---

