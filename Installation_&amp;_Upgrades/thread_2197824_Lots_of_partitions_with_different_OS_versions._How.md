---
title: "Lots of partitions with different OS versions. How do I know what's installed?"
date: 2014-01-05
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2014-01-05
I have 6 different partitions with different versions of Ubuntu, Lubuntu, Mint, etc. Is there a command or a app I can use to see each partition and what OS version is installed? I know how to see what OS is installed but I need to know which version so I can get rid of some of them. Within the last 2 weeks, I was doing something and remember seeing a partition table that showed this. For the life of me, I can't remember what I was doing or what program it was. Gparted does NOT show this. Neither does the Disk program. 

Anyone have any ideas? Doesn't have to be a GUI app, just needs to list the partition and version of Ubuntu.

---

### Post by varunendra on 2014-01-06
The command from within the OSes is -
```
lsb_release -a
```

From outside, the version (release, or "issue") information can be read from "**/etc/issue**" or "**/etc/lsb-release**" files.

---

### Post by Bucky Ball on 2014-01-06
I just use Gparted when I want to remember where things are. You can work it out by what's mounted, or not, where in the particular install you're working in.

The best way of going about this is to give all partitions descriptive labels (different to the mount point names) when installing. For instance, I have 'mini' '12.04' 'LFS' as labels so when I look in Gparted I know I have a minimal install mounted at sda12, 12.04 at sda something (can't remember) and the Linux From Scratch partition at sda something else. And a heap of other, labelled, partitions besides.

You can also boot from a LiveCD, open Gparted and give them labels when the partitions are unmounted.

---

### Post by oldfred on 2014-01-06
I run BootInfo script to see where everything is and document it.
BootInfo report runs a script called bootinfoscript which I run as part of my rsync backup for regular documentation.

       [URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by mastablasta on 2014-01-07
volume labels - i've been using them since DOS era.

---

### Post by nerdtron on 2014-01-07
I'm not quite sure if this will work but have you tried reading the output of /etc/motd?
Basically every install of OS will have an motd (message of the day) that will be shown when you login the command line. It will show version of the currently installed OS.
So if you have multiple drives with different OS version on each, try "cat etc/motd" on each drive and see the output.

---

### Post by Bucky Ball on 2014-01-07
> **mastablasta said:**
> volume labels - i've been using them since DOS era.

+1.

---

### Post by PopsTheSailor on 2014-01-07
> **mastablasta said:**
> volume labels - i've been using them since DOS era.

Yea, kind of like backing up your hard drive. It works if you do it before the problem hits.

Although I wouldn't say the issue is solved, but I opened each instance and wrote down the info. I also labeled them all for future ref. I'm marking as solved but would be nice if I could remember what I was doing when I saw the information.

---

### Post by 1clue on 2014-01-07
Pick the one you like best, install kvm/qemu.  Set all the other ones up as VMs, either all together or separately.

I haven't actually dual booted anything in years.  I've had a spare partition in case I wanted to, but somehow never did.  VMs work great, you can use multiples at the same time.

---

