---
title: "Installing 12.04 on Lenovo G780 Laptop error before installation starts"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by mushigoya on 2012-10-25
I'm trying to Install Ubuntu 12.04 64-bit on Lenovo G780 and getting error before installation starts.

I downloaded the file from this page:
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

I verified the md5 checksum, burnt it on a CD.

When I boot from the CD, first I have a message "error: prefix is not set".

Next I get a menu with "Install Ubuntu", "Try Ubuntu", "Check Disc for defects", I choose "Install Ubuntu".

Now I get another error and a call stack, the error is "Error: couldn't read file".

And I photographed the screen, there's a first call stack than after a few seconds the call stack gets longer but you can only see the end as the computer gets stuck and you can't scroll up.

EDIT: Some more info: in BIOS "UEFI Boot" is enabled, and "Intel Virtual Technology" is disabled

First error screen:
[IMG]http://s13.postimage.org/j2sdya0tz/1st_1.jpg[/IMG]

[IMG]http://s11.postimage.org/yzeuhiooj/1st_2.jpg[/IMG]

Second error screen:

[IMG]http://s16.postimage.org/ksanxyssk/2nd_1.jpg[/IMG]

[IMG]http://s18.postimage.org/q7c1cvgrc/2nd_2.jpg[/IMG]

---

### Post by Bashing-om on 2012-10-25
mushigoya; Hi ! Welcome to the forum.

BIOS "UEFI Boot" is enabled, and "Intel Virtual Technology" is disabled

I have no experience with UEFI ..version 12.04 has the capability to cope with it; these links will provide what I can not.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29](https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)

Post back for additional assistance 
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by mushigoya on 2012-10-25
For now it seems disabling UEFI has solved it, It's installing right now

---

### Post by brainsick on 2012-10-25
I'm in the same boat.  Lenovo G780.  UEFI boot enabled.  The Ubuntu CD presents the textual menu, as opposed to the graphical one with the purple background, but selecting any option results in a Kernel panic.  I've tried Ubuntu 12.04.1 and Ubuntu 12.10.

Any suggestions other than disabling UEFI?

---

