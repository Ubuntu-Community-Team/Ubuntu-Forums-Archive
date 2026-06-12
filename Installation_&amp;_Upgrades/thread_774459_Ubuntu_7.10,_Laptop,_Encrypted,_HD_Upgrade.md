---
title: "Ubuntu 7.10, Laptop, Encrypted, HD Upgrade"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by stuman on 2008-04-29
I did it!  I swapped out my 80g for 320g SATA notebook drive in my Toshiba A135 and resized the encrypted space to take the new disk space.  This is my first efforts with LVM, so I'm happy.

Here are the steps that worked.

Since I only one SATA interface, I had to first copy the internal 80g drive to something else.  I used a 120g USB drive and did a "dd if=/dev/sda of=/dev/sdb bs=4096" from a live CD boot (actually used DSL, since I didn't need any lvm or cryptset processes, and it boots more quickly).

I then put the 320g SATA drive in the notebook, booted the DSL cd and reversed the process.

Laptop booted fine, but as expected, was only using 80g of the 320.

I used gparted to increase the extended partition (/dev/sda2) to use the new space.  This left the encrypted partition (/dev/sda5) small, but had room to grow within the extended partition (/dev/sda2).  The default encrypted install is one file system for the whole shebang, and I did not feel like messing with that just now.

After resizing the extended partition (/dev/sda2), I performed the following as root ("sudo -s"): ("*computer*" is your computer name, "*extents_from_?*" is the number of free PE's listed by "pvdisplay" in step "?".

1.re-boot with the Ubuntu live CD.  Use fdisk (as root...to be sure new partition table is loaded) to delete/create /dev/sda5 with same numbers as /dev/sda2.  This file space is not ext2 or 3, so gparted can't be used here.  I used Ubuntu as loading the lvm and cryptsetup programs is easy.

2.If using the Ubuntu live CD, as opposed to another distribution which may come with these already loaded, you will need to load the following software to continue...

“apt-get update && apt-get install lvm2 cryptesetup && modprobe dm-crypt”

3.Open crypt with "cryptsetup luksOpen /dev/sda5 crypt".  You will of course need your pass phrase...  This should grow the encrypted space to fill /dev/sda5. 

4.Resize LVM Physical Volume.  "pvresize /dev/mapper/crypt" 

5.Note how many extents are available to increase root.   Use “pvdisplay”

6.Delete the swap space.  “lvremove /dev/*computer*/swap_1” 

7.Unlock the lv.  “pvchange -x y /dev/*computer*/root”

8.Resize LVM Logical Volume. "lvresize -l +*extents_from_5* /dev/*computer*/root" 

9.Check file system.  "e2fsck -f /dev/*computer*/root" 

10.Grow file system.  "resize2fs /dev/*computer*/root"  (no options should grow it to take all available space) 

11.Note how many extents are available with pvdisplay again.

12.Recreate swap.  “lvcreate -l *extents_from_11* -n swap_1 /dev/*computer*/swap_1”

13.Finish making new swap.  “mkswap -L swap_1 /dev/*computer*/swap_1”  Note the UUID (put in buffer, mark and ctrl-ins)

14.Mount the root system. “mount /dev/*computer*/root /mnt”

15.Edit root fstab.  “vi /mnt/etc/fstab” or your favorite editor.

16.Change the swap UUID.  (Paste in the buffer, shift-ins)

17.Save the file.

18.Relock the lv.  “pvchange -x n /dev/*computer*/root”

19.Reboot from hard drive. 

The "dd" steps take a loooooooong time...but are mostly unattended.  This way, I did not need to re-install anything.

---

### Post by sehe on 2008-09-17
just saying thanks for inspiring a bit of confidence in my upcoming lvm2 exercise!

---

### Post by jonthysell on 2009-08-25
I was hoping this was possible. I have a dying HD and need to upgrade it (same deal even: 80->320). Looks like I need to get to work!

---

