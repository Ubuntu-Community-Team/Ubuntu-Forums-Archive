---
title: "CD Boot Record not found?"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by sfabel on 2005-04-14
Okay, call me stupid. How do I burn a installation CD-ROM under Linux (K3B)? I've downloaded the installation CD ISO image for Hoary and burned the thing under K3B with the option "Tools - CD - burn Cd image".

When I put in the CD, it shows up as "Ubuntu 5.04 i386" and has the filesystem on it.

The BIOS is set up to boot from CD-ROM. I put in the disc, and restart. It displays "Searching for Boot Record on CD-ROM...", then after a little while: "...NOT FOUND!" and I am stuck in my SuSE GRUB. :-x 

So what am I missing. Do I need to activate some option in K3B or do I need to fiddle around with trying to copy a boot record on the CD-ROM first? This is frustrating. The PC boots from another CD-ROM containing a boot record, by the way.

So the only thing I figure is that I am too stupid to burn an Installation CD. ARGL!

Thanks for your help,
Stephan

---

### Post by heimo on 2005-04-14
What I did to successfully burn Hoary CD is right click on the iso file in nautilus (file browser), click *write CD / burn CD *or what-ever the text is. No options given. However, to me it sounds like you already burnt that CD correctly (not showing ISO file on it, but the actual files). Could be though that it wasn't made bootable.
 
Make sure your CD-ROM drive is correctly found by BIOS and that it's set to ... hmm... it's probably not that. Your computer is trying to boot from that CD-ROM, right? Set in the boot order - BIOS settings?

---

### Post by sfabel on 2005-04-14
[QUOTE=heimo]What I did to successfully burn Hoary CD is right click on the iso file in nautilus (file browser), click *write CD / burn CD *or what-ever the text is. No options given. However, to me it sounds like you already burnt that CD correctly (not showing ISO file on it, but the actual files). Could be though that it wasn't made bootable.
 
Make sure your CD-ROM drive is correctly found by BIOS and that it's set to ... hmm... it's probably not that. Your computer is trying to boot from that CD-ROM, right? Set in the boot order - BIOS settings?[/QUOTE]
 Okay, I burned the way you described (right-click in nautilus). I get the same results.

Is there an error with the ISO images??

---

### Post by sfabel on 2005-04-14
Funny, the image size that I have is 586 mega-bytes (I downloaded from the European mirror).

I looked around and right now I am downloaded the image that is 600.1 megabytes in size (from the American mirror).

I'll try that one as well...

Stephan

---

### Post by heimo on 2005-04-14
Hmm.. haven't heard that there would be common problems of this sort. But you could check that your iso file is not corrupted by running *md5sum [isofilename] *and comparing it to the corresponding value on the MD5SUMS list from:
[http://us.releases.ubuntu.com/releases/5.04/MD5SUMS]("http://us.releases.ubuntu.com/releases/5.04/MD5SUMS")
 
 
EDIT: You posted while I was typing. Yeah, that would probably be it... :)

---

### Post by sfabel on 2005-04-15
[QUOTE=heimo]Hmm.. haven't heard that there would be common problems of this sort. But you could check that your iso file is not corrupted by running *md5sum [isofilename] *and comparing it to the corresponding value on the MD5SUMS list from:
[http://us.releases.ubuntu.com/releases/5.04/MD5SUMS]("http://us.releases.ubuntu.com/releases/5.04/MD5SUMS")
 
 
EDIT: You posted while I was typing. Yeah, that would probably be it... :)[/QUOTE]
 Guess what... I have a correct ISO image. Why the hell is my PC not able to boot THAT whereas it boots other CD-ROMs?

Stephan

---

