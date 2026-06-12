---
title: "Aspire One A110 - UNR installation troubles"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Goat Boy on 2009-12-22
Hi guys, 

New here, new to Linux, new to Ubuntu.  Something of a Windows, sort of power user, sick of it.

Trying to install UNR on the Aspire One, it has an 8GB SSD, and I also have an 8GB SD card, sometimes in while trying to install, sometimes not.

Not going to try and re-type all the stuff, figured I'll post some screenies instead.  I've tried to search, but so many variations of the netbook model, so many different issues, and me not knowing all the terms, so, here goes:

The installer tends to hang at 70% while launching the partitioner, at the menu: 'Detecting File Systems'.  Sometimes happens, sometimes not, installer functions better while running UNR off the live CD.
[IMG]http://i47.tinypic.com/2jc6nt2.jpg[/IMG]

Not really a major issue, but maybe a symptom?

Big problem is here, when I get through, I get a partition failed to mount message:
[IMG]http://i49.tinypic.com/zsr39f.jpg[/IMG]

The drive is empty of all partitions prior to beginning the install:
[IMG]http://i50.tinypic.com/ego7ps.jpg[/IMG]

Have tried multiple different sources of ISO files.  Have tried multiple different USB programs.  Tried multiple different USB Pen Drives, and have tried to install the OS on both the SSD & SD Card.

Getting pretty frustrated at this point.  I even tried to install Jollycloud, which installed successfully, however GRUB failed to install.

Any help would be much appreciated.

Cheers,

GB

---

### Post by Goat Boy on 2009-12-22
Oh yeah, also checked the USB for errors.  Most were clean, the current one I'm running LiveCD off is as well.

---

### Post by Goat Boy on 2009-12-29
Bump

---

### Post by siabost on 2009-12-29
Hi,

In the light of no replies from the more experienced here's my tupence worth!

Although I have installed Ubuntu plenty of times to a desktop I've never done so on a netbook with a flashdrive instead of a HD.

If I were you I'd try the "Specify Partitions Manually" option. This will allow you to specify the size of each partition, which format to use (ext3 or ext4), whether to format the partition, and which should be bootable.

In a desktop scenario I would do something like this:
First partition = specified as 7.5Gb, / (root: where the OS gets installed), ext4, format partition YES, boot flag ON.
Second Partition = specified as twice the onboard memory size, SWAP (memory exchange)
Third Partition = Remainder of HD, /HOME (where your docs & files are stored), ext4, format partition YES, boot flag OFF.

Now, with an SSD drive the SWAP partition may not be a good idea as the system may continually write and rewrite to it & the relative sizes of each partition will have to be different because you have only 8Gb to play with. There may be more info on the forum re this.

It's always a good idea to have a root (OS) partition & a /HOME partition as this allows a reinstall of the OS without wiping your personal files (a good back-up is always advisable though).

I hope this helps. :)

---

### Post by Goat Boy on 2009-12-29
Thanks Siabost, I'd tried that though.

Here's an interesting update.

Trying to install on /dev/sda, the SSD.

Gparted will not modify partitions /dev/sda2 & /dev/sda5
/dev/sda is not mounted.

Attempts to mount/unmount in the terminal confirm this.
Attempts to reformat using the terminal command yields:
/dev/sda is apparently in use by the system; will not make a filesystem here!

Now how in the heck is it in use?  If it isn't mounted?

Very possibly the problem?

---

