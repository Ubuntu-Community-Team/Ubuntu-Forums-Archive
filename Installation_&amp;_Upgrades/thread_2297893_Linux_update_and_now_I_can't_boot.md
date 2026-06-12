---
title: "Linux update and now I can't boot"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by sccjono on 2015-10-07
Hello all, firstly can I apologise because I am relatively ignorant of the inner workings of Linux and so may well say something stupid.

I am using Ubuntu 15.04 and all has been well until today when an update to what I assume is the Linux kernel was installed and my system now freezes at the unity login prompt. The new files were numbered something like 3.19.0.31-35 and I'm sure they were replacing those numbered 3.19.0.31-34 and were "generic" and "headers" etc. Does that make any sense? I have seen these kind of updates quite regularly and they have never caused a problem before but as I say re-booting afterwards causes a freeze that means I have to turn my laptop off.

I am logged in now as I am able to choose what I assume is an older kernel of 3.19.0-30 from the advanced grub menu which seems to work ok.

Has anyone got any advice?


Regards,
jono

---

### Post by dino99 on 2015-10-07
a kernel image/header can be corrupted (in that case, purge the 4 related files, update the archive, and reinstall it) (of course always use the genuine ones)
[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

Sometimes it can be an ABI/driver issue; so use the previous kernel until a fixed one is rebuilt

---

### Post by pauljw on 2015-10-07
Looks like the fix has been committed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

---

### Post by christian-bobach on 2015-10-07
I had exact same issue

---

### Post by sccjono on 2015-10-07
Thank you guys, I'm not entirely sure I understand what I'm reading in the links that you've provided. Are we saying to continue to boot from the previous kernel and wait for another update to replace the broken one?

If that is the case, is there any problem in running the 'sudo apt-get dist-upgrade' command when you are not running the latest kernel on your machine?

Thanks again,
jono

---

### Post by sccjono on 2015-10-08
OK I have just received the files in an update for 3.19.0-31.36 and I can now log in OK. I still get error messages but I can put up with those. Thanks for your assistance guys.

jono

---

