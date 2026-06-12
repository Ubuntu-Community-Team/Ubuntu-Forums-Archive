---
title: "Ubuntu 9.10 - Issues after installation"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Drackard on 2010-03-02
Hi,

I'm currently testing Ubuntu 9.10 x86-64 on various types of servers at Work so that we can ensure it functions fine before offering it to our clients.

To begin with I encountered no problems and every installation I did, regardless of the hardware, worked fine.

I then hit an issue which has been bothering me for a while as I'm yet to find any resolution to it.

In short, I perform the installation, the server reboots and then it stops at the automatic FSCK which runs on the initial boot up. It hangs there and doesn't do anything. I reboot the server and then rather than automatically selecting the kernel at GRUB, it simply stays at the GRUB screen until a kernel is selected.

Once one has been selected, it boots fine with no problems. I'm trying to resolve the issue so that after the initial boot, it doesn't hang on the FSCK and it goes straight to the login prompt.

This is happening on the following types of chassis so far:

Dell SC 1425

Dell PowerEdge 860

Dell SC 430

Unfortunately I cannot provide exact hardware specifications, as the hardware varies depending on the clients requirements.

Any help would be greatly appreciated!

---

### Post by khelben1979 on 2010-03-03
If I were in your situation I might go for a [LTS release]("https://wiki.ubuntu.com/LTS") (see link) instead for better stability.

---

### Post by Drackard on 2010-03-03
Hi khelben,

Thank you for your reply. Unfortunately I'm not in a position to make the decision of using an LTS version, simply been asked to test 9.10 so that we can officially use it.

Do you know if there's anyway of disabling the automatic FSCK?

---

### Post by khelben1979 on 2010-03-04
It's not recommended to turn it off, however this is how you do it:
    > [Johan] The fsck parameters are kept in the filesystem itself. 

    ## This will disable forced fsck after a certain number of mounts.
     tune2fs -c 0 /dev/${partition.}

    in my case 

      tune2fs -c 0 /dev/hda1

    ## This will disable forced fsck after a certain period
     tune2fs -i 0 /dev/${partition.}

    in my case 

      tune2fs -i 0 /dev/hda1

    `$ man tune2fs' for details. 

    Kind regards Johan H 

[Source of the information.]("http://linuxgazette.net/issue76/tag/6.html") Try it at your own risk, never tried it myself.

---

