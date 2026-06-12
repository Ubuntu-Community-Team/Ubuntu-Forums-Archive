---
title: "Problem after installing updates in 9.10"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by manicmoddin on 2010-04-07
Hello, My first post on here :)

Anyway...

I use Ubuntu for educational purposes as I want to learn a few things other than the "Windows way".

All was going fine from the install which I did through windows using a live USB pen I created for the laptop.

Been running the install for a few day perfectly (dual booting) with absolutley no complaints untill last night when I ran the updates. The laptop warned me that is was on battery power, so I plugged in and turned on the power supply. All went well and it rebooted.

Now when I select Ubutu from the boot screen it tries then gives me a error message along the lines of

"Basic bash like line editing is supported. For the first word. TAB lists other possible command completions."

then gives me the prompt

"sh:grub"

I looked in the ubuntu folder on the disk, but it appears it creates a virtual drive and mounts that, so as such I cannot get in to play with the files on my xampp server :(

Any ideas guys?

Jimmy

---

### Post by coffeecat on 2010-04-07
Aha! This one sounds familiar. You're running Ubuntu in Wubi, aren't you?

Have a look at this Launchpad bug report thread:

[https://bugs.launchpad.net/wubi/+bug/484799](https://bugs.launchpad.net/wubi/+bug/484799)

Have a look at post #33 on that thread, which links to:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If this all seems familiar, and you are running Ubuntu 9.10 in Wubi, then replacing C:\wubildr in windows may be the fix you need.

---

### Post by manicmoddin on 2010-04-07
> **coffeecat said:**
> You're running Ubuntu in Wubi, aren't you?

Spot on mate.

Sweet, will give that a try later on when at home.

If works will back up the dev server and repartition the drive and do it properly :P

Cheers

Jimmy

---

### Post by manicmoddin on 2010-04-07
Worked fine,

Just got a few extras in the select ubuntu version screen, but I'm sure I can find info on removing them elsewhere on here!

Cheers mate!

Jimmy

---

### Post by coffeecat on 2010-04-07
> **manicmoddin said:**
> Just got a few extras in the select ubuntu version screen, but I'm sure I can find info on removing them elsewhere on here!

They will be different kernel versions, with the newest first. As a general rule, always keep the immediately previous version installed in case the latest kernel gives you problems. The best way of removing unwanted kernel versions in the grub menu is to uninstall them from the system. If anyone tells you simply to edit the grub configuration menu, that will be bad advice, because the unwanted kernel files will still be taking up room in your system. When you uninstall older kernel versions, the grub menu is automatically updated for you. If you want any more details, just post back.

Good luck with Ubuntu!

---

