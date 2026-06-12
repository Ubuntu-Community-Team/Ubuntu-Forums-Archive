---
title: "After I upgraded to be 7.10 I can not to adjust resolution to 1024X768"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by noname2 on 2007-11-02
After I upgraded to be 7.10 I can not to adjust resolution to 1024X768
[[IMG]http://img81.imageshack.us/img81/8599/screenshot1lg7.png[/img]](http://imageshack.us)

My Monitor blink all time and dim but when I adjust resolution to 800X600 My monitor is OK
But I prefer 1024X768

Before upgrade I use 7.04 I can use 1024X768 why after upgrade my laptop has problem !!!

How to solve this problem? Thank you very much :-)

---

### Post by mikewhatever on 2007-11-02
Check your xorg file for the right resolution. If it is not there, add it manually, save and exit. Restart x.
Another way is to reconfigure xserver. Hit Alt+Ctrl+F1 and type > sudo dpkg-reconfigure xserver-xorg
Go through with the wizard, then restart X.

---

### Post by noname2 on 2007-11-02
After I use wizard and restart X
Then I restart ubuntu it's show me
- Running local boot scripts ( /etc/rc.local )

ubuntu can not to load GUI for login

How to solve this problem? Thank you very much :guitar:

---

