---
title: "grub2 and windows 7 problem"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by Morgan86 on 2010-09-23
Hi.
I installed windows 7 then ubuntu 10.04 and I noticed that windows somehow broke grub. To remove any doubt I restore grub2 from live cd and then I made a series of restarts using only ubuntu and everything went smooth. When I decided to open windows the problems restart immediately: in practice ubuntu does not load after grub screen (still black) and I have to try several times until it starts correctly. What do you recommend? I was thinking to try EasyBCD ...
My setup is: windows7 with ssd and ubuntu; hd with windows documents, / home and / swap.

thanks

---

### Post by Herman on 2010-09-24
If I were you I would check Windows for viruses.
Boot sector viruses like to try to install themselves in the MBR and first track of the hard disk because that way they can start up and take control of your security software before it has time to get going, so they can avoid detection and take complete control of your computer. If you hadn't installed GRUB you would never have noticed anything unusual.
I hope I'm wrong, but check and see if you can find out what else might be corrupting your MBR. If it was your antivirus or any legitimate Windows program I would imagine it would at least do a proper job and restore the MBR completely and not just a little bit, and cause your computer to boot only Windows.
You can never trust Windows not to harbour viruses, because new viruses are always written first, and then it takes time for them to be discovered and identified, and finally a cure found, before you will be informed that your computer is infected, and that can take six months or more.
Not all viruses harm your computer in a way that's apparent to the user  and make themselves known, many prefer to lurk in the shadows and  quietly monitor the user's activities, harvesting such things as bank  account details and passwords and so on.

When viruses are able to occupy the 'hidden sectors' of a hard disk, they can re-infect Windows again after a so called 'clean re-install', and that's why some people 'zero' their hard disks before they re-install if they suspect their Windows system might have had a virus.

---

### Post by Herman on 2010-09-24
Normally we can't 'see' what's in the MBR and in the first track of the hard disk.
These are called 'hidden sectors'. GRUB's boot.img occupies part of the MBR and GRUB's core.img fits in about the next 49 sectors of the first track.

If you want to see for sure if your MBR and hidden sectors are being corrupted by some program writing to them without your knowledge or permission, you can use a dd command to make a file containing a hexadecimal copy of the data in those sectors. 

If you do that when GRUB has just been re-installed and again after booting Windows and letting whatever might be corrupting GRUB do it's thing, you can at least confirm or disprove your suspicions about what seems to be happening.

If you run this command when GRUB is newly reinstalled and working well, it will copy the data to a plain text file in hex code, don't worry if it makes any sense to you or not,
```
sudo dd if=/dev/sda bs=512 count=63 | hexdump -C > testfile_1
```Next, after letting Windows 7 or some program in it corrupt GRUB, run the same command again to make a second plain text file,
```
sudo dd if=/dev/sda bs=512 count=63 | hexdump -C > testfile_2
```Now you have two plain text files with hexadecimal representations of your MBR and GRUB's core.img.
You can compare the two files to determine if GRUB is really getting corrupted or not.
```
diff testfile_1 testfile_2
```A useful gui program for comparing files for changes is meld diff viewer, which can be easily installed in Ubuntu from 'Applications', 'Ubuntu Software Center'.

You may need to use a Live CD or boot from another disk such as a USB flash memory stick that contains GRUB to boot your Ubuntu installation the second time, since the MBR and GRUB's core.img will be corrupted. 
It's useful to have an auxilliary Ubuntu installation in a flash memory stick that boots with GRUB2 because it can be used as an additional means of booting your computer's internal operating systems at times like this, and it may be handy for other work as well.
EDIT: Or a grub-mkrescue CD,
```
grub-mkrescue --overlay=/boot/grub GRUB2RESCUE.iso
```

---

### Post by Morgan86 on 2010-09-25
The problem probabily was on the grub2 bug that corrupt MBR all times i switch forum Ubuntu to Windows.
I solve this problem installing BURG, excellent alternative to grub2.
I find this tutorial very helpfull [http://syndofyouths.wordpress.com/2010/04/12/the-boot-loader-problem-in-ubuntu/](http://syndofyouths.wordpress.com/2010/04/12/the-boot-loader-problem-in-ubuntu/)

Official Burg site: [http://www.sourceslist.eu/](http://www.sourceslist.eu/)


Bye!

---

### Post by coffeecat on 2010-09-25
> **Morgan86 said:**
> The problem probabily was on the grub2 bug that corrupt MBR all times i switch forum Ubuntu to Windows.
I solve this problem installing BURG, excellent alternative to grub2.
I find this tutorial very helpfull [http://syndofyouths.wordpress.com/2010/04/12/the-boot-loader-problem-in-ubuntu/](http://syndofyouths.wordpress.com/2010/04/12/the-boot-loader-problem-in-ubuntu/)

Official Burg site: [http://www.sourceslist.eu/](http://www.sourceslist.eu/)


If you are calling this a grub bug on the basis of this Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

... then you are very much mistaken. A bug has been raised because it affects grub2 but it is not a bug in grub. It's the result of some sloppy practices on the part of some Windows software developers. Grub2 is not corrupting the MBR; some Windows software is. And if you read post #144 on that thread you'll see that substituting BURG may give you different problems down the line.

More from the person who posted #144:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

And a useful link which describes this issue and give some fixes:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

You have not solved your problem. You have merely sidestepped it for the time being.

---

### Post by Rubi1200 on 2010-09-25
Excellent stuff here coffeecat; thanks for the links and informative description of the issue.

Personally, I have noticed many problems with users who have the Dell Recovery Partition.

Our friend, oldfred, has also dealt with this quite a lot.

---

### Post by Herman on 2010-09-25
:-k Yes, thanks for those links, coffeecat.

@ Morgan86, if BURG works for you, fine.

I still think you should run some proper tests to try to find out what program is over-writing to your core.img.

If it isn't a program it could be a virus of some kind, and ignoring the problem by installing some other boot loader won't make it go away. Your security may be compromised.

---

