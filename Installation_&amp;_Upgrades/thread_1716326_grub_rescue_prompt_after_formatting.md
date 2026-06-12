---
title: "grub rescue prompt after formatting"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by vramya on 2011-03-28
hello,

i have a dual booting the first one being ubuntu 10.04 within which i have installed windows7.Unfortunately,i've formatted that part of my hard disk in which i've had ubuntu.
Now my problem is i cant load into any of the two os and i dont want to loose my vital data in the system.I've tried booting using the live CD but in vain.i desperately need my info in my laptop.could anybody help me out....:confused:

---

### Post by drs305 on 2011-03-28
> **vramya said:**
> hello,

i have a dual booting the first one being ubuntu 10.04 within which i have installed windows7.Unfortunately,i've formatted that part of my hard disk in which i've had ubuntu.
Now my problem is i cant load into any of the two os and i dont want to loose my vital data in the system.I've tried booting using the live CD but in vain.i desperately need my info in my laptop.could anybody help me out....:confused:

vramya,

Welcome to the Ubuntu Forums!

Please go to the following site and download the boot info script. From the LiveCD, run the script and post the contents of the RESULTS.txt file it generates. This information will give us the boot details we need to help solve your problem.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by vramya on 2011-03-28
am not even able to boot using the live cd as well...tried booting using a pendrive but no result...all i get is a grub rescue prompt which says unknown command even for sudo...

---

### Post by drs305 on 2011-03-28
> **vramya said:**
> am not even able to boot using the live cd as well...tried booting using a pendrive but no result...all i get is a grub rescue prompt which says unknown command even for sudo...

Presence of the grub rescue prompt indicates the system is still trying to boot from the hard drive.

There can be a few reasons for not being able to boot the CD. The first is that the CD drive is not listed first in your BIOS setting. You enter BIOS during boot up by pressing a key - often one of the Fn keys, the ESC or DEL key. It varies by manufacturer. Do you hear the CD spinning as the system powers up?

If the CD is listed first, it's possible the CD is corrupt and BIOS is moving on to the next option. Does the CD work in another computer? Does another CD work in the problem computer?

Here is a link to resolving problems from the Grub rescue prompt. It's a lot easier fixing things from the LiveCD, but if needed you can refer to this guide:
[Grub Rescue Prompt Megathread ]("http://ubuntuforums.org/showthread.php?t=1594052")

---

