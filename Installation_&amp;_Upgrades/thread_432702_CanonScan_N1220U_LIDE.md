---
title: "CanonScan N1220U LIDE"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by dwanders on 2007-05-04
I upgraded to Feisty Fawn when it was released. Never even thought to check my Scanner for operation (as it has always worked in the past with various version of Linux & Ubuntu). But it seems now, that when I run Xsane or Gnome Scan Utility, they both detect the scanner, but time out when I try to acquire a scan or preview. It is a USB only scanner (gets its power from the USB) and it seems to me that the lamp never starts up. 

Any help with this problem would be greatly appreciated.

---

### Post by brianlawson on 2007-05-06
I just ran across the same issue.  So, if it helps motivate the smart guys to find a fix, this is affecting more than 1 happy & proud Ubuntu user.

---

### Post by imon9 on 2007-05-06
that is due to a kernel experimental module called USB-suspend. 
Read the following thread and it may help you:
[http://ubuntuforums.org/showthread.php?t=432130](http://ubuntuforums.org/showthread.php?t=432130)

tell me if it works for u! coz it works for me

---

### Post by dwanders on 2007-05-09
This worked fine for me. However, after installing the kernel, my video (XWindows) blew out and would not launch. Following are the steps I had to use to resolve everytihng:

Have all your Video specs and settings prior to doing it Monitor Name & SIze, V & H sync etc...

Download the kernel from the post above
Install it by Double clicking on it, then selecting install
Reboot
If GUI crashes out, at command line run:
     dpkg-reconfigure xserver-xorg
Answer the questions correctly and reboot again
Everything should be back to normal

After this my scanner now works fine again. Thanks for the information.:guitar:

---

### Post by Ubimad on 2007-05-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/85488) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				their is some work around for some of you, I had to compile a new kernel.

This should not happen for Ubuntu

---

### Post by LeChuck on 2007-06-10
- sry -

---

