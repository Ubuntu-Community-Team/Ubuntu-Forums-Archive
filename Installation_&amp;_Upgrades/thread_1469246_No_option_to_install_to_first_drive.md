---
title: "No option to install to first drive"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by tlongren on 2010-05-02
Hi!

Upgraded one box that has 2 drives in it to 10.04 no problem.

Tried doing my other box today, and it won't give me the option to format the /dev/sda drive (first drive), only gives me /dev/sdb as an option.

/dev/sdb is my media drive. /dev/sda is where the previous version of Ubuntu was installed and I need to be able to install to that drive.

When I boot the live cd instead of installing, I see both drives under the "Places" menu, so I know ubuntu sees both drives.

Can anyone help?

---

### Post by tlongren on 2010-05-02
Anyone know why this happens?

---

### Post by tlongren on 2010-05-02
See the attached screenshot to see what I'm talking about.

---

### Post by gregmo on 2010-05-03
I'm having the same problem.  /dev/sda is not showing as an install option.  I have two other disks and they are showing.  Also, the install doesn't think I have any other OS's and I have both XP and Vista on other partitions.

I remember this happening before with a previous version and I just don't remember the solution.

---

### Post by gregmo on 2010-05-03
Ah ha!  It took me a few minutes, but I remembered!

Boot into the live CD and open a terminal window.
Do 'sudo apt-get remove dmraid'.
When you run the install program, /dev/sda will show up.

Hopefully that will work for you (it did for me)!

---

### Post by tlongren on 2010-05-04
gregmo, thanks for the reply! I will give this a try when I get home today and will report back with my findings.

Desperately need to do a fresh install on that box. I have had to do upgrades the last two releases and the box is getting sluggish.

---

### Post by tlongren on 2010-05-05
gregmo, that worked. Thanks so much for posting. Thanks even more for remembering how to fix it! :)

---

