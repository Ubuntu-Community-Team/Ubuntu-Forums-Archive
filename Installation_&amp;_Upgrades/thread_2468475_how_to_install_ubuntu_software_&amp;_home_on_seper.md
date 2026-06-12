---
title: "how to install ubuntu software &amp; home on seperate partitions"
date: 2021-10-30
forum: Installation &amp; Upgrades
---

### Post by mcsheffrey on 2021-10-30
I would like to install ubuntu on one partition and my /home on another partition. So I can restore the software without all my user data.

---

### Post by guiverc on 2021-10-30
You can re-install Ubuntu and have it not touch any user files, and even have it restore the *manually* installed packages; ie. if I made a packaging mistake & my system is a mess; I can re-install Ubuntu (*or flavors which is Lubuntu in my case*) without losing my files, music and my chosen music player which isn't included with Lubuntu, will be auto-reinstalled. None of this requires a separate partition.

This (*re-install without touching user files, re-install of [Ubuntu repository] manually installed packages*), is a QA-*testcase* we test for with Lubuntu ([*install using existing partition*]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743")) but it works for all *flavors* and main Ubuntu too.

I do like having a separate partition; but that's mostly as it allows me to replace this system with a non-Ubuntu and keep data files; Ubuntu doesn't need them to be separated to re-install & keep files. Key is you don't format your partitions.

To install; I also use "*Something else*" and setup my disk how I want.  In Lubuntu with the `calamares` installer that option is called "*Manual Partitioning*", with KDE's Qt skin it's called "*Manual*" but its the same; just a different name for the same option.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by mcsheffrey on 2021-10-30
OK, I will try the "something else" approach. I use clonezilla as a backup and this way I can just restore the partition/partitons that I need to.  Thank you

---

### Post by TheFu on 2021-10-31
> **mcsheffrey said:**
> OK, I will try the "something else" approach. I use clonezilla as a backup and this way I can just restore the partition/partitons that I need to.  Thank you

Clonezilla is an image-based tool, not really suitable for real backups.  Backups need to be versioned - like daily - with 90+ days of versioning, so that we can return to any date over that period.  Of course, most people don't have that amount of raw storage, so the versioning usually takes the form of differences between the files.  There are forward diff and reverse diff methods.  

Real backup tools handle these versions for us.

Considering that 90 days of versioned backups typically needs just 30% more storage than the source files, I struggle to understand why people don't just do it that way.

As for separate partitions ... that's one way to split things, but there are much more flexible solutions if you use LVM or ZFS.  Today, ZFS isn't really ready for the OS, but LVM has been enterprise used and proven for over 20 yrs.  

However, the installer makes setting up LVM storage "the correct way" not-so-easy.  There is a 1-click LVM install option, but then we have to go back and massively reduce the "root" storage LV (logical volume), add /var and /home LVs and finally setup the fstab to mount those new storage places where we need them.  Some people with greater security needs may create a /tmp LV.  Each LV gets different mount options so it is often that /tmp/ would be mounted in a safer way with a few extra options to make using that file area for anything except data slightly more difficult should the system be compromised.

When I'm setting up new systems with LVM, I get the installer booted, then change to a different console and run some commands/scripts to setup the storage areas exactly as I'd like them.  Something like this:
```
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage (PV and vg00)
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB 
 swap   swap            LV/SWAP         swap    4.1GB 
```
Those last four lines are all LVs inside partition #3.  /var may need to be larger, but with LVM, it is 5 seconds to allocate more storage from the VG into **any** LV.  Add up the used storage and you'll see post-install only about 80GB is used.  I don't think / will need to be resized larger, ever.  Partition #3 will be nearly the entire HDD/SSD - so for most of my physical systems, 500GB.  That will be the entire PV and VG sizes too.  Plenty of room for all sorts of LVM goodness, like taking a few read-only snapshots to aid with getting perfect backups that won't be corrupted.
If I need some scratch storage for junk - I'll create a /stuff LV that will never get backed up or hold and data that is important. For example, on a laptop, this can be entertainment files for travel - perhaps a few videos and music that is kept elsewhere.
After I use **sgdisk** to create those partitions, then **pvcreate**, **vgcreate** and **lvcreate** are used for the LVM stuff. Next, I'll use **mkfs** to create file systems onto each partitions/LV as needed - typically ext4, but the EFI must be FAT32 by standards.  The swap LV has to use **mkswap**.  The last thing I do is swap back to the installer and choose "do something else" ... which let's use connect the storage up to what the installer demands we have.  This way, it will directly put things onto the correct places of the disks during the installation and setup the fstab for us.

LVM is pretty great, provided you've worked through a tutorial for how to set it up and how to use it in the future.  If I need to move to a larger SSD in the future, a single command can move an entire PV (including the VG and LV parts) to new storage - - while the system keeps running!  How great is that?  There are techniques to add more storage while the system keeps running if the hardware supports hot-swap.  I've used this as well.  The main trick to getting the most from LVM is to only allocate storage to LVs for about 3 months of use. Adding more is easy. Removing too much storage from any LV is more difficult and can require off-line work from a separate boot disk.  Only allocate what you ABSOLUTELY KNOW you need for the next few months. Never take all the storage in the VG. Always leave about 10% for use as short-term snapshots which can be used for backup needs.

---

