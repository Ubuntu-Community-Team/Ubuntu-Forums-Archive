---
title: "Ubuntu 14.04.1 install wiped out Windows"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by parminides on 2014-10-07
I believe I have managed to do the same thing that RedMartin describes in [http://ubuntuforums.org/showthread.php?t=2217611](http://ubuntuforums.org/showthread.php?t=2217611). Namely, overwrite Windows 8 partitions during a fresh Ubuntu installation that was meant to reside in the existing Ubuntu partition only. In my case I was moving from Ubuntu 13.10 to 14.04.1. (All this was motivated by the recent bash security scare, by the way.)

During the installation from a live flash drive, the critical point appears to be when it asked,

"This computer currently has Ubuntu 13.10 on it. What would you like to do?"

The first option was,

"Install Ubuntu 14.04.1 LTS alongside Ubuntu 13.10. Documents, music, and other personal files will be kept. You can choose which operating system you want each time the computer starts up."

I chose the second option, which was,

"Erase Ubuntu 13.10 and reinstall. Warning: This will delete all your Ubuntu 13.10 programs, documents, photos, music, and any other files."

I'm a native English speaker, and I believe the clear and unambiguous meaning of the second option is that it was supposed to install 14.04.1 in the 13.10 partition and leave the other operating systems alone.

When I finished and booted up, the grub menu showed no sign of Windows. Only Ubuntu, Ubuntu advanced options, and System.

The command,

```

df -h

```

yields,

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       680G  176G  469G  28% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.8G  8.0K  3.8G   1% /dev
tmpfs           769M  1.1M  768M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  156K  3.8G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda1       511M  3.4M  508M   1% /boot/efi

```

I've attached an image from gparted, which doesn't look too promising.

Windows 8 is gone, isn't it? It's my understanding that when you buy a computer with Windows 8 pre-installed, there's no way to create recovery disks. I studied the issue when I bought the computer and concluded that it's impossible. I believe it's an anti-piracy feature.

So it's not a question of me being careless and not backing things up. It's not possible to back up Windows 8. That's what the recovery partition is for. Now I'm pretty sure it's gone. Am I right?

Don't bother making any suggestions that will cost me money, such as purchasing another copy of Windows 8. I'm not interested in those. Don't bother telling me that I should have chosen the "Something else" option. (I read that a few times in the forums already.) The meaning of the option I chose was very straightforward. Don't bother complaining that the evil Microsoft won't allow me to make Windows 8 recovery disks. Don't tell me that I don't need Windows. (I had to use Windows to make the bootable flash drive as I couldn't get the Ubuntu utilities to work. I also use Windows 8 for court transcription because there is no reliable foot pedal driver for Linux that I know of.)

I'd be very tempted to switch to Windows after this fiasco, but I'm pretty sure I don't have Windows anymore.

---

### Post by fantab on 2014-10-07
According to the screenshot, you don't have Windows there.
If you plan on recovering the lost partitions then immediately stop using the HDD... boot with Live Ubuntu only.

Your options:
1. Try any Windows partition recovery tool which can be booted from CD/USB... some will offer free solutions and some have paid licenses, your choice. [MiniTool]("http://www.partitionwizard.com/partition-wizard-bootable-cd.html") is both free and bootable cd... see if it helps.
2. Contact your PC/laptop service and explain your accident... they might send you a recovery disc, some vendors have nominal price tag to it... again your choice.

As for Ubuntu, there seems to be a bug in the installer which wipes out all partitions on certain computers.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)
[http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions ]("http://www.omgubuntu.co.uk/2014/08/ubuntu-installer-bug-wipes-partitions")

Though the bug doesn't seem to apply 100% to your case, but still...

---

### Post by Mark Phelps on 2014-10-07
This has been an area of heated debate in which supporters claim the phrase > and any other files. clearly tells you that ALL your files and folders in ALL partitions will be removed; and detractors  claim otherwise.

The Mint developers also encountered this and changed their warning to more clearly indicate that your entire drive will be erased.

Canonical is NOT changing this, as they do not see this as a problem.

---

### Post by oldfred on 2014-10-07
You may be able to contact vendor and get the recovery DVD set for your system. Some offer it for a nominal charge, others do not offer anything. One user who purchased from a local store, was able to get tech at store to make the backup recovery DVD set from an identical computer. Only the vendor OEM version will reuse your existing product key that is embedded in your UEFI.

Mark has posted many times this info, and they say it works for Windows 8.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

It now looks like they are making some fixes, but those will not be in ISO already released. The next point release and next version should include them.


 Reinstall says overwrite Ubuntu but it also erases existing Windows. Only 111 posted that they had this issue.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

