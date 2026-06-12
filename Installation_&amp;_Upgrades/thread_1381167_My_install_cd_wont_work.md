---
title: "My install cd wont work"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by mastermael on 2010-01-14
Ok, i made an install cd, it wont work when i try to use it.

I made the install cd on a Mac, And im trying to use it on a windows machine. will this affect it? 

I can open it just fine on the mac but it wont work on the windows machine. 

I want to make it dual-boot.

Any helpful information will be exrtemely useful. 

Is there a way to install just straight from the internet?

---

### Post by tachuela on 2010-01-14
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://mediakey.dk/~cc/ubuntu-netboot-and-netinstall-with-pxe/](http://mediakey.dk/~cc/ubuntu-netboot-and-netinstall-with-pxe/)
[http://www.wrigley.me.uk/wp/2005/01/09/ubuntu-netinstall-without-cdrom/](http://www.wrigley.me.uk/wp/2005/01/09/ubuntu-netinstall-without-cdrom/)
[http://www.rojtberg.net/articles/ubuntu-net-install/](http://www.rojtberg.net/articles/ubuntu-net-install/)

---

### Post by mastermael on 2010-01-14
Thanks, looking into these now.

---

### Post by DestructionsRightHand on 2010-01-14
Did you try the Check Disk option during boot?

---

### Post by lisati on 2010-01-14
> **mastermael said:**
> Ok, i made an install cd, it wont work when i try to use it.

I made the install cd on a Mac, And im trying to use it on a windows machine. will this affect it? 

I can open it just fine on the mac but it wont work on the windows machine. 

It shouldn't make a difference. Having said that, some CD/DVD drives read some disks better than others.
> 
I want to make it dual-boot.

Any helpful information will be exrtemely useful. 

Have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
> 
Is there a way to install just straight from the internet?
"[Wubi]("https://help.ubuntu.com/community/Wubi")" has this as an option, but the way wubi works is a little different to "dual boot". There are other options, one of which is described here: [https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)

---

### Post by mastermael on 2010-01-14
> **DestructionsRightHand said:**
> Did you try the Check Disk option during boot?
Doesnt even boot the cd. I cant get the cd to "read" the file.

*computer to read the file*

---

### Post by mastermael on 2010-01-14
> **lisati said:**
> It shouldn't make a difference. Having said that, some CD/DVD drives read some disks better than others.

Have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

"[Wubi]("https://help.ubuntu.com/community/Wubi")" has this as an option, but the way wubi works is a little different to "dual boot". There are other options, one of which is described here: [https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)
Do you also have a link for "grub"? I'm feeling under the weather righ tnow and will not be back for a few hours.

Thanks all for the links I am looking into them all right now.

---

### Post by lisati on 2010-01-14
Sorry about the delay replying (I was messing round with a PHP script for my server)

For "grub" (used with 9.04 and earlier): [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
For "grub2" (used with 9.10): [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Take care, and here's to a speedy recovery!

---

### Post by mastermael on 2010-01-14
wasnt on myself, i am currently not at the machine that needs it (its at school) but will be working on this tomorrow /monday.

---

### Post by spcwingo on 2010-01-14
> **mastermael said:**
> Doesnt even boot the cd. I cant get the cd to "read" the file.

*computer to read the file*

By the above it sounds like you burned the ISO to the disk as a file, not an image.  If said win computer runs, download Infrarecorder from [[COLOR="Red"]here[/COLOR]]("http://infrarecorder.org/") and try to burn again.  If I am not understanding you correctly, let us know (and disregard the above).  :)

---

### Post by mastermael on 2010-01-16
> **spcwingo said:**
> By the above it sounds like you burned the ISO to the disk as a file, not an image.  If said win computer runs, download Infrarecorder from [[COLOR="Red"]here[/COLOR]]("http://infrarecorder.org/") and try to burn again.  If I am not understanding you correctly, let us know (and disregard the above).  :)
Well, i call it a "file" because i dont know the proper term.

The "iso" is readable, on the mac it works fine. the windows machine does not have a cd-rw drive and so i cannot burn it straight off there, im using an external burner from a mac.

---

### Post by CottonCandy on 2010-01-21
Hi. I found your thread while searching to see if it's possible to boot a pc from a cd burned by a mac because I may attempt that myself. 
I don't know if you've solved the problem you were having but if not & in case you haven't seen it yet, I also found this thread: [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1339214](http://ubuntuforums.org/showthread.php?t=1339214)[/COLOR]. Post #2 & #7 have some good suggestions.

---

### Post by tachuela on 2010-01-21
Don't use a CD-RW; use a CD-R and burn as 'image' at 4x or less.

---

### Post by mastermael on 2010-02-02
I tried burning it 5 times, I just sent away for a free disc. Thanks for all the the anyways, maybe someone else will benefit from it

---

