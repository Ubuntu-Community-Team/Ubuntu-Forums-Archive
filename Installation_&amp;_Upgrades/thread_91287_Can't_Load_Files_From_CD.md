---
title: "Can't Load Files From CD"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by Othersider on 2005-11-16
Hi,

My installation for Ubuntu 5.10 fails when the installer tries loading files from the CD.  I downloaded the iso from a mirror listed on the site, checked the md5 sum there, then burned it.

The option in the installer to check for disk integrity shows me an error (the problem file sometimes varies, usually it's install/initrd.gz) and says the md5 sum doesn't match, but if I get my own checksum of that file, it *does* match with the value listed in md5sum.txt on the CD.

Any ideas what the problem is?  Specs: Dell Pentium D CPU 2.80 GHz, 1.0 GB RAM, RADEON X600 256 MB HyperMemory.

Thanks in advance :).

---

### Post by ChaoticGood on 2005-11-17
I've encountered the same thing. Installation freezes when loading initrd.gz
I'm using Compaq Presario 2544 ai with 64mb ATI Radeon Omega Driver, Pentium 4 2.8G 448 mb RAM, currently on windows XP SP2.

Edit: I realized that the issue may be traced from the fact that I burned the cd from one pc and I am installing it in my notebook. Must be the difference in drivespeed, or the burning process (I read a related topic in another thread earlier). Anyway, I have resolved the issue. Thanks.

---

### Post by Othersider on 2005-11-17
ChaoticGood and I have a similar problem, but my installation doesn't freeze - it just fails (says files could not be loaded from the CD) and quits to the install menu.

I burned the CD on the same computer as I'm installing it on, currently on XP SP2.

---

### Post by taurus on 2005-11-17
Try to burn it at a slower speed like 4X...

---

### Post by alfrjw on 2005-11-17
I encountered the same problem, so did a few tests using:

ShipIt 5.04 Live CD x86
ShipIt 5.04 Install CD x86
ShipIt 5.10 Live CD x86
ShipIt 5.10 Install CD x86
ShipIt 5.10 Live cd 64-bit
ShipIt 5.10 Install CD 64-bit

Always with the same result:
I choose language and keyboard, the system looks for the CDROM, finds it, loads some files and then claims one is failing MD5.

I suppose there is "something" in a driver used by the cds..

On the same machine,SUSE10.0 installed without a hitch from the same drive, and windows does the same.

hardware specs:
Mainboard: Asus P5LD2-VM (intel 945G chipset), Pentium D 820 , Hard disk on ide master and DVD-R (benq dw1640) on slave.

---

### Post by Othersider on 2005-11-17
[QUOTE=taurus]Try to burn it at a slower speed like 4X...[/QUOTE]

Same problem, this time it's /Packages that fails the MD5 check (that has been a problem in the past, too).  Though usually it's initrd.gz.

Any other ideas :(?  My problem seems identical to alfrjw's, though I'm still waiting on the ShipIt CDs.  I don't think it's the CD integrity, though, because the md5's *do* match.

---

### Post by gsus777 on 2005-11-20
[COLOR="DarkOrange"]
I had the same issue and solved it by using "expert" mode and when getting prompted for hdparm entering "-d 1 /dev/hda1". This turns DMA on. In some dvd drives this is required to work with the linux driver. Benq and Plextor are affected, others I don't know.[/COLOR]

---

### Post by Othersider on 2005-11-22
Thanks, gsus's solution worked great :).

---

### Post by ninotob on 2005-11-22
[QUOTE=gsus777][COLOR="DarkOrange"]
I had the same issue and solved it by using "expert" mode and when getting prompted for hdparm entering "-d 1 /dev/hda1". This turns DMA on. In some dvd drives this is required to work with the linux driver. Benq and Plextor are affected, others I don't know.[/COLOR][/QUOTE]

I didn't see a prompt for putting in hdparm info -- where do I do this in the install process?

---

### Post by Othersider on 2005-11-22
You need to be in 'expert' mode.  Type 'expert' at the prompt when you boot from the CD.  The dialog asking you for hd params will pop up after you load files from the CD, I think.

---

### Post by ninotob on 2005-11-22
[QUOTE=Othersider]You need to be in 'expert' mode.  Type 'expert' at the prompt when you boot from the CD.  The dialog asking you for hd params will pop up after you load files from the CD, I think.[/QUOTE]

Well, there isn't anything obvious for this.  I took a look at the additional options bit for the modules that are loaded and gave it a shot for the isofs module -- it just failed and didn't even give me a chance to fool around with it.  I did use expert mode, I also tried "expert -d 1 /dev/hda1" but that didn't chance anything.  I tried replacing hda1 with hdc1.  Let's see, I also changed my bios for the cd to be udma 1 instead of auto.  That didn't have an effect.

I remember some issue w/ dma with suse 9.somethingorother some time ago, but I haven't had to mess around with it in a long time.  I feel like I suddenly became a newb again.

I think I'll look into netinstall -- that always worked great for ubuntu on my macs -- grrrr ... there's no openfirmware in a PC so that means I have to learn something else ... I guess I'm just going to install Hoary.  It installs without any problem at all -- why fiddle with an installer that works great?  I wonder if I can start with Hoary's installer and then swap discs.  Probably a bad idea but what the heck.

EDIT:  can't swap discs.

---

