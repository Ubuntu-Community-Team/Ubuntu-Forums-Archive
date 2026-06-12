---
title: "Ubuntu virgin trying to install 7.10, requires advice"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by brown049 on 2008-04-19
I have burned an the following ISO image 'ubuntu-7.10-desktop-i386' to DVD.  I then boot from the DVD and choose 'Start or Install Ubuntu' from the menu.

I then see a nice 'Unbuntu' Logo and a progress bar going side to side on the screen.

Then a black shell screen appears displaying the following:

[B]BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu7) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [84.171882] ata1.00: failed to set xfermode (err_mask =0x40)
[90.223588] sd2:0:0:0:[sda] assuming drive cache: write through[/B]

***Can anyone tell me whats gone wrong?***

The spec of the machine I am installing onto is:

Vostro 400 E6550 Core 2 Duo Processor (2.33GHz, 1333Mhz FSB, 4MB cache) 

Memory 3072MB 667MHz (2x1024 + 2x512) Memory 1 S

Hard Drive 1TB Serial ATA Non Raid (2x500GB) 7200Rpm Dual HDD Config 1 S

Roxio Creator / MYDVD 9.0 (Vista & XP) 1 S
16X DVD+/-RW 1 S
Integrated Intel Graphics Media Accelerator 3100 1 S
Audio Integrated HDA 7.1 Dolby Digital capability 1 S
UK/Irish Keyboard & Mouse Dell Wireless Bluetooth Black & Optical Mouse 1 S
English Windows Vista Home Premium 1 S

Thanks in advance for your help.

Kind Regards

Mike

---

### Post by Pumalite on 2008-04-19
This might help:
[http://ubuntuforums.org/showthread.php?t=623604](http://ubuntuforums.org/showthread.php?t=623604)

---

### Post by brown049 on 2008-04-19
Thanks for the advice.  Still having a problem unfortunately.

My BIOS was v1.0.11 I have now installed the latest one from DELL v1.0.13.

However, the message I now get was [103.873547] ata1.00: revalidation failed (errno=-5)

The post you directed me to said that updating to BIOS v1.0.8 worked.  Not sure I can get this now since its an old version :-(

Anymore thoughts would be much appreciated.

Thanks

Mike

---

### Post by Pumalite on 2008-04-19
I assume you are using the Alternate CD.??

---

### Post by brown049 on 2008-04-19
?  Err I think I'm using the 86 compatible desktop ISO?  What does the ALternate CD do?

Apologies for my ignorance.

Mike :-)

---

### Post by brown049 on 2008-04-19
> **brown049 said:**
> ?  Err I think I'm using the 86 compatible desktop ISO?  What does the ALternate CD do?

Apologies for my ignorance.

Mike :-)

Downloading the 'Alternate' Now to see if it helps :-)

---

### Post by Victormd on 2008-04-19
The alternate CD should do the trick...
You might run into some more problems because of your graphics card though, at least to get 3D support (but this should be only after you're up and running and trying to "fancy-it-up").

Question about your HD setup: You have 2x500GB HDs that are not set up in RAID but shows as 1TB? Or did you mean that you have 2x500GB HDs that total 1TB? (not sure I'm being clear)

---

### Post by brown049 on 2008-04-19
The HD info I originally stated is from the dell order form.  I'm sure thare not in RAID configuration.  However, they are 2 physically seperate 500gb drives.  But from what I can tell VISTA sees them as one big drive although partition into seperate ones.  Haven't really got my head round the exact setup to be honest.

Cheers

Mike

---

### Post by Victormd on 2008-04-19
Ok, so you're dual-booting Ubuntu & Vista...
If you don't know your HD setup, that might make things a bit harder for you to install... I'd suggest you figure out your HD config, because from the error you posted, it really seems like it's HD related...

---

