---
title: "boot failed - loosing partitions by UUID label vs identifier"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by serrs on 2007-11-04
I've installed Gutsy on a new partition (hda2).  I have long running Feisty (on hda5).  After the Gutsy install, I could not boot Feisty.  After about 20 minutes I found it was because the Grub config for Feisty was wrong.  root=UUID=blah point to something it could not find.  I had to change the grub kernel line (by hitting 'e' in grub).

The Feisty install I think was moved there from a VMware image.  The grub that was installed before may have been from Gentoo (hda3)...  but when Gutsy detected things it went bonkers.

You have to wait for the initramdisk to time out and the message is very cryptic.

I've also had this problem with /etc/fstab pointing to a data partition that had been remade.  Ubuntu wouldn't boot because it couldn't find an auxiliary data partition.

I like to keep a SysRescueCD around for times like these.  Atleast I know I can get to my data always and rsync it off to another box if safety is needed.

---

### Post by Herman on 2007-11-04
Hello serrs,
Usually mine pauses during booting right after the file system check and all I have to do is hit 'enter', followed by 'CTRL'+'D' keys and it will resume booting up.
After that all I do is update my /etc/fstab with the new UUID numbers for any new file systems I have created.
Editing GRUB's /boot/grub/menu.lst is similarly simple.

All you have to know to get a current list of all your file systems and thier UUID numbers is 'ls /dev/disk/by-uuid/ -alh', (without the inverted commas),
```
ls /dev/disk/by-uuid/ -alh
```You should expect an output something like this,
```
herman@amd46b:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 220 2007-11-02 05:14 .
drwxr-xr-x 6 root root 120 2007-11-02 05:14 ..
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 3c0ea3df-9bbc-4365-84ff-c29b1ad50afa -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 4f7aaf26-a20b-42f1-9838-1aa224afbf76 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 6853B2380721391F -> ../../hdb1
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 6db5cdae-03bb-49ba-a865-255cf8afc45e -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 9e9e5184-127f-45d2-bf4a-e6f0a112f180 -> ../../hda2
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 af9de220-3728-4c35-bf3a-b7c40f8faf0c -> ../../hdc1
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 de6a9292-ff35-4a7d-ad47-9c227036f823 -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-11-02 15:14 e7e39ee8-2022-46bc-af71-a48ab3bd4f61 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-11-02 05:14 f0ff07cb-3064-45fe-8ee5-a65a78cb20da -> ../../sdc1

```As long as you can do that it's really quite simple to copy the appropriate UUID numbers from that output and paste them in the required locations in your /etc/fstab or /boot/grub/menu.lst files.
When that's done you'll have no problems.

Regards, Herman :)

---

