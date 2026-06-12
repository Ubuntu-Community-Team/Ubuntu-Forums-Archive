---
title: "Dual Boot with Ubuntu and Windows ME"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by tholman_ut on 2006-07-22
I recently got a used laptop (Sony VAIO 128MB RAM 30GB HD) and it came with WinME already loaded on it.  I put Ubuntu on my old desktop and like using it, so now I want to dual boot on my laptop.  I'm concerned because if I lose Win98 I won't be able to reload because I don't have a WinME disk.  I have +25GB space on my HD.  I'm so sick of my WinME because my laptop always locks up!](*,) 
 
Has anyone dual booted with Ubunto 6.06 and WinME?
Can I load Ubunto without losing my ME? If so how?
How do I partition my HD?:confused:

I'm not that computer savy so any help would be appreciated.:D

Thanx

---

### Post by afbase on 2006-07-22
i wish i could really help, but i can't.  All i can say is that this setup might not be good for ununtu.  Windows ME is notorious for its self suicide/decay of operation ability, and eventually any data that is not backed up is almost certain to be lost! and potentially any data stored on linux could be lost too because of Windows ME.

---

### Post by Herman on 2006-07-22
Hello, tholman_ut,
I don't know much about Windows ME. 
You should be able to use the 'Alternate' Install  CD quite alright, I don't know if you can use the popular new 'Desktop' Live/Install CD with that amount of RAM though. 
My first (left-hand) sig link under this post contians an example of how to use the  'Alternate' CD Installer if you have Windows that has a FAT32 filesystem. 
If you have an NTFS filesystem in Windows, my middle sig link will be more like what you might want to do.

It should be relatively safe, but nothing is 100% guaranteed, we always use partitioners and install software at our own risk. The 'Alternate' Installer and partitioner are about the safest that can be made. It's more challenging for new users because it is text based. You should be okay if you look at my sig links. Thousands have already used it to install dual boots with, using all flavours of Windows. I haven't heard of any particular problems with dual booting Win ME and Ubuntu in over two years of monitoring these forums.
Good Luck with it, Regards, Herman :D

---

### Post by djheadley on 2006-07-22
I've been dual booting Ubuntu and WinME for about a year now and haven't had any problems with either.  I did make all of my data partitions Fat32 so I could use them from both OS.  In fact, I just moved all my drives to a newer machine and all that happened was the usual hardware detection and/or reconfigure.  Until I can get rid of Windows, I am happy to do it this way.

---

### Post by bernied on 2006-07-22
Beware that even the alternate install cd will replace your MBR (master boot record) without prompting you first, so that Windows will no longer boot by default. This is no problem if your grub install works fine and gets you access to your windows install. If the grub install doesn't give you access immediately, you'd have to edit the grub configuration manually, which would need some guidance if you've not done it before. So installing ubuntu could be a problem if, say, this was the only machine that gave you internet access and the ubuntu install wasn't successful, so you couldn't get that guidance.

It is possible to get your Windows MBR back (in case the linux install proved impossible and you wanted to restore the Windows setup), even without a Windows CD. My favorite tool for this is the FreeDOS live-CD - just type fixmbr and all is back to normal (for Windows). Of course, you won't be able to boot (or even see) your Linux install from Windows.

Not trying to panic you here, just suggesting that you need to be prepared for things not going totally smoothly. Anything can be fixed, and I'm sure that your dual boot is possible (if you have enough disk space and you can boot to cd), but if you lose all access to the internet it can be difficult to fix anything.

---

### Post by tholman_ut on 2006-07-22
Thanx for the feedback guys I'm going to go ahead and load the dual boot.

I was also wondering if I will have any problems with my Motorola wireless card (PCMCIA)?
The card is a Motorola WN825GP wireless card with the BCM4306/BCM22050000 chip set.

If so is the driver already imbedded in the OS or is it an extra download?

---

### Post by Herman on 2006-07-22
[IMG]http://users.bigpond.net.au/hermanzone/p2d/21fat32.png[/IMG]
You will be warned first, and the 'Alternate' install CD also offers you the most alternatives as well. Click [Here]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") and [Here]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_Go_Back__to_Install_LILO_Boot_Loader") to see.

bernied is correct though, the occasional failure or misconfigured installation of the GRUB bootloader can be upsetting to some new users.
That's the reason why I  recommend GAG Boot Manager. It's free and only a small download, is graphical and easy to use and will boot Windows for you in an emergancy without any trouble. [Click Here]("http://users.bigpond.net.au/hermanzone/p12.htm") for how to download and use GAG Boot Manager
There are plenty of people here on Ubuntu Web Forums waiting to help you if you have trouble with GRUB.

About wireless cards, I don't know much about those, but I think you will probably need to install a driver for it seperately, there should be information about that in the Official Ubuntu Wiki.
Good Luck, Regards, Herman :D

---

### Post by bernied on 2006-07-22
Hmmmm, I must have had some kind of reverse hallucination - quite possible. I was looking out for that particular screen and didn't see it, then got my mbr toasted and had all kinds of stress fixing it. I used the kubuntu 6.06 alternate install cd.

---

### Post by Herman on 2006-07-22
No Probs, :D
Hey, here's a link for how to back up and restore your bootloader part of your MBR for next time, using the Ubuntu Dapper 'Desktop' Live/Install CD (or any Live CD). If you want to see that, [*Click Here.*]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

When people say their 'MBR is Hosed', sometimes there really are problems that even a real computer expert would work hard to solve, but that would be quite rare. Most of the time, it's just because people need some help with getting Grub set up properly. Grub can do almost anything in the hands of an experienced user or an inexperienced user following the right instructions. The biggest problem with Grub is getting people to understand hopw ot use it. The [Grub manual]("http://www.gnu.org/software/grub/manual/grub.html") already contains all the information, but many people find it 'dry' reading. (Dull and boring) Illustrations can help, [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm") for a Grub Page with some illustrations, and try out some tricks with Grub.
Regards, Herman :D

---

### Post by tholman_ut on 2006-07-23
Just to let everone who helped me know, or to let anyone who reads this that is doing the same thing, the install went smooth as could be.  The only problem that I am having si with my wireless card see my other post for a description (and hopefully I'll post my solution in a day or two): [http://www.ubuntuforums.org/showthread.php?t=221737](http://www.ubuntuforums.org/showthread.php?t=221737)
:???:

---

