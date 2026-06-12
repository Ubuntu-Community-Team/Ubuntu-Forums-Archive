---
title: "Problem with USB install of Ubuntu netbook"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by whatthefunk on 2010-12-08
Hi all,
I'm trying to install Ubuntu Netbook on an older Sony Vaio laptop. I've prepared a USB drive with the Ubuntu files on it as directed by the instructions. At startup, I go to alter the BIOS and I move "removable media" up to the top but it still wont boot from the USB. 
What should I do now? Ive tried to install a couple different boot managers, but my DOS skills are rather sucky and I havent managed to accomplish anything. 
Any help would be appreciated.
whatthefunk

---

### Post by C.S.Cameron on 2010-12-08
What are the specs on your laptop? does it have at least 500MB RAM?
If you can run Bootscript and post the results it would be a big help:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sikander3786 on 2010-12-09
> I've prepared a USB drive with the Ubuntu files on it as directed by the instructions

I hope you did that properly and just not copied the ISO to your USB drive?

You can use unetbootin to create a new disk.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

And it would also be worth checking the image for defects before burning.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

PS: Under some system Bios, USB drives tend to appear under the HDD menu instead. Check it and if it is found there, bring it to the top of that list.

---

### Post by whatthefunk on 2010-12-09
> I hope you did that properly and just not copied the ISO to your USB drive?

 
Yes.  I unetbootin and a couple other similar programs to load the ISO onto my USB.  It didnt work.  I did the MD5sum on the files and they all checked out.
 
> What are the specs on your laptop? does it have at least 500MB RAM?

 
Pentium III processor, 256MB RAM, 15 GB harddrive.
 
It is a little under the system recommendations, but it runs Win XP with little trouble.
 
So, a bit of an update.  I gave up completely on the USB method and dug out an old external CD drive to try to do it that way.  I first tried with the standard Ubuntu Live CD, but it froze up and the CD stopped spinning.  Thinking that my little laptop may not be able to handle Ubuntu, I tried Xubuntu and got slightly further along, but it frooze up after I selected the language.  I then tried Kubuntu and had the same problem.  Then I figured that maybe it was the graphic heavy installation program and downloaded the Kubuntu Alternate Cd file.  At around 2 am last night, in the first steps of installation, it couldn't find a couple dozen files and I gave up for the night.  This morning I went out and bought some new CD-RWs and am trying again.  
 
So far all that Linux has proven to be a royal pain in the ***....

---

### Post by sikander3786 on 2010-12-09
Rather than Ubuntu, Kubuntu or Xubuntu, I would suggest Lubuntu after seeing your system specs.

[http://lubuntu.org](http://lubuntu.org)

---

### Post by whatthefunk on 2010-12-09
> **sikander3786 said:**
> Rather than Ubuntu, Kubuntu or Xubuntu, I would suggest Lubuntu after seeing your system specs.
 
[http://lubuntu.org](http://lubuntu.org)
 
Hmmm....interesting.  Im doing a Alternate CD install of Ubuntu at the moment and (*shock*) its working.  If it runs slow I may try the Lubuntu.  Thanks.

---

