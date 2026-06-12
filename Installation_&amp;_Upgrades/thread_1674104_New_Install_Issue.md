---
title: "New Install Issue"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by Dr_Obbins on 2011-01-23
I downloaded version 10.10 32bit and burned it to a DVD. Placed it into the computer (XP) and ran it in the trail mode. Everything worked well. Next I wanted to do the full install and over-write everything on the HD. The install went well and it prompted me to restart. It went into the boot sequence and ejected the dvd, but it hangs.

The screen is full of messages like:
[1928.973679] end_request: I/O error, dev sr0, sector 53528 

I tried the reinstall from the dvd 3 times and get the same result.

FYI - I already tried this:
> 

[LIST]
[*]**I/O error after CD is ejected at end of install.**  In some cases, ejecting the CD at the end of installation will leave errors on the screen such as:
[/LIST]

end_request: I/O error, dev sr0,  sector 437628these  error messages indicate that the system is still  trying to access some  files on the CD, and are harmless except that  they obscure the message  asking the user to press Enter to reboot.  You  can safely remove the CD  from the tray and press Enter at this point  to reboot to your new Ubuntu  system. ([539027]("https://bugs.launchpad.net/bugs/539027"))

---

### Post by Dr_Obbins on 2011-01-23
Ok I have been trying this install for over a day now and still no luck. 
During startup, it wants to boot from the CD.[INDENT] If there is no CD, then it just sits there waiting. 
 If I put the CD in, it will boot to the CD and then it wants to install. [INDENT]If I install, it goes through the same routine over again. 
If I exit out of the install screen with out doing anything, then the boot completes and everything seems OK. I can use the computer. But then it will not restart with out going through it all again.
[/INDENT][/INDENT]Anyone got any ideas? If not, then the computer is trash.

---

### Post by Dr_Obbins on 2011-01-23
49 views and no replies. Anybody? Is this a bad time / day? 
I trusted this software and its designers and now I am left with a useless computer. :mad:

PLEASE HELP!

---

### Post by presence1960 on 2011-01-23
> **Dr_Obbins said:**
> Ok I have been trying this install for over a day now and still no luck. 
During startup, it wants to boot from the CD.[INDENT] If there is no CD, then it just sits there waiting. 
 If I put the CD in, it will boot to the CD and then it wants to install. [INDENT]If I install, it goes through the same routine over again. 
If I exit out of the install screen with out doing anything, then the boot completes and everything seems OK. I can use the computer. But then it will not restart with out going through it all again.
[/INDENT][/INDENT]Anyone got any ideas? If not, then the computer is trash.

I don't know what is wrong, ***_BUT YOUR COMPUTER IS NOT TRASH. IF YOU DON'T WANT IT I WILL TAKE IT OFF YOUR HANDS_***

Start at the beginning:

1. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning as an image to CD/DVD?

2. Did you burn the image at a slow speed? 4x-8x works great. High speed burning is great for pics, videos and other data, but may leave a small error which will render an image useless.

3.Did you boot the CD/DVD & check disk for defects prior to installing?

---

### Post by Dr_Obbins on 2011-01-23
> **presence1960 said:**
> I don't know what is wrong, ***_BUT YOUR COMPUTER IS NOT TRASH. IF YOU DON'T WANT IT I WILL TAKE IT OFF YOUR HANDS_***

Start at the beginning:

1. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning as an image to CD/DVD?

2. Did you burn the image at a slow speed? 4x-8x works great. High speed burning is great for pics, videos and other data, but may leave a small error which will render an image useless.

3.Did you boot the CD/DVD & check disk for defects prior to installing?

Thanks for the reply!


[LIST=1]
[*]I did not check it prior, but during the install, I pressed Delete  while the keyboard icon was showing and checked it from there. I guess I could re-download and start over.
[*]I do not know what speed it was burned at. Just the default.
[*]I ran the DVD in the trial mode many times to ensure that I wanted to commit. I did not have any error messages and it went smoothly.
[/LIST]
I think it was installed correctly, but it doesn't boot to it. If it boots to the DVD and I cancel out of the setup screen, it defaults back to Ubuntu not windows. 

Old computers are probably not even worth the shipping costs these days. :rolleyes:

---

### Post by Dr_Obbins on 2011-01-24
I downloaded and installed MD5SUM. Then re-downloaded the Ubuntu iso file 4 different times (at 1.5 hours each) and checked it. Each time the result is "MD5 Check Sum is different" Including the 2 previous times that it was downloaded and not checked, that is 6 times downloaded. 

If the definition of stupidity is doing the same thing over and over and expecting a different result. Right now I am feeling pretty stupid. ;)

Is the file on the server corrupted? Is there another place to download it? Is there a different version somewhere else?

---

### Post by kansasnoob on 2011-01-24
Backing up a bit here :)

> I did not check it prior, but during the install, I pressed Delete while the keyboard icon was showing and checked it from there. I guess I could re-download and start over.

So you selected "Check disc for defects", then waited a few minutes, and it showed "No defects found"?

Not sure what's up with the md5sum. You're checking it with Windows via "WinMD5Sum"? And this is the md5sum you're checking it against:

> 59d15a16ce90c8ee97fa7c211b7673a8

Backing up a bit further you do know this is expected behavior:

>     *

      I/O error after CD is ejected at end of install. In some cases, ejecting the CD at the end of installation will leave errors on the screen such as: 

end_request: I/O error, dev sr0, sector 437628

these error messages indicate that the system is still trying to access some files on the CD, and are harmless except that they obscure the message asking the user to press Enter to reboot. You can safely remove the CD from the tray and press Enter at this point to reboot to your new Ubuntu system.

I think so but I'm just checking :)

It sort of sounds to me like only grub is failing to install properly, but I'm not too sure. I assume you're dual-booting with Windows? Or is this an Ubuntu only machine?

Maybe you're downloading and burning the iso on a different Windows machine?

It might or might not be helpful for us to see the output of the Boot Info Script if you'd run it on that machine using the Live CD/DVD:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2011-01-24
I'm about to get swamped here for several hours, maybe, so I wanted others that may stop by to help to know where I was headed ;)

Naturally I'm wanting to "double-check" that the iso/disc is good. IMHO if the disc passes it's own "Check disc for errors" test I tend to think it's OK. Needless to say, I don't trust Windows tools very much.

Anyway, if the iso is at all in doubt, I was going to recommend copying the .iso to the Live Ubuntu's home folder if possible - NOT the contents of the disc, but the actual "unburned", raw .iso - and then using zsync to check the .iso like this.

NOTE: I'm basing this on Dr_Obbins saying, "I downloaded version 10.10 32bit and burned it to a DVD." in the first post!

You can see that I have the 10.10 i386 iso in my home folder:

```
lance@lance-desktop:~$ ls
Backups                                       New Ubiquity.tar.gz
Belt.pdf                                      Pictures
Belt.ps                                       Public
Desktop                                       resolution fix
Documents                                     symlinking
Downloads                                     Templates
examples.desktop                              **[COLOR="Red"]ubuntu-10.10-desktop-i386.iso[/COLOR]**
gcalctool_5.30.0.is.5.28.2-0ubuntu2_i386.deb  Ubuntu One
grub-common_1.99~20101126-1ubuntu3_i386.deb   ubuntu-tweak_0.5.7-1_all.deb
grub-pc_1.99~20101126-1ubuntu3_i386.deb       Videos
Music                                         VirtualBox VMs

```

And I checked the .zsync DL here:

[http://mirror.its.uidaho.edu/pub/ubuntu-releases//10.10/](http://mirror.its.uidaho.edu/pub/ubuntu-releases//10.10/)

It's still active, so you could first install zsync in the Live Ubuntu Desktop:

```
sudo apt-get install zsync
```

Then simply copy-n-paste:

```
zsync http://mirror.its.uidaho.edu/pub/ubuntu-releases//10.10/ubuntu-10.10-desktop-i386.iso.zsync

```

Sample:

```
lance@lance-desktop:~$ zsync http://mirror.its.uidaho.edu/pub/ubuntu-releases//10.10/ubuntu-10.10-desktop-i386.iso.zsync
#################### 100.0% 395.8 kBps DONE     

reading seed file ubuntu-10.10-desktop-i386.iso: ***********************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read ubuntu-10.10-desktop-i386.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 726827008 local, fetched 0

```

You can see it checks the file for completeness including the checksum and, if it were incomplete it would download only the parts needed.

NOTE: If the .iso were saved to a location other than home you'd need to first "cd" to that location.

Then a new disc could be burned using the Live Ubuntu's Brasero :)

If, as hoped, it's simply a grub problem I'd go the purge and reinstall route:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I hope my guessing is helpful to someone.

---

### Post by Dr_Obbins on 2011-01-24
Well this morning I downloaded and installed Fedora and it worked the first time. Besides cosmetics, is there any big differences between Ubuntu and Fedora? Are there advantages in still pursuing  Ubuntu? 

Thanks for the replies.

---

### Post by kansasnoob on 2011-01-24
> **Dr_Obbins said:**
> Well this morning I downloaded and installed Fedora and it worked the first time. Besides cosmetics, is there any big differences between Ubuntu and Fedora? Are there advantages in still pursuing  Ubuntu? 

Thanks for the replies.

Package management is different. Naturally I prefer Ubuntu but I can't say that Fedora is worse than Ubuntu.

Ubuntu is based on Debian, Fedora is based on RedHat. Both are Linux.

You can add BSD and Solaris to the mix :)

Many, many distros to look at:

[http://distrowatch.com/](http://distrowatch.com/)

I really don't care to argue over which is best, it's a matter of choice. There are also many different desktop environments to explore.

I test a lot and I still always end up back on some derivative of Ubuntu because IMHO it stays "cutting edge" but also offers a very decent LTS release which overlaps by a year so you have plenty of time to test the new LTS before giving up the old one :)

---

### Post by kansasnoob on 2011-01-24
BTW Fedora still uses legacy grub whereas Ubuntu uses grub2. I'd almost bet that we could have corrected your boot problem.

I like to multi-boot trying out different distros, currently all either Debian or Ubuntu based, but you'll only know once you try.

Grub2 is NOT problem free yet but someone had to get out front with development and it's usually Ubuntu :D

---

### Post by Dr_Obbins on 2011-01-24
> **kansasnoob said:**
> Package management is different. Naturally I prefer Ubuntu but I can't say that Fedora is worse than Ubuntu.

Ubuntu is based on Debian, Fedora is based on RedHat. Both are Linux.

You can add BSD and Solaris to the mix :)

Many, many distros to look at:

[http://distrowatch.com/](http://distrowatch.com/)

I really don't care to argue over which is best, it's a matter of choice. There are also many different desktop environments to explore.

I test a lot and I still always end up back on some derivative of Ubuntu because IMHO it stays "cutting edge" but also offers a very decent LTS release which overlaps by a year so you have plenty of time to test the new LTS before giving up the old one :) I am new to the whole Linux scene so I will play around with the software that is working. I am also sure you could have worked me through the process, but right now I need to learn more about this whole Linux culture. Once I learn my way around, I am sure to try again.

Thanks,
Dave :)

---

