---
title: "Clean install of 22.04 and still get 'mtd device must be supplied'"
date: 2022-08-30
forum: Installation &amp; Upgrades
---

### Post by tjsilver on 2022-08-30
Hello!

After booting my machine (22.04 upgraded from 20.04) this morrning there were 'updates'.  So I did that and when prompted, rebooted.  There appeared a few lines of text, one of which was 'mtd device must be supplied (device name is empty)'.  I was then presented with a tty login (never seen that before!). Logged in but system wouldn't accept WiFi password and no GUI!

Created new bootable USB stick (22.04) and did clean install.

I still get the 'mtd device must be supplied (device name is empty)' message appearing - even after the clean install - and the system won't accept WiFi password.

Any help much appreciated as I've no idea what to do! (Other than going back to 20.04).

Regards,

Tim

31st August - clean install of 20.04 - no 'mtd device' message but wifi password still not accepted - I can 'see' all available networks but cannot connect using wifi (had to revert to ethernet cable - not very good for 2022 [and I fancy all due to a release that wasn't quite ready!])

---

### Post by vvons on 2022-08-30
I have the same problem

---

### Post by ubfan1 on 2022-08-30
The mtd message is not really a problem, and will probably go away after some kernel update.  The wifi issue is not related.  Does your password echo so you can confirm that the correct characters are being sent?  Sometimes a keyboard problem can mess things up, like a numlock, without any led indicator, may change some letters to numbers.

---

### Post by oldfred on 2022-08-30
My system also shows that error/warning, but does not seem to have any effect on booting.

mtd device must be supplied, work around in post #10
[https://ubuntuforums.org/showthread.php?t=2476796&page=3](https://ubuntuforums.org/showthread.php?t=2476796&page=3)
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622)

But my dmesg now does not show error.
System is regularly updated.

fred@z690-jammy:~$ sudo dmesg | grep mtd
[sudo] password for fred:
[ 2.761808] systemd[1]: Starting Load Kernel Module mtdpstore...
[ 2.769635] mtd device must be supplied (device name is empty)
As of Aug 30, 2022
fred@z690-jammy:~$ sudo dmesg | grep mtd
[sudo] password for fred: 
fred@z690-jammy:~$

---

