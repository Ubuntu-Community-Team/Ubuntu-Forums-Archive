---
title: "Ubuntu refuses to see my HD"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by JigglyWiggly_ on 2009-12-23
Ok I know the hd works, I even had ubuntu installed on it prior. Then I installed FreeBSD, FreeBSD had no problem seeing it, it installed on it fine. Then I installed Debian on it. (These are all clean installs). Reason I got rid of FreeBSD is because it didn't like software RAID with 1.5tbs, and Debian, well it was having trouble seeing the 1.5tb hds, which Ubuntu actually sees fine. I didn't spend much time on Debian however.


Anyway, so when I try to install ubuntu, it sees only the 1.5tb hds, but not the 300 gig hd I am trying to install too. I unplugged all of the 1.5tb hds and it still does not see it. So then I just put the hd in a usb enclose into a windows box, and formatted it to NTFS. Still nothing, then I put it back in with no partitions. Still nothing. Thing is, fdisk -l reveals that the HD is infact there, why the hell doesn't the installer see it?

Is there a way to install ubuntu without its installer? (Maybe text based installer, like FreeBSD sysinstall?)

EDIT: I just switched sata cables and did a BIOS reset, so there should be no reason it should fail to work, but of course it does.

---

### Post by JigglyWiggly_ on 2009-12-23
I don't get this stupid crap. Debian sees it fine, even freaking Windows. Ubuntu is being retarted. Anyone got any advice?

---

### Post by theDaveTheRave on 2009-12-23
JigglyWiggly_

have you tried booting from a live CD?

can it see the drive then?

You said that you can use an "external case" for the drive

from within ubuntu

```

lsusb

```
before and after plugging in drive, so as you can see what is seen.

Also hunt down details of < [how to fstab]("https://help.ubuntu.com/community/Fstab") > the following comes from the wiki...

```

ls /dev/disk/by-uuid -alh

```

should list all the devices and thier mount points, your disk should be showing up in there somewhere ???

David

---

### Post by presence1960 on 2009-12-23
Try the ubuntu alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by JigglyWiggly_ on 2009-12-23
> **theDaveTheRave said:**
> JigglyWiggly_

have you tried booting from a live CD?

can it see the drive then?

You said that you can use an "external case" for the drive

from within ubuntu

```

lsusb

```
before and after plugging in drive, so as you can see what is seen.

Also hunt down details of < [how to fstab]("https://help.ubuntu.com/community/Fstab") > the following comes from the wiki...

```

ls /dev/disk/by-uuid -alh

```

should list all the devices and thier mount points, your disk should be showing up in there somewhere ???

David
Sorry I mean that I was using a usb enclosure to wipe the hd out on a windows box, but it is plugged in internally. And yeah I have tried booting from the live cd, I'll try the alternate install before I do anything first.

---

### Post by JigglyWiggly_ on 2009-12-23
Ehh I just tried the text installer still same thing :? I am using a crap nvidia 780i board for this box. Thing is during the install it said: One or more drives containing Serial ATA RAID configurations have been found. Do you want to activate these RAID devices?
Activate serial ATA RAID Devices?


I hit yes, but not only does this not make sense because: This HD was fully formatted, not even a quick format with NTFS, and I have reset the BIOS to default...

---

### Post by ThaddeusW on 2009-12-23
I had that same problem a few days ago with an nvidia board. You said you previously had Ubuntu running, what version was it? If you are trying to install 9.10 but previous used 9.04 or earlier I would avoid 9.10 and go back to 9.04.

I have tried to install 9.10 on two different machines, one was an nvidia chip set, the other intel. Both 9.10 installs failed. The nvidia system didn't see the hard disk and the intel machine kernel panicked during live cd booting.

Oh and run a media test to be sure your install cd is not corrupted.

---

### Post by JigglyWiggly_ on 2009-12-23
I think it was 9.10, though it could have actually been 9.04, I will try that. It's not the cds, because I used one for the GUI and one with no GUI.

---

### Post by JigglyWiggly_ on 2009-12-24
Ok, 9.04 works. Then did an upgrade to 9.10 works great. Though now I am using ext3 insteada ext4, well w/e.

It's either something changed in the Linux Kernel, or maybe Ubuntu. I have no idea, but this should be brought up.

---

