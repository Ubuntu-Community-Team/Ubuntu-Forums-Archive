---
title: "Unable to boot into windows"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by prasenjit007 on 2010-09-17
Hi Everyone...

First of all i know am not supposed to post threads about other linux os..but since mint linux is based on ubuntu am askin this question...

I first installed mint linux 9...then installed windows xp ( I know windows should always be installed first..bt i had to do that in this order). Anyways after i installed windows i rebooted my system. So now i can no longer boot into mint linux. so i inserted mint linux live cd..opened the terminal and typed in the following..

1.```
sudo fdisk -l
```
-----> I came to knew that mint linux is installed in /dev/sda1. and windows xp is in /dev/sda2.

2.```
sudo mount /dev/sda1 /mnt
    sudo grub-install --root-directory=/mnt/ /dev/sda
```

---->I got the following output:

grub-probe: error: cannot find a device for /boot (is /dev mounted?).
Installation finished. No error reported.

Now the problem is i can boot into mint linux without any problem but i can't boot in windows..
plz help me..i need windows n linux both..how can i fix this?

Any help would be appreciated..
Thanks in advance..

---

### Post by drs305 on 2010-09-17
First, if you don't have Windows in the Grub menu, run:
```
sudo update-grub
```

If you do, but it won't boot from the Grub menu, normally following the steps in this guide gets Windows booting again along with retaining Grub:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by prasenjit007 on 2010-09-17
using live cd or from within mint linux?

---

### Post by drs305 on 2010-09-17
> **prasenjit007 said:**
> using live cd or from within mint linux?

To update Grub2, you would run that command after your normal boot as long as mint is booting correctly.

---

### Post by prasenjit007 on 2010-09-17
> **drs305 said:**
> To update Grub2, you would run that command after your normal boot as long as mint is booting correctly.

Thanks a lot drs305.
It worked successfully. I must say today I learned something.
Thanks once again..:)

---

### Post by drs305 on 2010-09-17
Only been on the forum a few weeks and already have figured out the command line and "SOLVED"! Looks like you are off to a great start.

Happy Ubuntu-ing (even if it's Mint).  :guitar:

---

