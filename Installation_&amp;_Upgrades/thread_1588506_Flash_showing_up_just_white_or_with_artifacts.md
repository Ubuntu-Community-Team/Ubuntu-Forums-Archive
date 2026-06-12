---
title: "Flash showing up just white or with artifacts"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by approaching on 2010-10-05
I have had quite a bit of trouble now getting flash to work on only one of my machines, the others work just fine. I have installed the flashplugin-installer, ran the .deb from abobe.com, gotten the whatever.so and put it into my firefox folder, tried disabling compiz and now I'm getting frustrated.

Any help will be greatly appreciated.

---

### Post by lechien73 on 2010-10-05
Are you using Ubuntu 32-bit or 64-bit edition?

You could try the preview version of Flash player - codenamed "Square". Flash has been a lot more stable for me since I installed it.

You can download it here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

But if you have 64-bit edition, then you can install it using the script I linked at this blog post:

[http://blog.mattrudge.net/2010/09/23/new-64-bit-flash-installer-for-ubuntu-10-04-lucid-lynx/](http://blog.mattrudge.net/2010/09/23/new-64-bit-flash-installer-for-ubuntu-10-04-lucid-lynx/)

---

### Post by lovinglinux on 2010-10-05
See the third item on [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

---

### Post by TBABill on 2010-10-05
I would caution against installing even the flash plugin outside the repos unless critical to current performance that cannot be accomplished with software from the repo. Look at all the failed upgrades from 10.04 to 10.10, or 9.10 to 10.04. Any software installed outside the repos can potentially lead to upgrade problems in the future, which for experienced users may not be a big deal but a new user could really struggle or be turned off by Ubuntu, assuming the problem was caused by Ubuntu.

Just my $0.02 from all the recent posts of failed upgrades this year and then finding out the person installed a driver our software externally and then upgraded with failures in the process.

---

### Post by approaching on 2010-10-07
I think that is what happened. I've had this machine for a long time just upgrading it, and I've had flash problems in the past, so my "fixes" have probably interfered with the upgrades. I've gotten a lot of good info here and will try it when I'm at my home machine.

---

### Post by approaching on 2010-10-07
Lovinglinux's link fixed what I needed. I used the first section on that page, and sure enough, I still had lingering bits of conflicting flash plugins. Thank you guys so much, this was making me pull my hair out.

---

### Post by lovinglinux on 2010-10-07
> **approaching said:**
> Lovinglinux's link fixed what I needed. I used the first section on that page, and sure enough, I still had lingering bits of conflicting flash plugins. Thank you guys so much, this was making me pull my hair out.

You are welcome.

---

### Post by approaching on 2010-10-07
and so say we all

---

### Post by lovinglinux on 2010-10-07
> **approaching said:**
> and so say we all

:)  I miss that show so much...

---

