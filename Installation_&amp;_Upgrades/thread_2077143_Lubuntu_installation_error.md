---
title: "Lubuntu installation error"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Lunestic on 2012-10-27
I'm trying to download Lubuntu on my new laptop.

Got the iso here: [http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)
Then used UNetbootin to put it on my usb drive.

I booted from my usb, selected install Lubuntu, and it started the Wubi installer in Windows.  However, I got this problem near the end: 

[IMG]http://puu.sh/1jqlJ/98bbb0488bd6d8756a6dd91e0ed4116b[/IMG]

First it was for 12.10, then I tried for 12.04 and the exact same thing happened.

Can anyone help me?
Thanks.

---

### Post by bcbc on 2012-10-28
That's probably this bug: [https://bugs.launchpad.net/wubi/+bug/989991](https://bugs.launchpad.net/wubi/+bug/989991)

You can check the log file to find the real problem (prior to the null reference failure).

In general though, you shouldn't create a bootable USB to install wubi. Just place the Wubi.exe in the same directory as the ISO and run it like that. 

For lubuntu, you need the 12.04 wubi.exe (due to another bug): [https://bugs.launchpad.net/wubi/+bug/1043607](https://bugs.launchpad.net/wubi/+bug/1043607)

(There's a workaround on that bug report). Since you have the USB, just copy the wubi.exe off that as it's 12.04, and then place the ISO in the same folder as that wubi.exe before running.

---

