---
title: "Can't boot normally since last adept update (resume and/or nvidia problem?)"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by geraschenko on 2007-06-24
**Edit: This issue has been resolved.**

I ran adept and updated all the updatable packages. I believe there was a kernel update in there. (I guess I also installed texlive-full, but I don't think that was the problem) Since then, I haven't been able to boot normally. It looks to me like a resume problem and/or an nvidia problem. Here's what I have for you.

I'm running Kubuntu 7.04.

My hda is partitioned into four pieces:
13GB ntfs,
13GB ext3,
30GB extended partition (29GB fat32, and 1GB swap).
My swap space is smaller than my RAM (1.25GB), which is probably the reason suspend and hibernate haven't been working for me, but I'd like to take care of the problem at hand before I resize my swap partition.

I installed nvidia drivers with ENVY.

When I start up, I get stuck at a splash screen. I hit Alt-F1 to get to the following screen:
```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/84e1455d-a6884da6-9678-1a72a160e8b5)=hda6(3,6)
kinit: trying to resume from /dev/disk/by-uuid/84e1455d-a6884da6-9678-1a72a160e8b5
kinit: No resume image, doing normal boot...
resume: libgcrypt version: 1.2.3
resume: Could not stat the resume device file.
	Please type in the file name to try again	or press ENTER to boot the system: <blinking cursor>
```
I hit ENTER, and a bunch of stuff happens 
(* Reading files needed to boot...
etc.)
I see a splash screen in the process, but I eventually get to a terminal with the following line:
```
* Running local boot scripts (/etc/rc.local)			[ OK ]
<blinking cursor>
```
I hit ENTER to get to login screen
```

Ubuntu 7.04 antonia tty1

antonia login:<blinking cursor>
```
so I log in and try
```
startx
```
which produces the following:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux antonia 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 24 10:29:53 2007
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Could not open '/lib/modules/2.6.20-16-generic/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```
Then I run
```

sudo cp /lib/modules/2.6.20-15-generic/nvidia/nvidia.ko /lib/modules/2.6.20-16-generic/volatile/
startx
```
and it works fine. When I want to shut down, I log out and ```
sudo shutdown -r now
``` and push the power button when it begins to restart (if I use "sudo shutdown now", it seems to get stuck). The file nvidia.ko has disappeared by the next boot.

---

### Post by dreadlord_chris on 2007-06-24
the *volatile* in the directory name should give you a clue as to why it disappears each reboot - that file is a link created dynamically each boot **and** is destroyed each shutdown.

The solution is to use Envy to reinstall your video drivers....

---

### Post by geraschenko on 2007-06-24
I tried uninstalling and reinstalling my nvidia drivers with ENVY, but I'm still having the same problem.

---

### Post by geraschenko on 2007-06-24
I guess there are two things I don't understand, and it isn't clear to me how these two problems are related. Please let me know if you understand either of these.

(1) What is going on with resume? In particular, why do I get the message
```

resume: Could not stat the resume device file.
        Please type in the file name to try again or press ENTER to boot the system:
```
Is there some way I can tell my machine not to try to resume from some image?

(2) What is going on with nvidia? Why does the directory /lib/modules/2.6.20-16-generic/volatile exist, and why is my machine looking for nvidia stuff there?

---

### Post by geraschenko on 2007-06-24
All this trouble started 3 weeks ago, but I haven't had time to work on it until now. I just updated everything again through adept and reinstalled my nvidia drivers with the latest version of Envy, and everything seems to be better. I'm happy that things are working now, but I wish I understood what was going wrong.

Thanks for taking the time to read about the trouble.

---

### Post by dreadlord_chris on 2007-06-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/108230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/108230) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **geraschenko said:**
> All this trouble started 3 weeks ago, but I haven't had time to work on it until now. I just updated everything again through adept and reinstalled my nvidia drivers with the latest version of Envy, and everything seems to be better. I'm happy that things are working now, but I wish I understood what was going wrong.

Thanks for taking the time to read about the trouble.

Your *resume* issue: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/108230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/108230)

As for your *video drivers* issue - since you used Envy to install them originally, whenever you update your kernel you're going to have to re-run Envy.

---

