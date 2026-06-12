---
title: "(K)ubuntu on ASUS N550: issues and fixes"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by LK_gandalf_ on 2015-05-03
Hi, I just installed Kubuntu 15.04 on my Asus N550JK. I have a number of issues, so I was hoping that others could help and share their solutions?

Not working:
- external subwoofer
- brightness (f5-f6)
- mute, volume up and down (f9-f10-f11)

**Nvidia graphic card. (fixed)**: after the first installation I only got a black screen. To access the system, I needed to:
- when grub shows up, press e and edit the line: remove "quiet splash" and write instead "nomodeset".
- when you are on the desktop, enable the repository "partner" (you can do it from software center muon >> sources)
- then launch the driver manager. A list of drivers will appear, I installed the recommended one. Reboot.


Working out-of-box:
- wifi
- keyboard backlit (f4-f3)
- microphone
- webcam


Links with some fixes and guided, some outdated, not tested:
[http://linux-on-n550.blogspot.no/p/n550jv-issues-and-fixes.html](http://linux-on-n550.blogspot.no/p/n550jv-issues-and-fixes.html) (many typos in the commands)
[http://ubuntuforums.org/showthread.php?t=2201047](http://ubuntuforums.org/showthread.php?t=2201047)
[https://bugzilla.kernel.org/show_bug.cgi?id=65091](https://bugzilla.kernel.org/show_bug.cgi?id=65091)
[https://wiki.archlinux.org/index.php/ASUS_N550JV](https://wiki.archlinux.org/index.php/ASUS_N550JV)

---

### Post by dino99 on 2015-05-03
Looks like shortcuts have changed  [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1451084](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1451084)  and needs to be redefined as you wish (but then not standard)
About sound, pavucontrol should help to set the best parameters

---

### Post by LK_gandalf_ on 2015-08-09
Hi
I am trying again with ubuntu, after some months, since I coud not solve the black screen issue and had no time to work on it.
Now it seems with latest upgrades the screen is fine. Also the audio volume buttons are working.

What is still not working:
- external subwoofer, still produces both basses + music, it's messy
- brightness (f5-f6)
- extra functions under some keys (for example "insert")
- mouse logitech G700s, working very bad.

Any idea? I really cannot find enough info online, as if nobody has this laptop and linux :(

---

