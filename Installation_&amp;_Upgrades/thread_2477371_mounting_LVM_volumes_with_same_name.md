---
title: "mounting LVM volumes with same name"
date: 2022-07-22
forum: Installation &amp; Upgrades
---

### Post by cunfusu on 2022-07-22
I have two installations of ubuntu  in two separate HD.
In both cases I've chosen the guided partition with encrypted luks volumes.

it looks something like for both devices.

```

[FONT=monospace][COLOR=#000000]sda                      8:0    0 111,8G  0 disk   [/COLOR]
&#9500;&#9472;sda1                   8:1    0   512M  0 part  /boot/efi 
&#9500;&#9472;sda2                   8:2    0   732M  0 part  /boot 
&#9492;&#9472;sda3                   8:3    0 110,6G  0 part   
  &#9492;&#9472;sda3_crypt         253:0    0 110,6G  0 crypt  
    &#9500;&#9472;vgkubuntu-root   253:1    0 109,6G  0 lvm   / 
    &#9492;&#9472;vgkubuntu-swap_1 253:2    0   976M  0 lvm   [SWAP][/FONT]

```


I'm trying to transfer some files by connecting one hardrive via usb on the computer when I'm running a session of the other installation.

I can open the luks partition with cryptsetup command but the logical volumes do not appear under /dev/mapper.

For testing I have created an encrypted logical volume on a small usb drive (but with a different name) and in this case after the partition is opened with cryptsetup I get the volume mapped in /dev/mapper and I can mount it successfully

I suspect this has to do with the fact that the lvm have the exact same name (I can see them with the lvs command). this seems to prevent whatever takes care of mapping logical volums under /dev/mapper from doing it 

Was considering to attempt changing the volume name but it feels pretty risky since I don't know if it can cause undesired effects. Is there any other way to mount such volumes?

EDIT:
articles like this seems to confirm my suspect and propose the rename as solution: 
[https://www.sbarjatiya.com/notes_wiki/index.php/To_mount_LVM_Volume_Group_with_similar_name_on_same_system](https://www.sbarjatiya.com/notes_wiki/index.php/To_mount_LVM_Volume_Group_with_similar_name_on_same_system)

what would be the effect of renaming the volumes/groups? would changes prevent ubuntu from starting

---

### Post by TheFu on 2022-07-23
The combination of VG name and LV name must be unique.
I would use the network to transfer files - rsync if there are more than a few.
If I had only 1 computer, then I'd rename the VG of the "guest" storage.  This will break any prior settings that are dependent on that - if it was the booted drive, then that would impact the /etc/fstab at boot time.

I don't mount storage through the /dev/mapper/ stuff.  It is required, but I dislike using long path+filenames when a shorter one contains more information in a cleaner way.

Look for /dev/{VG name}/{LV name}  Those are what I use in my fstab to mount.  
I've renamed the VG before. Generally, I ensure the VG name is the hostname with an increasing number, so that other VGs can be created later.

VG name: vg-hadar-01
Some LVs: 
lv-root
lv-swap
lv-home
lv-var

I didn't always to this and I'd change it for new installs.  Live and learn. There's always more to know and consider.

---

