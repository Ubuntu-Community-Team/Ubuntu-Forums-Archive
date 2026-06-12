---
title: "Trouble logging into Ubuntu 12.04 on USB 3.0 Drive"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by mtadyshak on 2013-04-09
I setup a 1TB Toshiba USB3 external drive to boot Ubuntu 12.04 (64-bit). I started with the ISO downloaded from the Ubuntu website (12.04 64-bit).
I boot this on a Dell Inspiron 5720 (i5-3210M) which has a 64-bit instruction set. I also boot the drive on a Dell E6430 and I get the same failure.
I went thru the entire process of installing Ubuntu 12.04 and other required packages , two times using two different USB drives with the same result, booting from either laptop.
During the setup process I run Ubuntu Software Update manager, then restart the machine and log in with no problem. Then I install the TI AM335x Sitara ARM EZSDK v05.07 and Code Composer Studio v5.3.0.
After that, when I restart the machine and type the password a purple screen with text appears for about one second then it bounces back to the login screen. It does not say invalid password.
I reboot into recovery mode. It comes up with a read-only file system. I go to the root console and enter:
mount -rw -o remount /
passwd
<password>
<password>
The file system remounts as read-write and it lets me change the password. If I then Resume Normal Boot it lets me log in but then a solid yellow screen appears and the system dies. No disk activity. 
I tried the change recommended here but that did not help:
[bugs.launchpad.net/.../1002429]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1002429")

---

