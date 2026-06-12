---
title: "WIll not boot with new update"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Ryanmt on 2008-04-24
When booting in recovery mode for the new kernel i get the following
 
ALERT! /dev/disk/by-uuid/<id> does not exist. Dropping to shell!

<insert busybox login prompt>

the /dev/disk/by-uuid/ file does not exist, only by-path does.

I suspect this was caused by ubuntu running out of hdd space when upgrading.

I can boot into the old kernel.. just about (loads ok but with bad screen resolution etc) and i ran update-initramfs -u and it said it was doing something but its not fixed the fault.

What do i do :(

---

### Post by Ryanmt on 2008-04-24
further up in dmesg is the following... this could be due to me unplugging the non OS hdds in the pc just to see if it had any effect (it didnt.. it still doesnt boot)

ata1: SATA link down (SStatus 0 Scontrol 30)
ata2: SATA link up 1.5Gbps (Status 13 Scontrol 30)
ata2.0: qc timeout (cmd 0xec)
ata2.0: failed to IDENTIFY (I/0 error, err_mask=0x4)
ata2: failed to recover some devices, retrying in 5 secs.


Ive booted into the old kernel and ran ls /dev/disk/by-uuid and i get two IDs.

then ive done cat /boot/grub/menu.lst .. the IDs refered to in there refer to the second ID in the previous command.. does that mean anything?

---

### Post by Ryanmt on 2008-04-25
bump

is there anyway i can re-run the 8.04 upgrade script?

---

### Post by Caligatio on 2008-04-25
I did a fresh install of Heron today:

ata3.00 qc timeout (cmd 0x27)
ata3.00 failed to read native max address (err_mask = 0x4)
ata3 failed to recover some devices, retrying in 5 secs
ata3.01 qc timeout (cmd 0x27)
ata3.01 failed to read native max address (err_mask = 0x4)
ata.01 revalidation failed
ata3 failed to recover some devices, retrying in 5 secs

Repeat for quite a few times then it dumps me at a BusyBox prompt.

I was reading on Launchpad that this might be some type of SATA bug...

---

### Post by Ryanmt on 2008-04-29
Finally found a solution.

When booting and you get to the grub stage press ESC, select the 2.6.24-16-generic .. not recovery mode and edit it, add at the end of the kernel line " pci=nomsi" and press b to boot. 

To make this permenant type sudo gedit /boot/grub/menu.lst and edit the lines at the bottom

after a bit of config swapping my hardy install is back up and running at full pace some 4 days later... now, where did i put my marbles :S

---

### Post by panaman on 2008-05-18
> **Ryanmt said:**
> Finally found a solution.

When booting and you get to the grub stage press ESC, select the 2.6.24-16-generic .. not recovery mode and edit it, add at the end of the kernel line " pci=nomsi" and press b to boot. 

To make this permenant type sudo gedit /boot/grub/menu.lst and edit the lines at the bottom

after a bit of config swapping my hardy install is back up and running at full pace some 4 days later... now, where did i put my marbles :S

not sure how you figured this one out... but i had the same problem and adding the pci=nomsi to the end of the line with the kernel worked for me to!

---

