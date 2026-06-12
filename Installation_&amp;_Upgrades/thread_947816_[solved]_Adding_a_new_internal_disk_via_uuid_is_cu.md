---
title: "[solved] Adding a new internal disk via uuid is cumbersome"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by Georges on 2008-10-14
ubuntu 7.10 gutsy

I added a new internal SATA harddisk, used gparted to partition and created an ext3 filesystem on it.
And from there on I'm lost. I have to switch my brain from "dumb gui clicking user" to "console shell linux wizard". Isn't there a gui for fstab? And no, pysdm "Storage Device Manager" does not use the new UUID layout of fstab. In fact it would be best that gparted did the fstab job too.

So after partinioning start a shell. My partition is called /dev/sde1
Gather the UUID:

```
sudo vol_id --uuid /dev/sde1
```

Use this value to edit /etc/fstab (as root) 

```
sudo gedit /etc/fstab
```

use your UUID you just recieved instead of mine:

```
UUID=f6ac1b92-30d4-4fe8-a9cd-b1f9e3b8c456   /data          ext3         errors=remount-ro        0  0  
```

save the file and exit the editor.
create the mount point where you want the new disk to appear

```
sudo mkdir /data
```

populate the uuid symlinks, this is necessary because else you get a nice meaningless message like "mount: special device /dev/disk/by-uuid/f6ac1b92-30d4-4fe8-a9cd-b1f9e3b8c456 does not exist". I found the solution here [https://answers.launchpad.net/ubuntu/+source/udev/+question/30919](https://answers.launchpad.net/ubuntu/+source/udev/+question/30919)

```
[COLOR="Red"]**sudo partprobe**[/COLOR]
```

mount the disk

```
sudo mount /data
```

And next time you boot, the disk will be automatically mounted too.

Hope this helps anyone struggling to add a disk to his box
Georges

---

