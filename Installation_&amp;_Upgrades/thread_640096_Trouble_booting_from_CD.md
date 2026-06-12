---
title: "Trouble booting from CD"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by arloth on 2007-12-13
I have an older Cyrix 3 computer that's been happily running XP for quite some time now, and decided I wanted to switch this computer to Ubuntu or Xubuntu.  However, it either refuses to reformat the hard drive or boot from the cd. 

I grabbed one of the CDs I previously used, which happen to be Xubuntu 7.04.  The installer worked fine until it came time to format the 120GB hard drive, at which point it threw fits and refused to reformat it.  I then tried an Ubuntu Server 7.10 CD, figuring maybe it's not happy with something.  However, the 7.10 cd is even worse, It stops at the isolinux loading message and goes no further.  I then tried with a regular Xubuntu 7.10 (after finding it in my pile) with similiar results.

As it stands now, I found a set of FreeBSD 6.2 cds, that installed and worked, but I am loathe to leave that installed.  It works, but I'd rather spend time using my computer than setting up and maintaining it.  Help!

---

### Post by jken146 on 2007-12-13
Have you tried an alternate CD?  I've found that the graphical installer for Xubuntu hangs on some systems but the text one is fine. (not a lack of ram issue)

---

### Post by arloth on 2007-12-13
Yes, I just tried the 7.10 alternate install cd for Xubuntu, with the same issue of it not getting past the isolinux loading message.  It just stops there. :confused:

---

### Post by jken146 on 2007-12-13
Wish I could help you more.

---

### Post by arloth on 2007-12-14
After installing FreeBSD 6.2, I tried the 7.04 install again, It gave an error about the hard drive but continued on.  I then tried to update it to 7.10 but it crashed halfway through.  On restart, i ran dpkg --configure -a and it seems to have finished the install.  Oddly now when I go to reformat my raid array from ntfs gparted says the raid array I have is -198594033152.00B, with a total size of -512B.  Maybe I'll just have to give up on ubuntu for now and go back to windows ](*,)

oops, looks like i'm not the only one with this issue, [http://ubuntuforums.org/showthread.php?t=447894](http://ubuntuforums.org/showthread.php?t=447894) and others like it. I'll take that issue up over there.

---

### Post by actionjeans on 2007-12-14
Not that this is of any help to you, but I'm also having a similar issue. At this very moment, I am running an upgrade from Feisty to Edgy, and from their I'll be going from Feisty to Gutsy... All because I was unable to get the install CD (either graphical or alternate) from either Feisty, or Gutsy to run. Edgy loads fine.

I do get an error message that is rather cryptic; emasks error on ata01. It displays this all the way down the screen, one error every 30 seconds or so, until it times out. I have tried 3 different cables, tried 3 different CDROM's, I have burnt the media on 3 different burners at varying speeds, and 5 different types of media with the exact same results.

The system is a 5 year old (at least) PIII 1.4Ghz, with a SiS chipset, onboard video. NOTHING bleeding edge. I know this is something to do with the way the new kernel after edge (starting with Feisty, or 7.04) handles IDE drives, but I honestly am wondering how this isn't fixed yet. I had the exact same issues with Feisty. I finally said screw it, and went with Fedora.

I'm back to Ubuntu (Kubuntu actually), but this is really, really frustrating. I can't imagine having to explain to a new user why I should go through this much hassel (I like the distro doesn't really cut it). Fedora's live CD works fine, as does SuSe. Edgy also works, but not Feisty nor Gutsy.

Yikes.

---

### Post by arloth on 2007-12-14
The motherboard I'm using is a DFI CA-64TC, with a bios update I managed to weasel out of them to get the Cyrix chip to work proper. [http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=1151&CATEGORY_TYPE=MB&SITE=NA](http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=1151&CATEGORY_TYPE=MB&SITE=NA)  

It uses the VIA 694T/686B, is the south bridge chip on yours also a VIA?  It seems odd that the newer boot cds would not work on certain hardware.  Possibly an issue with certain chipsets?

---

