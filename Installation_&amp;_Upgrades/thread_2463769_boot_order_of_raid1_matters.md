---
title: "boot order of raid1 matters?"
date: 2021-06-17
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2021-06-17
I've installed the latest LTS server version on a raid1 with 3 disks and initially everything worked as expected after the install.

After a bios change, the grub menu comes up, but when I continue, it just hangs.

If a change the the order of the disks in the bios prior to the boot, the boot succeeds and everything works as expected.

As far as I can tell all three disk are identical.

---

### Post by MAFoElffen on 2021-06-18
UEFI or BIOS boot? MBR or GPT disks??

---

### Post by lister171254 on 2021-06-18
Sorry,
MBR

---

### Post by MAFoElffen on 2021-06-18
It really depends on the how you installed and how you setup your /boot partitions on the drives... That takes a few steps to get those to mirror outside of the MD Device. Grub (the low-level parts of it), normally will install to the main boot drive.

---

### Post by lister171254 on 2021-06-19
I've only got 2 partitions. "/" and "/home".

One thing I did do was to change fstab entries for the array from md-uuid to UUID

The original install fstab looks like this

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/disk/by-uuid/533d6c36-54f1-4de4-9dd1-a1553b4588fa none swap sw 0 0
/dev/disk/by-uuid/5b02df05-7475-45b6-9b52-66206970be4f none swap sw 0 0
/dev/disk/by-uuid/bb9ea700-2d45-44d8-858d-b87fe687ac0b none swap sw 0 0
# / was on /dev/md0p1 during curtin installation
/dev/disk/by-id/md-uuid-2f829977:d2924d0a:375f3303:24636ff1-part1 / ext4 defaults 0 0
# /home was on /dev/md1p1 during curtin installation
/dev/disk/by-id/md-uuid-f0fba7f4:0a2ed17b:03f7c64a:e529825a-part1 /home ext4 defaults 0 0
/swap.img	none	swap	sw	0	0

```

I changed this to 
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=bb9ea700-2d45-44d8-858d-b87fe687ac0b none swap sw 0 0
UUID=5b02df05-7475-45b6-9b52-66206970be4f none swap sw 0 0
UUID=533d6c36-54f1-4de4-9dd1-a1553b4588fa none swap sw 0 0
UUID=b10e1181-50c0-4811-b90c-27d8b053dc84 / ext4 defaults 0 0
UUID=8bf648f7-526b-47bf-80e7-1505ca1231e5 /home ext4 defaults 0 0
/swap.img	none	swap	sw	0	0

```

blkid output is
```
/dev/sda2: UUID="2f829977-d292-4d0a-375f-330324636ff1" UUID_SUB="391eb455-40c6-015a-15c5-f8630c021e59" LABEL="ubuntu-server:0" TYPE="linux_raid_member" PARTUUID="15a8c8dd-b4bd-460a-8fda-851f1f0de36e"
/dev/sda3: UUID="bb9ea700-2d45-44d8-858d-b87fe687ac0b" TYPE="swap" PARTUUID="70d410e8-b729-4407-a755-e60d4edbbd15"
/dev/sda4: UUID="f0fba7f4-0a2e-d17b-03f7-c64ae529825a" UUID_SUB="5d25389b-af96-5ac3-6ec1-259bf2fc9dd8" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTUUID="6c4b13a1-b2aa-4851-bde1-29fe84c88613"
/dev/sdb2: UUID="2f829977-d292-4d0a-375f-330324636ff1" UUID_SUB="a9944046-380e-9dbe-caf8-b5d8957807e3" LABEL="ubuntu-server:0" TYPE="linux_raid_member" PARTUUID="b12cdb88-4426-4f7c-838e-beb3082a5036"
/dev/sdb3: UUID="5b02df05-7475-45b6-9b52-66206970be4f" TYPE="swap" PARTUUID="066f9874-9ad6-4a1f-819f-495e36a4f995"
/dev/sdb4: UUID="f0fba7f4-0a2e-d17b-03f7-c64ae529825a" UUID_SUB="ed610f4f-a6df-22ed-c3d4-336beab0c0c0" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTUUID="cab84d92-7a63-4ab5-8b5c-c7ae10414b40"
/dev/sdc2: UUID="2f829977-d292-4d0a-375f-330324636ff1" UUID_SUB="1f5b2cb0-f097-c862-b41c-2d3c18b1a725" LABEL="ubuntu-server:0" TYPE="linux_raid_member" PARTUUID="b163d164-6031-470c-af25-dc8fa37fd792"
/dev/sdc3: UUID="533d6c36-54f1-4de4-9dd1-a1553b4588fa" TYPE="swap" PARTUUID="0656d2ed-145d-4cbf-8615-778ea2948047"
/dev/sdc4: UUID="f0fba7f4-0a2e-d17b-03f7-c64ae529825a" UUID_SUB="e57d31fc-5d2e-18e5-e75e-c29337ee2cb7" LABEL="ubuntu-server:1" TYPE="linux_raid_member" PARTUUID="8555375d-6599-4239-86ee-e63adac5ec8a"
/dev/sdd1: LABEL="System Reserved" UUID="780A1DC30A1D7F76" TYPE="ntfs" PARTUUID="00089e7c-01"
/dev/sdd2: UUID="549E38019E37D9E6" TYPE="ntfs" PARTUUID="00089e7c-02"
/dev/sdd3: UUID="82709409709405D7" TYPE="ntfs" PARTUUID="00089e7c-03"
/dev/md0p1: UUID="b10e1181-50c0-4811-b90c-27d8b053dc84" TYPE="ext4" PARTUUID="be700811-c0f4-41f4-b42b-45c93d1b844d"
/dev/md1p1: UUID="8bf648f7-526b-47bf-80e7-1505ca1231e5" TYPE="ext4" PARTUUID="d1e09d1f-32b8-45f8-8384-2b468876f132"

```

---

### Post by MAFoElffen on 2021-06-19
As long as that "pointer" works for your system, then yes. Now it points directly to the md filesystem that is mounted as root, instead of an md device located on a disk device, which is logically mirrored. 

Grub "should" look at that as where to point to the intramfs image, when grub is updated for it's menu. You could verify that by pausing at the Grub menu > Edit grub, and looking at the kernel boot line, specifically where it is looking for the location of the intramfs image.

* Remember that it also has to be updated in the intramfs image... Just a reminder to others that might see this.

---

### Post by lister171254 on 2021-06-20
I think the issue is grub terminal related.

As I can dual boot, the grub menu is displayed for a period of time before booting into Ubuntu (the default).

When I try and edit the menu, I sometime can scroll up and down without any issues and use any other keys. Escaping the editor boots Ubuntu

Other times, the terminal just hangs (i.e. accepts no keys) after a few key strokes. 

There doesn't seem to be any pattern to this.

If I hit the enter key (to boot the highlighted menu option) when the grub menu is displayed, the machine never boots.

If I let the timeout expire, it always boots.

Confused...

---

### Post by MAFoElffen on 2021-06-20
Entertained. LOL. 

Not sure what is going on there,. What did your kernel boot line say?

---

### Post by lister171254 on 2021-06-20
Getting this screenshot is how I found the weird behaviour

[ATTACH=CONFIG]288706[/ATTACH]

---

### Post by MAFoElffen on 2021-06-21
Which in the Linux boot line of the Grub, Grub did pick up the change that you made in the fstab, using the root filesystem in your MD filesystem (UUID=b10e1181-50c0-4811-b90c-27d8b053dc84)...

So, yes, that verified that the changes where applied across where they needed to be (In Grub also)... So now it is generalized across all the Raid1 members.

Not sure of the quarks you are noticing in Grub, while in edit mode... Sometimes that's just how it is dealing with your keyboard, before an OS system is loaded (lowlevel, basic drivers, trying to deal with some USB keyboards). But those are usually staightened out one the the OS, is loaded and better, less generic keyboard drivers are used...

Everything is working now right?

---

### Post by lister171254 on 2021-06-27
After upgrading to 21.04 everyting seems to be working as expected.
Thanks.

---

