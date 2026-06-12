---
title: "mdadm: no devices ... were found after RAID0 install"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by gnychis on 2007-06-28
Hi,

I used the minimal server CD to install Feisty Fawn and create a software RAID0.

I was having problems with it actually creating and deleting the RAIDS like I wanted it to, so I manually created them by dropping to a shell.

I used the shell to configure my disks and create the raids and then dropped back to the Ubuntu console setup and it recognized my RAIDs and disks.

Heres what it looked like:
```

RAID0 device 0
   525.3MB   f   swap        swap
RAID0 device 1
   318GB      f   reiserfs    /
SCSI7 (0,0,0)
    #1 primary   139.8MB  B   f   ext2    /boot
    #2 primary   263.2MB       K  raid
    #3 primary   159GB          K  raid
SCSI7 (0,1,0)
    #1 primary   139.8MB  B   f
    #2 primary   263.2MB       K  raid
    #3 primary   159GB          K  raid

```

So I had a swap, a root, and a boot since a boot is needed to bootstrap the RAID.

The rest of the installation went great, I had no errors, nothing.  Grub installed, it was fine.

So then I remove the CD and reboot, it gets past grub and begins to boot (which means my /boot worked, I guess) and I get:

```

Starting up ...
Loading, please wait...
mdadm: No devices listed in conf file were found.

```

and then it pauses for about 2 minutes, and drops me to BusyBox (initramfs)

I'm totally clueless here.  I don't even know where it keeps the mdadm configuration ... should it be kept on boot?  How else does it know what my RAID setup is?  Does it auto detect it somehow?  I managed to run a RAID0 in Gentoo successfully using these same disks and setup.... I'm just not sure where the config is to maybe look at it or even where to begin debugging this.

I'd greatly appreciate any help...

Thanks!
George

---

### Post by gnychis on 2007-06-28
*bump*

there HAS to be someone who has done a raid0

---

### Post by RainKap on 2007-07-22
You may find this thread useful; I did! I had the same problem with 2 boxes using software RAID0, one with SATA drives and the other with plain old IDE.

[http://ubuntuforums.org/showthread.php?t=507074&highlight=mdadm.conf+initramfs+sleep+10](http://ubuntuforums.org/showthread.php?t=507074&highlight=mdadm.conf+initramfs+sleep+10)

Good luck

Ian

---

### Post by phalkone on 2007-07-25
I had the same problem. Used the solution given in this post (added "sleep 10"):
[http://ubuntuforums.org/showthread.php?t=507074&highlight=mdadm.conf+initramfs+sleep+10]("http://ubuntuforums.org/showthread.php?t=507074&highlight=mdadm.conf+initramfs+sleep+10")

When I now restart my machine it fails to stop the MD array. Should I worry about this?

---

### Post by tstavely on 2007-08-16
I get this error message every time I boot.  I think it results from not responding properly to the configuration dialog when I upgraded from edgy to feisty.  I have no raid array, so I didn't know the correct response in the dialog.  How shall I get the boot sequence to stop trying to start up a raid array?

Thanks,
Tony

---

