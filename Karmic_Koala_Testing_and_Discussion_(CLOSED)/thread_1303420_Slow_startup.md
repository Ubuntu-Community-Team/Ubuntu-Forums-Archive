---
title: "Slow startup"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mpiktas on 2009-10-28
Upgraded to RC today. All the reviews raved about improved boot times, so did not anticipate such unpleasantness. After boot screen, it takes 16 seconds for login prompt to appear. To get a working desktop takes full 50 seconds. I created a new user to test whether some applets misbehave, but had the same results.

My laptop is Asus F3Jp with T7200 Intel Core 2 Duo with 2GB of RAM and ATI X1700. 

I strongly suspect that some rogue process is responsible for that. During the startup the disk gets heavily written to. 

Any pointers how to find the culprit? Which log files to check, what processes to inspect?

---

### Post by grizato on 2009-10-28
System > Preferences > Sartup Applications would be the first place I would go.
There was another place that deals with low level stuff n Administration but I've forgotecn the name!

I hope that gives you a head start:)(by the way, you should try auto login;))

---

### Post by mpiktas on 2009-10-28
Yes I have already looked there. No luck. I disabled all the startup processes which I felt comfortable that nothing will break. I will try to remove all the applets. Maybe something will come up.

---

### Post by emarkay on 2009-10-28
By "Boot Screen" do you mean GRUB2?
That issue is covered here:
[http://ubuntuforums.org/showthread.php?p=8182577#post8182577](http://ubuntuforums.org/showthread.php?p=8182577#post8182577)

There is also comments about the "Throbber" taking system resources that could otherwise speed booting, as  noted here:
[http://ubuntuforums.org/showthread.php?t=1284677](http://ubuntuforums.org/showthread.php?t=1284677)

Remember, keep addressing these flaws and they will get addressed!  :)

---

### Post by mpiktas on 2009-10-29
Since I upgraded from Jaunty, I did not use grub2. All the problems start when X starts. Boot proceses before the start of gdm and X is faster.

---

