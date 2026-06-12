---
title: "After install, Ubuntu wont load up."
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by Snufkin UK on 2007-10-03
Hello everyone. :) I recently download Ubuntu 7.04 iso, and burned it to disc;
booted up the live cd, everything worked fine, and installed it on a seperate partition on my harddrive, Windows XP is installed on the other part.

Get to the bootloader, load Ubuntu. The progress bar comes up, freezes. Hangs for awhile and then gives me a blank screen with:

```
udevd-event[1931]: run-program: '/sbin/modprobe' abnormal exit

/bin/sh: can't acess tty; Job control turned off
(initramfs)

```


Anyone have any ideas, I've searched the problem on the boards, come up with similar things but have seen no fix. As I've never used Linux/Ubuntu I have no idea about this kind of thing, but was pleased with the Live CD, and would like to start using.

Can anything be done?


Thanks much.
Snufkin UK.

---

### Post by Snufkin UK on 2007-10-04
Any ideas? Would love to know, or even if this is lost cause.

Would be amazing to switch from the old Windoze...

Snufkin UK

---

### Post by Mr_JMM on 2007-10-04
Just to rule something out whilst you're waiting for help with this one: After you downloaded the iso file, did you check it for errors?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Snufkin UK on 2007-10-04
Well did check for defects on the CD before installing. So don't think it's to do with that. Thanks anyway.

---

### Post by Caffeine_Junky on 2007-10-04
Hey there :)

Hmmm I am not sure how to help you with that one ..BUT ..I can BUMP you back to the top of the list ;)

Bump!!!

---

### Post by Snufkin UK on 2007-10-04
Found a way that should get around this at: [http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/](http://giggsey.com/2007/08/06/ubuntu-feisty-modprobe-solved/)

I get to the part about: chroot /mnt/ubuntu/ /bin/bash
And I get:

chroot: cannot change root directory to /mnt/ubuntu/: Operation not permitted

Any ideas? :(

---

### Post by pizzutz on 2007-10-04
try 

sudo chroot.......

sudo lets you perform operations not permitted for a normal user

---

### Post by Snufkin UK on 2007-10-04
That worked, thank you much, but even more problems now. :(

After: ‘deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted’
root@ubuntu:/# sudo apt-get update

I get:
E: Type '‘deb' is not known on line 44 in source list /etc/apt/sources.list
root@ubuntu:/# 

Hmm, Sorry to be a bother, but any ideas now?

---

### Post by rsambuca on 2007-10-04
It looks like you have mixed up your repositories.  Why do you have Gutsy repos - I thought you said you downloaded Feisty.  I really think you should make another CD but burn it at a very low rate to avoid single bit errors.

---

### Post by Snufkin UK on 2007-10-04
The website says it's for Fiesty. :S I honestly have only really just picked up Ubuntu. I could give it a try I suppose. But lots of people had the same problem and did that and didn't help. :S

---

