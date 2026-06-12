---
title: "Ubuntu 9.10 won't boot after install"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Ricky-Ray on 2010-01-23
New to Ubuntu, I installed 9.10 onto a Dell Latitude D610 laptop.  I partioned the entire hard drive for ubuntu and it installed perfectly fine as far as I can tell.  Once the install was finished it said to eject the disc and reboot.  Once I did that Ubuntu won't start.  I get an error message that say's

error: no such device: cc019bc9-b8d1-472e-9368-bd3c2530b2fc

I even tried booting it in the recovery mode and I get the same error message.  I've never seen this problem before.  I used the same CD and was able to successfully install it onto a Dell Latitude D600 and I was playing with that computer for about a week before I decided to install Ubuntu onto the D610.

I know the D610 laptop works perfectly fine because it was running Window's XP Pro on it perfectly fine and the hard drive is perfectly fine too.

Am I doing something wrong?  Any help is greatly appreciated.  Thanks.

---

### Post by tachuela on 2010-01-23
What you get is an UUID. Boot your Live CD and edit /etc/fstab

---

### Post by Ricky-Ray on 2010-01-25
Not sure I understand.  I'm VERY new to using Ubuntu or even any Linux.  Thanks.

---

### Post by tachuela on 2010-01-25
Take a look at this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by Ricky-Ray on 2010-01-28
Ok. I figured out that there's a line in the startup that I need to delete.  I followed the instructions on that link and it tells me to hit Ctrl X once I've deleted that line to boot.  It does boot but the next time I start the computer up again or restart I run into the same problem.

Does hitting Ctrl X just boot the machine or is it suppose to save the edited commands and then boot or am I suppose to type in a different command to save it first then hit Ctrl X to boot?

---

