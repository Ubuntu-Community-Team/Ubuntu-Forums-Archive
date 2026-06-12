---
title: "Mount of Root Filesystem Failed: Jaunty to Karmic"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by BJ_Covert_Action on 2010-11-21
Howdy All,

I decided to try to do the 3 distro upgrade stretch from 8.04 to 10.04 this weekend and now I am hung on 9.04 to 9.10.. The upgrade went swimmingly, but I hit a wall upon boot. When I try to load kernel 2.6.31-22 I am greeted with the following error:

```

[   20.879845] ACPI: I/O resource vt596_smbus [0x400-0$407] conflicts with ACPI region SMOV [0x400-0x406]
Mount of root filesystem failed.

A maintenance shell will now be started ...

```

After doing some digging I found [this thread](http://ubuntuforums.org/showthread.php?t=1301724) which appears to be similar in the inability to mount the filesystem. However, it does not mention the ACPI error. I tried everything in that thread; verifying device ID's, editing fstab options; running a filesystem check, and flipping the UTC option in the rcS file but nothing worked. The OP of that thread eventually did a fresh install of Karmic; but I would rather not have to go that far.

I found a few bug reports of this issue, but none of them have proposed fixes attached. I noticed that I cannot run an fstab command from my maintenance terminal (is it a command line utility?) so maybe that's a problem. I also reinstalled my nvidia drivers because those break every upgrade so I thought they may have gummed something up. Finally, I ran update-grub but that also didn't help. My primary partition is ext3 soooo ... that's about all I can think of. Any ideas? 

I can provide any further information requested. I look forward to some help.

Thank you in advance,
Brady C. Jackson

P.S. Posting a thread this long from an N900 make this phone totally kickass.

---

### Post by mörgæs on 2010-11-21
That is a long and risky path. I guess a clean install of the version you want (10.04 or 10.10) is the fast and safe approach.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by sikander3786 on 2010-11-21
> I noticed that I cannot run an fstab command from my maintenance terminal 

fstab is not the command, it is a config file that contains mount point definitions and needs to be opened up with a text editor such as nano.

Please post the output of

```
cat /etc/fstab
```

```
sudo blkid
```

---

### Post by BJ_Covert_Action on 2010-11-21
> **mörgæs said:**
> That is a long and risky path. I guess a clean install of the version you want (10.04 or 10.10) is the fast and safe approach.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Well crap. Is there any effort underway to fix this bug? Or is this going to be one of those issues that simply gets glossed over as a bug in an obsolete system? I don't mind doing a wipe, my home folder is backed up, but this kind of issue in an official upgrade path is a big turn off to new users.....

---

