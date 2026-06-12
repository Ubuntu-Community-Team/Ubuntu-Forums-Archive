---
title: "LVM Problems, can't use autopartitioner, volume in use?"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by dudinatrix on 2007-03-15
I've got a Dell PowerEdge server, and I'm trying to install Ubuntu Server 6.10 on it. It's configured with pure hardware RAID 1. The first time I tried installing it, I chose "Erase entire drive and use LVM". The following was set up:

```

LVM VG Ubuntu, LV root - 152.GB Linux device-mapper

        #1 152.6 GB    f ext3           /
SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
        #1 primary    255.0 MB B f ext3 /boot
        #5 logical      6.2 GB   f swap swap
        #6 logical    152.6 GB   K lvm

```I continued, thinking it would later ask me to set up remaining partitions (/home, /var, etc). It went ahead with clock setup stuff, so I tried to go back to the partitioner. I then added a few partitions like so:

```
LVM VG Ubuntu, LV root - 152.GB Linux device-mapper
        #1 152.6 GB    f ext3           /
SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
        #1 primary    255.0 MB B f ext3 /boot
        #5 logical      6.2 GB   f swap swap
        #6 logical     30.0 GB   f ext3 /home
        #7 logical     20.0 GB   f ext3 /var
        #8 logical      1.0 GB   f ext3 /tmp
        #9 logical    101.6 GB   K lvm
```But when I tried to write the changes, it said it might have problems and may need a reboot first. Sure enough, it failed. I tried rebooting, but now I simply cannot recreate that LVM structure.

When I try to again do "Erase entire disk and use LVM", I get an error saying "Autopartitioner using LVM failed...". It instructs me to view the fourth virtual console (CTRL+ALT+F4). Doing so shows the following error:

"Incorrect metadata area header checksum"

Now I'm just lost. I've tried zero filling the beginning of the disk, I've tried recreating the LVM manually.. and just nothing is working. If I go ahead without LVM, it seems to proceed fine. But I want LVM!

How the heck can I get it to get back to that first initial format created with the "autopartitioner"??? any ideas?

---

### Post by dudinatrix on 2007-03-15
Ok, I think I was making a dumb mistake. I was manually creating the Volume Group, and then tried to proceed.. but I finally realized I kept forgetting to make the Logical Volume. (this is all new to me) 

So I just tried again...
[LIST]
[*]Made the /boot partition
[*]Made the swap partition
[*]Made the lvm partition
[*]Created the LVM Volume Group
[*]Created the LVM Logical Volume
[*]Set up the Logical Volume to ext3 /
[*]Tried to reconfigure that lvm partition to break it up into /home, /var, etc... but then realized duh, I probably should have created those first and used the lvm partition as the remainder. Right? So I'm trying that now...[/LIST]

---

### Post by dudinatrix on 2007-03-15
That worked! However, there is one difference that I'm not sure is correct... Here's the original setup that Ubuntu autopartitioned the first time:

```
LVM VG Ubuntu, LV root - 152.GB Linux device-mapper
        #1 152.6 GB    f ext3           /
SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
        #1 primary    255.0 MB B f ext3 /boot
        #5 logical      6.2 GB   f swap swap
        #6 logical    152.6 GB   K lvm
```

And here's the one I manually created


```
LVM VG UbuntuVG, LV LunaLV- 101.5 GB Linux device-mapper
        #1 101.5 GB    f ext3           /
SCSI1 (8,0,0) (sda) - 159.0 GB Dell VIRTUAL DISK
        #1 primary    255.0 MB B F ext3 /boot
        #5 logical      6.2 GB   F swap swap
        #6 logical     30.0 GB   F ext3 /home
        #7 logical     20.0 GB   F ext3 /var
        #8 logical      1.0 GB   F ext3 /tmp
        #9 logical    101.6 GB   K lvm
```

The main difference i'm seeing being the SIZE of that Logical Volume. Ubuntu made it basically the full size of my disk. When I did it, I used the max size available, which was 101.5 GB -- the size available after all my other partitions. Any idea which is the correct way to do it?

---

