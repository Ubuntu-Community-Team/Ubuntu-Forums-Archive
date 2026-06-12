---
title: "Another Grub 15"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by rodent43 on 2006-11-20
Hi,

OK so i have been running ubuntu 5.10 in server mode for a basic samba file and print server and all has been fine...

the drives where as follows

hda1 mounted as a share
hdb1 mounted as a share
hdc1 mounted as a share

hdd CDROM

sda1 mounted as a share
sdb1 / (root)

so i have a need for more space so i was going to remove the CDROM as i never use it... so now hdd is a share to...

but when i reboot i get grub past stage 1.5 then 

Grub loading, please wait...
error 15

thats it...

i thought ok, its looking at the wrong drive as grub used to be root (hd4,0) which is sdb, so i changed to root (hd5,0) which still gives the same error...

any ideas?

---

### Post by DaveBorealis on 2006-11-20
> **rodent43 said:**
> remove the CDROM
<SNIP>
when i reboot i get grub past stage 1.5 then 

Grub loading, please wait...
error 15


Hello,

I wonder if this isn't a problem with your BIOS.  Have you looked and made certain that the new drive is listed, and that the boot order is how you imagine it to be?  If the CD drive was first for booting, could the new drive in its place now be where grub is looking for the boot partition?  Something perhaps to check....

Dave

---

### Post by rodent43 on 2006-11-21
Hi and thx for posting...

it is a very old server tbh and a very old bios...but the bios does see the new drive as expected...the cdrom was probably set to be the 2nd boot device in the bios...

the sda drives are scsi and the boot/grub in sdb, the 2nd scsi?

---

### Post by rodent43 on 2006-11-21
:rolleyes: Anyone?

---

