---
title: "unbuntu can not recognize raid drive"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by webappl on 2010-09-20
Hi every,
I intend to install ubuntu server 10.04 on an IBM blade server x3550 m3. The server has two SAS and two SATA II hard drives, each configured as RAID 1 through a ServeRAID m1015 card. However, ubuntu didn't recognize any hard drives at the installation.

Any suggestions? Is there a way that I can load raid driver (if exists) during installing Ubuntu?

Thanks.

---

### Post by lechien73 on 2010-09-20
I think this post might help:

[http://ubuntuforums.org/showthread.php?t=1507344](http://ubuntuforums.org/showthread.php?t=1507344)

It appears that you will have to copy the correct drivers in at install time in order for disk detection to work.

---

### Post by webappl on 2010-09-20
Thanks. I read that post. But how to load the driver file before drive detection?

---

### Post by lechien73 on 2010-09-20
First you will need to copy the driver to a floppy disk or USB stick. During the text-based part of the installer, but before it starts to probe for hardware drivers, do the following:

[LIST]
[*]Press Ctrl-Alt-F2 to switch to a BusyBox prompt
[*]Insert the floppy that contains your driver file
[*]Type:

```
mkdir /mount/floppy
mount /dev/fd0 /mnt/floppy
cp /mnt/floppy/megaraid.ko  /lib/modules/2.6.32-24-generic/kernel/drivers/scsi/
```

[*]Press Ctrl-Alt-F1 to switch back to the installation, and allow the install to go ahead.
[/LIST]

Note that the kernel version I have supplied in the 'cp' command (2.6.32-24-generic) may be different for your install. I have taken this from a stock Ubuntu Server 10.04.1 installation CD. To see what version you have, type:

```
uname -r
```

at the BusyBox prompt.

---

### Post by amtzone on 2010-12-16
i cannot make the dir.....cannot create directory.....please help

---

### Post by needhelpplease on 2010-12-21
I'm hitting the same bug.  I did get the LSI drivers onto a USB stick and got them loaded into the kernel during installation.

It did not help.

The problem is that those LSI drivers do not work with the IBM M1015 RAID card.  The IBM RAID card uses LSI chips but it is subtly different and the LSI drivers don't work.  I called LSI and they told me, "sorry, you're not using an LSI product, call IBM".  I called IBM and they said, "sorry, Ubuntu isn't officially supported.  Why don't you try one of our officially supported OSes, such as [SCO Unix]("http://en.wikipedia.org/wiki/SCO_v._IBM") (SCO: "we've filed a frivolous lawsuit against you, but could you please recommend us to your customers?" IBM: "Sure, of course!"), or Redhat, which costs $2,000 for this server.

I've asked my vendor to accept this entire thing as a return.  This is so stupid.  IBM could probably fix this by investing a few minutes in figuring out what's wrong with the driver.

---

