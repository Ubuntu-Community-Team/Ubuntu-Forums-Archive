---
title: "Crazy Ubuntu Install"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by jpg on 2006-03-06
Since I seem to be having no luck working with the Ubuntu installer on my damaged machine, I am going to try to install by hand, using the InstallFromKnoppix page as a guide:
[https://wiki.ubuntu.com/Installation/FromKnoppix](https://wiki.ubuntu.com/Installation/FromKnoppix)

I am going to use the UbuntuLive system instead of Knoppix (the logic being that it is more similar to the final install that I want, and the network works like a charm). I might not get around to if for a couple of days, because I have some urgent work issues to take care of first. However, if anyone has done this, and can offer some encouragement or tips, that would be greatly appeciated.

And ESPECIALLY if you can think of some reason I should NOT use the UbuntuLive CD and use Knoppix instead, please tell me now and save me some trouble.

I will go ahead and document the process here, when I get around to it, in case someone else wants to try it later.

Cheers!

---

### Post by jpg on 2006-03-10
Ok, so this is not working. I was not really expecting it to work, actually. I got debootstrap with apt-get (after an update), and ran the indicated command (after mounting the partition on /mnt/ubuntu, etc.):

[B]debootstrap='pwd' debootstrap --arch i386 breezy /mnt/ubuntu [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
[/B]
(putting the "breezy" on the end as the instructions indicate does not work).

It starts out Ok, downloading packages and all, but fails with this message:

[B]I: Validating Packages
/usr/lib/debootstrap/functions: line 901: /usr/bin/tr: Input/output error
W: Failure trying to run: chroot /mnt/ubuntu mount -t proc proc /proc[/B]

The log generated on /mnt/ubuntu/debostrap/debootstrap.log has this:

[B]/usr/lib/debootstrap/functions: line 344: /usr/bin/tr: Input/output error
/usr/lib/debootstrap/functions: line 344: /usr/bin/tr: Input/output error
/usr/lib/debootstrap/functions: line 344: /usr/bin/tr: Input/output error
/usr/lib/debootstrap/functions: line 340: /usr/bin/tr: Input/output error
ar: /mnt/ubuntu/: File format not recognized

zcat: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
[/B]

It looks to me like there is some problem with recognizing the disk. Not sure if there is any way around this, though. Suggestions appreciated. I will try just about anything at this point - not much to lose.

---

### Post by az on 2006-03-10
For starters, in what way was the computer damaged?

---

### Post by jpg on 2006-03-10
Thanks for posting!

I wrote a little about my situation and my install attempts here:

[http://ubuntuforums.org/showthread.php?t=105372](http://ubuntuforums.org/showthread.php?t=105372)

In retrospect, the only thing that I really know is broken is the ethernet on the motherboard, but I kind of don't trust it (the motherboard). I have the computer connected through the USB drive. The CD/DVD ended up failing completely, and I have an old CD drive to install from, and that seems to work Ok. Occasionally it hangs at one stage of the install with the fan and the hard drive running full tilt, but it is not clear that that is a motherboard problem.

I tried installing from a USB flash drive:

[http://ubuntuforums.org/showthread.php?t=139983](http://ubuntuforums.org/showthread.php?t=139983)

without much luck.

I have been able to install Fedora Core 3 (and upgrade to Fedora Core 4, which initially would not install, but was upgradeable from FC 3). RedHat does not handle Ethernet on USB as gracefully as Ubuntu.

I suppose I could try installing Warty and upgrading with the Breezy CD. That might work.

---

