---
title: "Fixparts, how to install, want to fix drive to dual boot Windows7 and Xubuntu"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by Jpendragon on 2012-09-03
Hey, I had another thread about a problem trying to install Windows 7 and Xubuntu alongside each other and the problems I had encountered. They recommended that I use a program called fixparts to fix my drive. (The problem is that xubuntu didn't recognize that the drive had been partitioned.) The problem is, I don't know how to install Fixparts... I've been trying to make sense of the "readme" file, but my juvinile understanding of this sort of thing has become a huge problem.

If someone could tell me exactly what I have to do in as simple of terminology as possible, that would be fantastic.

(Willing to install in either Windows 7 or a live USB version of xubuntu 12.04. Whatever works.)

---

### Post by GreatDanton on 2012-09-03
Why do you want to fix hard drive? Is something wrong with it. If I were you I would boot from Live usb/cd use Gparted and wipe the whole hard disk. Then I would create two partitions one for Windows and another for Xubuntu (and another one for swap). Remember not to format Windows partition. Just leave partition empty and Windows installer will take care of it. After Windows installation you can install Xubuntu.

I hope this helps.

Regards.

---

### Post by Jpendragon on 2012-09-03
> **GreatDanton said:**
> Why do you want to fix hard drive? Is something wrong with it. If I were you I would boot from Live usb/cd use Gparted and wipe the whole hard disk. Then I would create two partitions one for Windows and another for Xubuntu (and another one for swap). Remember not to format Windows partition. Just leave partition empty and Windows installer will take care of it. After Windows installation you can install Xubuntu.

I hope this helps.

Regards.

Yeah there is something wrong, I'll copy paste.

"OK, we got it. The results of fdisk -lu helped.

Anyway, you have a left over gpt backup table. It seems this disk was  used with gpt partition table and then you converted it to msdos with  windows. But windows doesn't delete the backup gpt table which linux can  detect and it gets confused whether the disk is msdos or gpt. Use  fixparts to remove the backup gpt table and you're OK.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)"

---

### Post by ajgreeny on 2012-09-03
I think (of course I could be wrong) that you can do more or less the same thing using gparted, either from the Xubuntu live CD or from any other of the *ubuntu family CDs.

Go to **Device ->Create partition table** and choose msdos which is the default.  That will leave you with a clean disk of unallocated space which you can use to install whatever you wish.

Apologies in advance if I am wrong, but it will do no harm, and you can then investigate fixparts again if necessary.

---

### Post by Jpendragon on 2012-09-03
Actually I riddled out how to do it myself on Windows.

---

### Post by darkod on 2012-09-03
1. Get the Debian package for fixparts from the link on their homepage according to the version you have, 32bit or 64bit:
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

2. When downloaded, right click on the file and select Install with package manager (or similar text). It will install it.

3. Then just open terminal and run the command stated on their website, like:
sudo fixparts /dev/sda

Usually that's all you need. It will detect your problem and offer to fix it for you (delete the backup gpt table).

You can do all of the above from live mode.

---

