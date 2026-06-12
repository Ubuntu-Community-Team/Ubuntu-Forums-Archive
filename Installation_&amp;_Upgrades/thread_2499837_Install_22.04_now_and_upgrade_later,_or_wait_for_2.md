---
title: "Install 22.04 now and upgrade later, or wait for 24.04.1"
date: 2024-08-12
forum: Installation &amp; Upgrades
---

### Post by David_Wright on 2024-08-12
To expand on the title, I am running 22.04 but want to reinstall (so as to encrypt the installation).

I was waiting for the point release of 24.04.1, but see that this is now delayed a couple of weeks.

Which is my best option here:
[LIST]
[*]Install 22.04 now, then wait for a stable 24.04.1 point release to upgrade later
[*]Install 24.04 now
[*]Keep waiting for 24.04.1
[/LIST]

---

### Post by TheFu on 2024-08-13
Wait.  No question.  There's no issue with 22.04. You have until April 2025, at least, to move the 24.04 and that's if it isn't Ubuntu Server or Ubuntu Gnome Desktop. All the other flavors get 3 yrs of support. You have time.

Do you have excellent backups? If you use encryption, you NEED excellent backups. If anything gets corrupted, it is possible to lose all access to everything inside the LUKS container.  Also, how good are you are LVM?  LUKS encryption comes with LVM.  I really dislike the default why LVM LVs are setup.   The "root" LV is far too large on most disks.  Just yesterday, I installed a new 24.04 flavor onto a laptop.  All my laptops use whole drive encryption.  Immediately after the install, I "fixed" the LVM to more closely match my storage management needs.  Here's the layout I've started with - not overly complex - It is just a portable computer for travel, not a main system.
```
$ lsblkt 
NAME                TYPE  FSTYPE        SIZE FSAVAIL FSUSE% LABEL MOUNTPOIN
nvme0n1             disk              476.9G                      
&#9500;&#9472;nvme0n1p1         part  vfat          512M  504.8M     1%       /boot/efi
&#9500;&#9472;nvme0n1p2         part  ext4          1.7G    1.3G    12%       /boot
&#9492;&#9472;nvme0n1p3         part  crypto_LUKS 474.8G                      
  &#9492;&#9472;nvme0n1p3_crypt crypt LVM2_member 474.8G                      
    &#9500;&#9472;vgmint-root   lvm   ext4           35G   24.1G    22%       /
    &#9500;&#9472;vgmint-swap_1 lvm   swap          4.1G                      [SWAP]
    &#9492;&#9472;vgmint-home00 lvm   ext4           20G   18.5G     0%       /home
```
Here's another view:
```
$ dft
Filesystem                Type      Size  Used Avail Use% Mounted on
/dev/mapper/vgmint-root   ext4       34G  7.5G   25G  24% /
/dev/nvme0n1p2            ext4      1.7G  194M  1.4G  13% /boot
/dev/mapper/vgmint-home00 ext4       20G  4.4M   19G   1% /home
/dev/nvme0n1p1            vfat      511M  6.2M  505M   2% /boot/efi
```

Adding new LVs or extending existing LVs is about 4 seconds.  Reducing any LV is more complex.  I booted off the Installation ISO and used "Try Ubuntu" mode to reduce "root" and do the other things.

I reduced "root", deleted "swap_1" and recreated it as 4.1G, added "home00". the sizes are likely to work for me for the life of the system.  I'll likely create a "stuff" LV that will hold temporary files for travel that don't usually get backed up - think videos, music, stuff that I'll keep the "official copy" on other storage back home.    Root at 35G is larger than I'll need.  If I decide to run some virtual machines, I'll have libvirt create an LV for each VM.  As you can see, the disk is about 500GB and I'm using only about 60GB.  

For backups, having extra free space in the VG is important so LVM snapshots can be taken to get clean (uncorrupted) backups on a running system.  Those snapshots are around just long enough for the backup to be completely.  The first backup takes as long a an rsync would, but every version after that, using the backup tool I use, will be less than 2-4 minutes.  Easy, fast, efficient.  100% necessary with encrypted storage.  OTOH, I consider backups required for all my storage holding data and settings and a few other things.  If the storage in this laptop dies, it is a used laptop, I want it to be an inconvenience, not a terrible data loss event.

BTW, see how the 2 partitions outside LUKS are much too large?  Those are the default sizes. Quite wasteful.  If I'd manually setup the storage, I'd have made /boot 700MB and EFI 50MB.  I hate waste.  My first HDD had 20MB, so the idea that some pre-boot code needs 50MB really bothers me.  It is only using 7MB, so even 50MB is overkill.

On another UEFI boot system that is from pre-COVID, ```

Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.7G   25G  24% /
/dev/nvme0n1p3                           ext4  672M  **309M**  314M  50% /boot
/dev/mapper/vg01-home01                  ext4   20G  9.6G  9.1G  52% /home
/dev/nvme0n1p2                           vfat   50M  **6.1M**   44M  13% /boot/efi
```
This system isn't LUKS encrypted, so I was able to setup exactly the storage layout I wanted. It has a minimal desktop, which avoids most bloat.

---

### Post by currentshaft on 2024-08-13
.

---

