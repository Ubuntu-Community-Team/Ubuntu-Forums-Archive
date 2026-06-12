---
title: "[SOLVED] Correct md5sum but corupt packages on the CD?"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by cferthorney on 2008-04-04
I hope I have posted this in the right section - I did a search and found nothing that seemed to help.

I am trying to install Ubuntu through the alternative CD as I wish to encrypt the hard drive and I also wish to use LVM.  I downloaded the CD from my local mirror (The UK Virgin Media one) and md5sum'd it as normal.

The md5sum was fine so I proceeded with an install.

However I am a paranoid soul, and selected "Check CD for defects" there were several mismatches including (worryingly) all the kernel.deb's, bash and apt.  Has anyone else come across this?  I tried to download the CD off 2 other mirrors (One Czech based and one German based) and a similar thing happened (Although the corrupt packages were different)

I don't think its safe to use this CD - but if every CD I try is slightly corrupt getting Ubuntu on my machine won't happen.

Thoughts and suggestions greatly appreciated.

---

### Post by stefangr1 on 2008-04-04
Yes, that happens. Checking the downloaded iso only determines if it has been downloaded correctly or not. Yours is ok, so you don't have to download it again. I think in your case it went wrong when burning the cd (you did burn it as iso?). Just burn cd's over and over untill the cd check says it's ok.

---

### Post by cferthorney on 2008-04-04
> **stefangr1 said:**
> Yes, that happens. Checking the downloaded iso only determines if it has been downloaded correctly or not. Yours is ok, so you don't have to download it again. I think in your case it went wrong when burning the cd (you did burn it as iso?). Just burn cd's over and over untill the cd check says it's ok.

Yes I burned them using Nero on my works laptop.  I have several linux boxes at home (Mostly running CentOS or Gentoo) Could I mount the ISO on loopback and then check the md5sums of the apps so I can confirm the ISO contents is OK?  I would rather not make too many coasters.

Also do you happen to know where I can find a copy of the main public key used to sign the apps so I can check the MD5SUMs.gpg in future?

Cheers :)

---

### Post by /etc/init.d/ on 2008-04-04
If the md5sum of the download matches okay, the problem is with the burned CD.  Try burning at a slower write speed, try using different  burning software (k3b, Gnomebaker, Brasero, to name but a few), and try a different brand of media.  If there are still problems, you have a defective burner or a hardware problem.

You can mount the ISO as a loopback and check the MD5 sum of each file, but there is no need if the MD5 of the single ISO checks out.

The MD5SUMS.gpg file is signed by key FBB75451 2004-12-30 Ubuntu CD Image Automatic Signing Key, see the link below for a message from Colin Watson confirming the key:

[https://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003500.html](https://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003500.html)

---

### Post by stefangr1 on 2008-04-04
If you already have linux, I think your burner application might have an option that checks the cd (I know k3b has one for sure) after it has been burned. The md5sums are also in the mirrors that provide the images, see for example the one of Universiteit Twente:

[http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/gutsy/](http://ftp.snt.utwente.nl/pub/linux/ubuntu-releases/gutsy/)

---

### Post by cferthorney on 2008-04-04
Thanks guys,

Burning it on a different machine solved the problem.

---

