---
title: "Bad fstab will not boot"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2010-09-02
Ok, I made a mistake in my fstab. I know what the problem is and how the fstab needs to be changed. However, since the system will not boot I'm having diffeculty getting in to edit it.

The system is running Ubuntu 10.4 64 Bit with LVM2.

I have both 10.4 64Bit Server and 10.4 32Bit Desktop cds currently and could burn others if needed.

With 32Bit Desktop I'm able to get to a live cd prompt but my hard disks are not mounted.

if I try mounting /dev/sda5 to a dummy directory I created it tells me it doesn't know the type of 'LVM2_member'.

---

### Post by Tipo on 2010-09-02
Mounting LVM partitions is a slightly different process. This post outlines how to do it: [http://ubuntuforums.org/showpost.php?p=4079308&postcount=2](http://ubuntuforums.org/showpost.php?p=4079308&postcount=2)

---

### Post by TennTux on 2010-09-02
Thanks for the clue Tipo. :)

However, I encountered a problem.

After reading your recommended post I came up with the following commands (volume name changed).

```
sudo apt-get install LVM2
sudo lvm lvdisplay -m
sudo mount /dev/mapper/VOLA-root /mnt/work
```

The response ```
mount: special device /dev/mapper/VOLA-root does not exist
```

I did make one change and not reboot as I'm essentially running on a live cd. However, I was able to use the lvm command to display my logical volumes.

Any more clues?

---

### Post by Tipo on 2010-09-03
> **TennTux said:**
> 

```
sudo apt-get install LVM2
sudo lvm lvdisplay -m
sudo mount /dev/mapper/VOLA-root /mnt/work
```

The response ```
mount: special device /dev/mapper/VOLA-root does not exist
```

I did make one change and not reboot as I'm essentially running on a live cd. However, I was able to use the lvm command to display my logical volumes.

Any more clues?

Hmm, is 'mapper' the name of your VolumeGroup? Mine looks like so:

```
LV Name    /dev/vg_ubuntu/lv_root
```

First, lets try activating the LVM group

```
sudo vgchange -ay vg_ubuntu
# then mount like this
sudo mount /dev/vg_linux/lv_root /mnt/work
```

The -ay in the vgchange command basically means 'available yes', which lets the kernel know your LV is there.

---

### Post by TennTux on 2010-09-03
> **Tipo said:**
> Hmm, is 'mapper' the name of your VolumeGroup? Mine looks like so:

```
LV Name    /dev/vg_ubuntu/lv_root
```


In my posts here I am using VOLA as my volume group. And the logical volume I need access to is root. To use your format mine would be:
```
LV Name    /dev/VOLA/root
```

In my post I used */dev/mapper/VOLA-root* because the post you referenced used the */dev/mapper* followed by *VolumeGroup-LogicalVolume*.

When I tried it and it failed, I tried several other variations including the mount you suggested, however, I didn't do the vgchange. I will try it again just to be sure but I need to boot the system and redo the install of LVM2 as I'm basicly booted on a live cd (not persistent).

Just to refresh our memory. I added a bad line to my /etc/fstab file that I either need to remove or edit to be correct. So I'm trying to get access to the root of my system from a live cd.

---

### Post by TennTux on 2010-09-03
Houston, we have lift-off.

It seems the trick was from a live cd boot I needed to tell the kernal to recognize the Volume Group with the vgchange command.

To summerize the working solution for those that follow.

VOLA    = Volume Group
root    = Logical Volume

```
sudo apt-get install LVM2
sudo lvm lvdisplay -m
sudo vgchange -ay VOLA
sudo mkdir /mnt/work
sudo mount /dev/mapper/VOLA-root /mnt/work
```

Thanks again Tipo. :)

---

