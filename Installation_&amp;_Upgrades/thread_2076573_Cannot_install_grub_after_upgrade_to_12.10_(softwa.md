---
title: "Cannot install grub after upgrade to 12.10 (software RAID-1)"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by jcauchy on 2012-10-26
Dear All,

I just finished upgrade from 12.04 to 12.10. I have fake RAID 1. During the install I get a message that grub cannot install on /dev/dm-1 so I waited until the installation is finished and tried to install grub by hand. But I failed:

```
piglet:~$ sudo grub-install /dev/mapper/isw_ecjaadgfhh_Volume0p1
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

```

After trying several more googled things I tried [boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), but it also failed starting from:

```
sudo dmraid -ay
RAID set "isw_ecjaadgfhh_Volume0" already active
ERROR: opening "/dev/mapper/isw_ecjaadgfhh_Volume0"

```

[Here is boot-repair log.]("http://paste.ubuntu.com/1306993/")

So after finished 12.10 install, I still did not reboot the machine (without grub I am afraid to do so)

Anybody could help me? 

Wojtek

---

### Post by darkod on 2012-10-26
First of all, /dev/mapper/... is fakeraid 8bios raid), not linux software raid.

I am not sure whether you can add grub2 right now since you didn't reboot it yet after the upgrade. I don't know how is the system mounted and whether everything is updated.

I suggest to reboot the machine, and if it doesn't boot without grub2 properly installed, boot it with a 12.10 live cd into live mode, open terminal and try adding grub2 to the MBR of the array with:
```
sudo mount /dev/mapper/isw_ecjaadgfhh_Volume0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_ecjaadgfhh_Volume0
```

That should install it to the array. Reboot without the cd and see if it boots.

---

### Post by jcauchy on 2012-10-27
> **darkod said:**
> First of all, /dev/mapper/... is fakeraid 8bios raid), not linux software raid.


Right. I corrected it in the original post.

> 
I suggest to reboot the machine, and if it doesn't boot without grub2 properly installed, boot it with a 12.10 live cd into live mode, open terminal and try adding grub2 to the MBR of the array with:
```
sudo mount /dev/mapper/isw_ecjaadgfhh_Volume0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_ecjaadgfhh_Volume0
```

That should install it to the array. Reboot without the cd and see if it boots.

It worked! Thanks!

---

