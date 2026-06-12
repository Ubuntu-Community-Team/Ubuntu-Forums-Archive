---
title: "Lubuntu crashes on clicking Firefox launcher a second time"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by cheapodonuts on 2014-05-05
Fresh Lubuntu install is getting a strange, Firefox launcher x2 = system crash. In other words, I only get this problem after trying to open a second FF window from either the desktop or task bar launchers. Right clicking a link on a current FF page and selecting 'open in a new window' will open a new window with no problems. I can also open as many FF windows as I want via the terminal.
 Installed the system from my new Linux Shop Lubuntu disk last night. Didn't notice the problem till this morning. Today I have updated everything, firstly via update manager, then used the terminal to do apt-get update twice. The issue is still there.
 I installed Chromium just to check and that works fine. So I'm assuming it's a FF/Lubuntu issue.

How do I report and solve the issue?

Terminal launches look like this.
________________________________________________________________

:~$ firefox

(process:1557): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:~$ firefox

(process:1660): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:~$ firefox

(process:1666): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
________________________________________________________________

---

### Post by mikewhatever on 2014-05-05
Looks like a bug. Report it on launchpad. [http://askubuntu.com/questions/5121/how-do-i-report-a-bug](http://askubuntu.com/questions/5121/how-do-i-report-a-bug)

---

### Post by cheapodonuts on 2014-05-05
I am about to try that, but although I have had a Launchpad account for a while, I'm used to Ubuntu setting up some of the info for a bug report before I go there. We'll see. ;)

---

### Post by eren-canpolat-t on 2014-06-08
Hi,

I think I have a similar problem with my AMD machine, which also has NVIDIA GeForce 6150SE nForce 430.

In my case, whenever I try to launch Firefox, first the mouse freezes, then I see a random pattern covering the screen and then everything freezes. I have to hard reset the PC.

Have you found any solutions/workarounds to this problem?

This is a fresh Lubuntu 14.04 install.

---

### Post by cheapodonuts on 2014-06-10
Ah, I forgot about this thread, sorry. My system has fixed itself after a month+ of freezing problems. The only thing I can suggest is to run the software manager and allow full software updates. Then to open a terminal and do sudo apt-get update , twice. Someone on here recommended doing it twice, mostly because it does no harm. :)

I hope this helps.

 I'm marking this thread solved now. :-\"

---

### Post by cheapodonuts on 2014-06-10
As far as I can understand it, the problems were all related to browsers and possibly flash media. But recent auto updates have fixed all. :)

---

### Post by eren-canpolat-t on 2014-06-10
In my case, I still had the problem even after running the updates. And the freeze was not strictly tied to Firefox or Thunderbird. I managed to reproduce the problem by launching AbiWord once. In my case, the workaround was to switching to the legacy proprietary graphics driver for nVidia (I had 3 choices, one of them -the one that said 'tested'- caused kernel panic and I had to reinstall Lubuntu, the second one I tried worked, I dare not try the third one). I guess the *Nouveau* driver is the one to blame. I think it may be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176062](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176062)

I suppose it could also be a firmware (BIOS) problem, but I don't know how to debug it. Dell doesn't provide a way to update the BIOS using Linux and I don't want to risk breaking the PC forever. If anyone is interested in fixing the driver bug, I'm willing to provide logs (provided that instructions are easy to follow).

---

### Post by cheapodonuts on 2014-06-12
Hmm, ironically, I have had several browser crashes in the last two days. So I have removed the 'Solved' tag. As I still have no idea what is causing these issues.
 I have now changed my graphics driver to the proprietary one as well. (good idea EC O:)) So we'll see if that makes a difference.

---

