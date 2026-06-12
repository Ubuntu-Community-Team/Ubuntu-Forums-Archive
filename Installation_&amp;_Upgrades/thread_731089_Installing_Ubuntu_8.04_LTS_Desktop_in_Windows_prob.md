---
title: "Installing Ubuntu 8.04 LTS Desktop in Windows problems"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Knight319 on 2008-03-21
Recently, I downloaded Ubuntu 8.04 LTS Desktop beta. I successfully downloaded the .iso and burned it to a CD-R. I checked the disc for errors as well, and it did not find any. Now, I have attempted to install Ubuntu inside Windows (Via the menu that pops up when you insert the disc in Windows and choosing the second choice). Each time it gets to 100% with creating the image, a window pops up saying "Could not access the CD, please make sure other applications are not using it and try again." I have tried again, and got the same error, and I'm 100% sure nothing is using the CD drive. I also tried on a spare computer and yet got the same error again. Any help?

Specs:
Dell Dimension E521
AMD Athlon X2 5200+ 2.6ghz
2gb DDR2 RAM PC2-5300
Hitachi DeskStar 80gb HDD
Sony CDRWDVD CRX310S
Windows Vista Home Premium 32-bit

---

### Post by Pumalite on 2008-03-21
Maybe this will help:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Knight319 on 2008-03-21
Thanks for the reply, but that wasnt.. exactly what I was looking for. It would help me out if I was partitioning though.

Ubuntu 8.04 Hardy Heron apparently includes something called "Wubi" which allows you to install Ubuntu INSIDE of Windows, and will let you uninstall it THROUGH Windows via Add/Remove Programs.. In theory, it's a program. Many people have said they have got this to work successfully, but I don't know why I'm getting that error. I would prefer to do this instead of partitioning my hard drive just because I would like to test it before fully installing it, and I don't want to really use the Live CD because then I'm missing out on some features.

---

### Post by hsjC on 2008-03-22
I'm testing out Hardy also!

"The kernel in this beta is unable to access CD-ROM devices in some configurations..." 

It's one of the caveats maybe.

---

### Post by forestpixie on 2008-03-22
It is indeed - [https://wiki.ubuntu.com/HardyHeron/Beta#head-2aeb09ed1ccc470c1f83b77fe62a06c43280dd68](https://wiki.ubuntu.com/HardyHeron/Beta#head-2aeb09ed1ccc470c1f83b77fe62a06c43280dd68)

> The kernel in this beta is unable to access CD-ROM devices in some configurations, which may prevent users who were previously able to install Ubuntu from installing this beta from CD media. [COLOR="Red"]As a workaround, users can boot the installer with the additional "all_generic_ide" boot option or switch the device from Master to Slave with jumpers.[/COLOR] [WWW] [https://launchpad.net/bugs/181561](https://launchpad.net/bugs/181561)

---

### Post by h-bar on 2008-03-22
> Each time it gets to 100% with creating the image, a window pops up saying "Could not access the CD, please make sure other applications are not using it and try again."

I get this exact same error.  I tried the wubi installation after [the liveCD installer failed]("http://ubuntuforums.org/showthread.php?t=190683&page=4").  I ran the diskcheck routine and had no problems.  Note: I also get the liveCD install fail with Gutsy.

---

### Post by boron on 2008-03-22
Hi, I'm ultra new to Linux, but have been impressed with the speed of it, compared with Windows on line, even when using a Live CD.  Having been a long time user of Windows, It would be pretty major for me to abandon it completely and overwrite my hard disk by Installing Ubuntu, but I found at [http://www.ubuntu.com/testing/hardy/alpha6](http://www.ubuntu.com/testing/hardy/alpha6) what seemed to me to be an excellent alternative.  The possibility of installing Unbuntu as A windows Application:)
Unfortunately, having burned a DVDrom [because I had one to hand, but not a CD], I cannot see the option to do this in the menu that eventually comes up.
At the link  [http://www.ubuntu.com/testing/hardy/alpha6](http://www.ubuntu.com/testing/hardy/alpha6) the option to install as windows application appears under CD Menu, I think. Is this different from the menu that os presented when Hardy Herom has loaded?  And, if so, how do I get to it, please?
Sorry for errors in above, I'm not used to forums, either.
Thanks for helpful advice soon to be received.
:)

---

### Post by Kiri on 2008-03-22
I have the same problem...

> The kernel in this beta is unable to access CD-ROM devices in some configurations, which may prevent users who were previously able to install Ubuntu from installing this beta from CD media. As a workaround, users can boot the installer with the additional "all_generic_ide" boot option

How can I boot the installer with this option?
Can I also do this to install the wubi?

---

### Post by Pumalite on 2008-03-22
F6 for new menu
'e' to edit
add 'all_generic_ide' at the end of the boot line
Then 'b' to boot

---

### Post by Kiri on 2008-03-22
> **boron said:**
> 
At the link  [http://www.ubuntu.com/testing/hardy/alpha6](http://www.ubuntu.com/testing/hardy/alpha6) the option to install as windows application appears under CD Menu, I think. Is this different from the menu that os presented when Hardy Herom has loaded?  And, if so, how do I get to it, please?


boron, you should download the more recent beta from [http://www.ubuntu.com/testing/hardy/beta]("http://www.ubuntu.com/testing/hardy/beta")

When you run the cd in windows it should give you the option to install in windows (2nd option from the top)

---

### Post by Kiri on 2008-03-22
> **Pumalite said:**
> F6 for new menu
'e' to edit
add 'all_generic_ide' at the end of the boot line
Then 'b' to boot

Pumalite, thank you. This will not be possible for installing the wubi in windows will it?

---

### Post by SHaFT7 on 2008-03-22
I had an issue installing ubuntu 8.04 beta via wubi until i passed it through zone alarm.  Once I did that, it started installing just fine without crashing.

---

