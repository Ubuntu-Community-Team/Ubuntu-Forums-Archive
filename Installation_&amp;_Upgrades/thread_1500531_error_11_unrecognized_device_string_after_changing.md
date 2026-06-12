---
title: "error 11 unrecognized device string after changing a title in /boot/"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by SusurAce on 2010-06-03
I changed some of the titles of entries in the  menu.lst grub file and now after restarting I get the grub menu with the new titles, but when I try to go into ubuntu i get error 11 unrecognised device string.  if i go to edit mode this is what I have:

root (hd0,4)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=92cde459-a11f-4ef8-
initrd /boot/initrd.img-2.6.32-21-generic
quiet
root

The computer is an hp touchsmart tm2 which was upgraded from Ubuntu 9.10 to 10.04 but I kept the original grub (which I think is legacy)

Is there any way I can solve this, preferably from the grub menu (as this laptop has no cd drive)

All ideas most appreciated, as I am really stuck if I can't get back into ubuntu (damn me and my pointless meddling :( )

---

### Post by ajgreeny on 2010-06-03
What exactly did you change?  If it was just the UUID string, you should be able to get the correct one quite easily by running the usb equivalent of a live CD, which is how I presume you installed in the first place.  If I'm wrong, how did you install the OS?

From that live install run ```
sudo blkid
``` and note the UUID of your ubuntu partition.  Mount the ubuntu partition and edit your /boot/grub/menu.lst with ```
gksudo gedit /media/*mountpoint*/boot/grub/menu.lst
``` file to show the correct UUID. Where I've shown "*mountpoint*" in the pathway you will need to type whatever the /media/*mountpoint* name is, which you should be able to see in nautilus.

---

### Post by SusurAce on 2010-06-03
An update on my issue:

I did not realise the the kernel line was not complete.  When I press e to edit the line, it appears there is a lot more.  The kernel line in fact reads:

kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=92cde459-a11f-4ef9-a11f-4ef8-ae79-a8cced3c5c18 ro quiet splash

as  a uuid of 92cde459-a11f-4ef9-a11f-4ef8-ae79-a8cced3c5c18 
is obviously wrong as all uuid's I have ever seen are in the form:

xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

this is obviously way too long.

I am completely confused, as I thought all I did was change the menu titles :confused: 

When I installed ubuntu I had to use the text based alternative installer as the live disk installer would not work. Is there any alternative ways of finding the uuid?

---

### Post by ajgreeny on 2010-06-03
> **SusurAce said:**
> An update on my issue:

I did not realise the the kernel line was not complete.  When I press e to edit the line, it appears there is a lot more.  The kernel line in fact reads:

kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=92cde459-a11f-4ef9-a11f-4ef8-ae79-a8cced3c5c18 ro quiet splash

as  a uuid of 92cde459-a11f-4ef9-a11f-4ef8-ae79-a8cced3c5c18 
is obviously wrong as all uuid's I have ever seen are in the form:

xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

this is obviously way too long.

I am completely confused, as I thought all I did was change the menu titles :confused: 

When I installed ubuntu I had to use the text based alternative installer as the live disk installer would not work. Is there any alternative ways of finding the uuid?
Yes, I see what you mean about the UUID being too long, but I don't know how you can get the UUIDs of the partitions unless you can get access to the various files on your disk, or can use a live OS of some sort. The ```
sudo blkid
``` command I showed will tell you everything, and you can get a listing with ```
ls /dev/disk/by-uuid
``` but that will just list the UUID files in that folder, with no reference to which partition is which, unless you can find the partitions linked to in someway.

---

