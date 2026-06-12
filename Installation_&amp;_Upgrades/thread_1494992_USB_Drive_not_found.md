---
title: "USB Drive not found?"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2010-05-27
I've always used a Seagate external drive (USB) for backup of data.

Now, for whatever reason, the drive isn't recognized/found/seen/appear.

For that matter- none of the USB stick memories I connect are recognized either on any of the USB ports I hook them into.

All of the USB stuff works perfectly in Windows.


This hasn't happened before.

Any idea how to fix it?

---

### Post by PDA1 on 2010-05-27
Anyone?

---

### Post by lindsay7 on 2010-05-27
Run gparted and see if there are errors on that device.

---

### Post by SisterNotes on 2010-05-28
I&#7743; having the same problem. But, I can mount my USB if I start my laptop with the usb plugged in. Ive been searching for a solution for the past few hours and not found anything that works. Anybody else have ideas?
Thanks!

---

### Post by PDA1 on 2010-05-28
I fixed it-

Use Synaptic to get USBMOUNT

Now, that fixed the mounting of  a USB drive but *DISMOUNTING *a drive....I haven't figure that out yet.  I used to use "safely remove....." but that's not a choice that's available.

---

### Post by garvinrick4 on 2010-05-28
Look in configuration editor and go to Apps then to nautilus to preferences and then make
sure media_automount is checked.

Mine is install_mime_activation, media_automount,media_automount_open all checked.

At command line: Give your USB drive a label in disk utility or gparted. Lets say it is flash for this. And in "sudo fdisk -l" (that is small L) it is sdb1
Make directory (one time thing)
```
sudo mkdir /media/flash
```Mount drive
```
sudo mount /dev/sdb1 /media/flash
```Unmount not a typo
```
sudo umount /media/flash
```Always have way to mount at command line and unmount at command line.
Makes life easier.
If need configuration editor, will come up under system tools.

sudo apt-get install gconf-editor

---

### Post by ssulaco on 2010-05-29
> **PDA1 said:**
> 
Now, that fixed the mounting of  a USB drive but *DISMOUNTING *a drive....I haven't figure that out yet.  I used to use "safely remove....." but that's not a choice that's available.
Right click on mounted drive....now left click "unmount volume"

---

### Post by PDA1 on 2010-05-29
The "unmount" option available on right click doesn't provide any results.

Here's the error message that's returned-

[B]Unable to unmount usb0

umount: /media/usb0 is not in the fstab (and you are not root)[/B]

---

### Post by efflandt on 2010-05-29
Under System > Administration > Users and Groups, Advanced Settings > User Privileges, does the user you are running as have permission to "Access external storage devices automatically"?

---

### Post by PDA1 on 2010-05-29
Yes.

---

### Post by SisterNotes on 2010-06-02
I'm still plagued by this one. The crazy thing is that I have two nearly identical laptops. There are only two known differences:
1) one has a newer faster larger hard drive
2) one uses a wireless card and the other a wireless usb

The laptop with the older hard drive uses the wireless usb. The laptop with the newer hard drive and the wireless card (it's older than the usb wireless) is able to consistently mount a usb flash drive.

The "problem" laptop sometimes mounts the flash drive and I will continue to trouble shoot to try to figure out when it works vs. when it won't. Having automount on or off doesn't make a difference. Connecting to the internet using the wireless usb rather than the cable might. I'll try it tomorrow.

Also disabling the non-existing floppy from bios does not make a difference either.

---

### Post by SisterNotes on 2010-06-03
Confirmed!

The USB flash drive won't show up if I'm using the USB wireless connection.

Argh :(

At least now I know why...Any ideas on a work around?

---

### Post by Elfy on 2010-06-07
Threads merged.

---

