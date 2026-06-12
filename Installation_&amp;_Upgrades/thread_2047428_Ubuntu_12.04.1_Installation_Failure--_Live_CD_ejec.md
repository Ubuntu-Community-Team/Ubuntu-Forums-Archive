---
title: "Ubuntu 12.04.1 Installation Failure-- Live CD ejects? Help!"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by jessgraham on 2012-08-24
I'm attempting to install the newest version of Ubuntu on my Windows 7 laptop, and the installer has crashed every time I've tried. I put the ISO (downloaded from the Ubuntu website directly) onto a LiveCD. As soon as I get to the partitioning option, and click on the option to install Ubuntu alongside Windows 7, the installer goes black, displays some text, and ejects the LiveCD. Then it returns to my Windows 7 startup screen.

I've tried to problem solve and attempted to fix the problem, but with no luck. Please help!

[ATTACH]223136[/ATTACH]

[ATTACH]223137[/ATTACH]




Ubuntu version is 12.04.1. OS is Windows 7 on Compaq laptop.

---

### Post by houseworkshy on 2012-08-24
First double check the md5 of the iso, could be a glitch in the iso itself.  Always use write once only discs burnt at the slowest speed your burner allows. Also use the latest iso you can get because bugs will have been fixed ( there was an installer bug in very early versions of 12.04 ) and less updating will be needed.   It's worth mentioning if you trying to do a wubi install ( inside windows ) or true duel boot ( onto a seperate partition/disk ) ?  True duel boots are generally better.  You can from a live session install tiny things to the RAM.  One which is very handy is sysinfo, using that is the easiest way of posting system specs.
This is actually only a bump as I'm still on 10.04 and on a differant PC so others can give better advice but providing the extra info suggested above may help them to do so.  Good luck.

---

### Post by jessgraham on 2012-08-24
Double-checked the md5 and it was clean. I used slow, write-only disks as well. I used the latest ISO, downloaded from the Ubuntu website. I was trying to do an install that installed Ubuntu alongside Windows, so a dual boot, like you said.

Thanks for all the advice though!

---

### Post by 2F4U on 2012-08-25
Do you experience problems when running the liveCD, i.e. try Ubuntu without installing?

---

### Post by kansasnoob on 2012-08-25
One more double (or triple) check. When you first boot the live CD and see this screen:

[http://www.psychocats.net/ubuntu/images/installingprecise00.jpg](http://www.psychocats.net/ubuntu/images/installingprecise00.jpg)

you have a whopping 3 seconds to press a key. Then you'll see the language selection screen followed by the boot options as shown here:

[http://www.psychocats.net/ubuntu/images/installingprecise02.jpg](http://www.psychocats.net/ubuntu/images/installingprecise02.jpg)

Be sure to choose "check disc for defects". It takes a few minutes to complete but it's worth the time to be certain that the burn was good ;)

---

### Post by jessgraham on 2012-08-25
No problems when running the Live CD- it works perfectly up until pressing the "Install alongside Windows" button.

kansasnoob: Your images didn't show up in the thread (bad link?) but I'll attempt the check disk for defects option. Thanks!

---

