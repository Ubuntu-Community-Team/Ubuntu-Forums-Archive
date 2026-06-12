---
title: "SQUASHFS Error"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by kjhughes23 on 2008-11-27
I have a HP Pavilion 01110n desktop and when I try to boot a Ubuntu Live CD or a USB it get SQUASHFS ERRORS and I cannot boot Ubunutu. I can boot Puppy Linux off of a USB but my computer will not let me boot Ubuntu. Do I need an alternate CD. 

Also I have tried 8.10 and 8.04LTS with the desktop ISO and I always get an SQUASHF ERROR. Any Ideas??

---

### Post by lemming465 on 2008-11-28
SQUASHFS error sounds like a problem reading the CD.  If you get it with USB too it makes me wonder about your memory.  Try running memtest86+ for 20 minutes or so and see if all of your memory is good.  If you have access to another CD-ROM driver, preferably on another computer, run the self-test and see if the CD validates as OK to install from.

The alternate CD is primarily interesting in scenarios where you have a complex disk layout (RAID & LVM), or you are doing servers, or you are doing off-line upgrades, or there is a hideous video problem you can't manage during the install but can fix afterwards.  I wouldn't expect it to help in your case, as whatever CD-burning issue, or CD-reading issue, or memory issue is contributing to the squashfs errors would probably hit you eventually during either the text-mode install or post-install when you booted.

For most Linux distributions, including both Ubuntu and Fedora, the #1 cause of installation failures is invalid CD media.  You could try burning it at a lower speed.  It's also worth downloading the SHA1SUM file of checksums and verifying that your download was good.  

The #2 cause of installation failures tends to be memory errors, hence the memtest86+ suggestion.

After those two causes it gets a lot more idiosyncratic.

---

### Post by CRIMPS on 2009-02-25
I was receiving a ton of SQUASHFS errors when trying to install as well.  What I found, thanks to this [post]("http://ubuntuforums.org/showthread.php?t=993763&highlight=squashfs+error") is that my CDRom drive didn't recognize CD-R media.  The CD player was quite old, manufactured in 2001.  So, I swapped in a different CD player and I was able to install without issue.  

Hope this helps

Z

---

