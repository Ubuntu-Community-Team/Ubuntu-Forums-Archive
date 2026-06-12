---
title: "Manual Install"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by Unr3a1r00t on 2008-05-27
I have been having problems with the installation version of Ubuntu working for me.  If I run the LiveCD, it works fine.  My sound card works, my touchpad works, and my ethernet card works.  However, once I install it, all three of these devices stop working.  Now, I did a dmesg while booted into the Hard Drive, and when booted into the liveCD, and the difference is that the liveCD actually loads the IRQs for this hardware.  However, that does not get translated over for the Hard Drive install.  

So my question is this: How do I install Ubuntu so that it runs as it does when the liveCD is loaded?  I was told to try a manual install, but I would have no idea how to do that.  Any ideas?  Thanks.

---

### Post by wpshooter on 2008-05-27
Have you tried downloading and attempt to install from the ALTERNATE (text based) CD version ?

---

### Post by Unr3a1r00t on 2008-05-27
Negative.  I was not aware there was such a way.  Is that right on Ubuntu's website?


EDIT
I found the alternate install, and will try that now.  I will post in a little bit to let you know how it went.

---

### Post by Unr3a1r00t on 2008-05-27
Ok, I was able to successfully install Ubuntu with it recognizing my network card, my touchpad, and my sound.  However, now when I try to boot into Slackware, this is the error I get:

```

VFS: Cannot open root device "sda4" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
0300   78150744 hda driver: ide-disk
  0301    2000061 hda1
  0302   11719417 hda2
  0303    2008125 hda3
  0304   62420557 hda4
1600    4194302 hdc driver: ide-cdrom
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

So I change the append to "root=/dev/hda4" and then I get this when I boot:

```

List of all partitions:
0300   78150744 hda driver: ide-disk
  0301    2000061 hda1
  0302   11719417 hda2
  0303    2008125 hda3
  0304   62420557 hda4
1600    4194302 hdc driver: ide-cdrom
No filesystem could mount root, tried: romfs
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(3,4)
```

Here is the thing though.  When I do a sudo fdisk -l this is the output:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82c382c3


    Device Boot		Start		End 	Blocks	  Id	System
/dev/sda1		    1		249	2000061   82    Linux swap / Solaris
/dev/sda2		  250	       1708    11719417+  83	Linux
/dev/sda3                1709          1958     2008125   82    Linux swap / Solaris
/dev/sda4		 1959          9729    62420557+  83    Linux
```

Seems as if Ubuntu recognizes the partitions as "sda" and the Slackware kernel recognizes the partitions as "hda".  I am completely lost on this one.  What would cause something like this, and how can I rectify it?  Thanks.

---

### Post by lswest on 2008-05-27
the reason Ubuntu sees it as sda instead of hda is that Ubuntu uses the SCSI drivers, as it was noticed that they support IDE drives better, whereas Slackware runs the IDE drivers, and allocates them the name hda.  This should not affect anything outside of the individual OSes.

---

### Post by Unr3a1r00t on 2008-05-27
> **lswest said:**
> the reason Ubuntu sees it as sda instead of hda is that Ubuntu uses the SCSI drivers, as it was noticed that they support IDE drives better, whereas Slackware runs the IDE drivers, and allocates them the name hda.  This should not affect anything outside of the individual OSes.

So then why wont Slack boot?

---

### Post by lswest on 2008-05-27
> **Unr3a1r00t said:**
> So then why wont Slack boot?

might be that by installing Ubuntu you overwrote a partition that was in use by slackware?  What is on /dev/sda4 (/dev/hda4)?  The Slackware OS?

---

### Post by Unr3a1r00t on 2008-05-27
> **lswest said:**
> might be that by installing Ubuntu you overwrote a partition that was in use by slackware?  What is on /dev/sda4 (/dev/hda4)?  The Slackware OS?

Yes.  Slackware is on /dev/sda4 (/dev/hda4).  I did not overwrite any partition that is required by slack.

---

### Post by Unr3a1r00t on 2008-05-27
Does anyone know what it is I need to do?

---

### Post by Unr3a1r00t on 2008-05-27
> **wpshooter said:**
> Have you tried downloading and attempt to install from the ALTERNATE (text based) CD version ?

Well, I was able to successfully download, install, and run the Alternate installer.  Everything is working beautifully now (except for the fact I still can't boot into Slack >.<) so thank you for your help.  It is much appreciated.

---

### Post by lswest on 2008-05-28
Sorry, I don't use Slack, so I'm not entirely sure what method could be used to fix it without possibly damaging something else.  Maybe someone will be able to answer it soon?

if it's ext2 or ext3, you could probably run an fsck on it.

---

### Post by Unr3a1r00t on 2008-05-28
Yea, I will probably end up just reinstalling Lilo as the main boot loader in the MBR, and then chainloading to Grub for Ubuntu.

---

