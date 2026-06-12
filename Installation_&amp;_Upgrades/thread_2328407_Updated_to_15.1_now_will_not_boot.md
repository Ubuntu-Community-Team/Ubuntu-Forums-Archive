---
title: "Updated to 15.1 now will not boot"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by richardlvance-0 on 2016-06-20
After very extended time I get to a tty screen. tty1
As I have never once logged into a tty screen I have no idea what the login is not the password.
Which won;t help me much anyway.

I tried the BIOS boot re0direct to a 13 version and same thing.
The update seems to have screwed the boot pooch.

---

### Post by TheFu on 2016-06-21
Welcome to the forums.  I'd load 16.04 since 15.10 only has a few more weeks of support. [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

If you are really new to Linux, then the steps needed to get the account back might be worse than just reloading.  The summary is to boot off a live CD and look at the /etc/password file on the HDD (not the live boot devices).  That will mean mounting the storage and looking for the file ... The last line (or one of the lines near the bottom) of the passwd file should have your userid.  The number is almost always 1000.  Reboot using the HDD to boot up, not the live-CD.  Login using that userid and your password.  Then we can try to fix things.

---

