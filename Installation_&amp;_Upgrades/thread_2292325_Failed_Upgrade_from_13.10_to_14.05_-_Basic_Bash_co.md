---
title: "Failed Upgrade from 13.10 to 14.05 - Basic Bash commands now gone"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by dakong27 on 2015-08-27
Finally having a window to upgrade from 13.10, I clicked the "upgrade" popup that appears in Ubuntu after boot.  The do-release-upgrade failed in the middle with errors, and now even basic bash commands like sudo, ls, su, etc are gone.  Typing "sudo" returns:

> bash: /usr/bin/sudo: No such file or directory

No other application I try to launch will either, not even xterm.  I have two windows still open on the desktop, one terminal I had entered the "do-release-upgrade" command in, and this browser window that I'm typing this in.  I am reluctant to reboot for fear I'll lose all room to maneuver, and hoping somebody on these boards has seen this before and can advise me.

I've been trying my usual toolkit of bash commands, and very few remain.  I can 'cd' and 'echo', but not much else.

---

### Post by ian-weisser on 2015-08-27
> **dakong27 said:**
> The do-release-upgrade failed in the middle with errors

Backup your data and clean-install 14.04 from a LiveUSB.

Your system may or may not be repairable: It depends upon where in process the upgrade failed, exactly what those errors said, and how many days of effort you are willing to invest.

---

### Post by Bucky Ball on 2015-08-27
13.10 hasn't been supported for awhile and that may have had something to do with it, but I second what ian-weisser suggests.

You could boot from live media, 'Try Ubuntu' and have a look at what's going on, retrieve any data you need to, if it exists.

PS: Do you mean 14.04 LTS rather than 14.05?

---

### Post by dakong27 on 2015-08-27
Yes, I meant LTS 14.04.

I have solved the problem, restored my system, and completed the upgrade to 14.04.  I'll post it here in case anyone else runs into this...

I still don't know how & where the upgrade failed.  But I lost all access to 95% of bash commands.  Some posts Google turned up suggested ctrl + alt + F1 to drop to a shell, login as root, and work it out from there.  I did that and it was a colossal mistake.  Login didn't work, no way to work with the system at all.  Trying to reboot into an older kernel image or recovery image failed at "/sbin/init: No such file or directory" and kernel panic.  

At that point there was no choice but to create a Live USB (couldn't find my rescue thumb drive) and hope for the best.  I booted into Ubuntu Live and worked from the instructions given <a href="https://help.ubuntu.com/community/LiveCdRecovery">here</a>:

> 
[LIST=1]
[*]Boot the Ubuntu Live CD. 
[*]Press Ctrl-Alt-F1 
[*]sudo mount /dev/sda1 /mnt 
[*]sudo mount --bind /dev /mnt/dev 
[*]sudo mount --bind /proc /mnt/proc 
[*]sudo mount --bind /sys /mnt/sys 
[*]sudo chroot /mnt 
[*]apt-get update 
[*]apt-get upgrade 
[/LIST]


I ran into two wrinkles with those steps:  1.  My / and /home partitions are in LVM, so I had to use 

> lvdisplay

to reveal the volumes on the LVM.  From there I had to mount those successively using the steps from the wiki to find the root partition.

The second wrinkle: 2.  sudo chroot /mnt failed with:

> bash: /usr/bin/chroot: No such file or directory

Trying this did not work:

> sudo chroot /mnt /bin/bash

saying, 

> bash: /bin/bash: No such file or directory

using

> ldd /bin/bash

and 

> ldd /sbin/init

showed that those files still existed on my hard drive, and which libraries they linked to.  Then it was clear that it was not that critical files had been deleted or overwritten, but that things weren't linking properly.

I found some threads via Google that suggested replacing /usr/lib with a symlink to /lib, or vice-versa, so I narrowed in on a comparison of /lib & /lib64 on the Live CD file structure vs. /lib & /lib64 on the harddrive.  /lib64 in Ubuntu 13.10, the previous version, had been chock full of libraries.  In Ubuntu 14.04, /lib64 contained one symlink to /lib.  I did

> sudo mv /mnt/lib64 /mnt/lib64bak
sudo mkdir /mnt/lib64
cd /mnt/lib64
ln -s ../lib/x86_64-linux-gnu/ld-2.19.so ld-linux-x86-64.so.2


After that I was able to chroot per the wiki and complete the upgrade process there.  I did have to manually create /etc/resolve.conf with OpenDNS servers

> nameserver 208.67.222.222 nameserver 208.67.220.220

to get 'apt-get update' and 'apt-get upgrade' to run.

I had trouble umounting /mnt after exiting chroot.  Apache2 was still running on /mnt, so I had to chroot back in and 'sudo service apache2 stop'.  However, gdomap and kerneloop were still running and wouldn't let me umount /mnt.  I eventually figured out those were running from Live CD, exited chroot, ran 'lsof /mnt' to get the PIDs of those and kill them.  But 'umount /mnt' still failed on 'busy'.  I chanced 'umount -lf /mnt' and crossed my fingers on 'sudo reboot'.  It worked and the system came back.

I still don't know why the breakdown occurred.  Even now with Google I'm not finding others who've run into the /lib & /lib64 issue in this particular upgrade.  But it seems clear 13.10 relied on /lib64 having its own files, whereas 14.04 is happy to have /lib64 link to /lib.  Somewhere in the middle of that transition, 'do-release-upgrade' quit and bash stopped working.

Hope this helps anyone else who finds themselves in this disagreeable situation.  It is certainly much better than having to do a fresh install and suffering massive data loss (and the environment you've perfectly tuned for maximum productivity over years).

---

### Post by Bucky Ball on 2015-08-28
Excellent news and thanks for sharing. Please see the first link in my signature to mark the thread as solved and help others. Good luck. :)

---

