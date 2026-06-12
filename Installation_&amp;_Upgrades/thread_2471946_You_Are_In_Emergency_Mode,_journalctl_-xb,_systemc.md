---
title: "You Are In Emergency Mode, journalctl -xb, systemctl reboot"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2022-02-14
My Ubuntu 20 installation stopped working. I backed up my data and reinstalled. But I'm getting the same error message.

[FONT=courier new]"You are in emergency mode. After logging in, type "journalctl -xb" to view system logs, "systemctl reboot", "systemctl default" or "exit"
to boot into default mode. 
Press enter for maintenance
or press Control-D fo continue."

First of all, how would I "log in" from that prompt?

I've tried a few of the other options listed in the error message but I remain stuck. How do I repair this?



[[IMG]https://i.ibb.co/7yhqmQc/Emergency-Mode-n02-20220213-144339.jpg[/IMG]]("https://ibb.co/7yhqmQc") [[IMG]https://i.ibb.co/F5BxvBq/Emergency-Mode-n01-20220213-144800.jpg[/IMG]]("https://ibb.co/F5BxvBq")[/FONT]

---

### Post by VMC on 2022-02-14
Did you try pressing Enter or Control-D? Then view journal logs

---

### Post by webmanoffesto on 2022-02-14
Yes, and nothing happened.

What is supposed to happen. And how would I navigate to the journal logs?

---

### Post by #&amp;thj^% on 2022-02-14
Can you show us this, might help here:
```
cat /etc/fstab
```
EDIT: From my experience, if you have created a new partition or edited existing one, you may get this error. I had the same error some time back. If you happened to be in the the Emergency Mode and see that it cannot load some of your drives. It means that some of your device id have been changed. So, you have to update the id accordingly in /etc/fstab file. Then do the following steps.

   [list] Type your root password
    [*]cat /etc/fstab
    [*]blkid (show the device ids)[/list]
    Now check which UUID in /etc/fstab does not apper in blkid output
    run 'nano /etc/fstab' and Comment out that line (Just put # infront of the line)
    type 'reboot' (Now your problem should be fixed and after logging in successfully, you can add the current UUID in /etc/fstab file )

---

### Post by webmanoffesto on 2022-02-14
> **1fallen said:**
>  [list] Type your root password
    [*]cat /etc/fstab
    [*]blkid (show the device ids)[/list]
    Now check which UUID in /etc/fstab does not apper in blkid output
    run 'nano /etc/fstab' and Comment out that line (Just put # infront of the line)
    type 'reboot' (Now your problem should be fixed and after logging in successfully, you can add the current UUID in /etc/fstab file )

cat /etc/fstab
Shows
/dev/sda2
/boot/edit
And
/dev/sda3

blkid Shows
/dev/sda1
/dev/sda2
/dev/sda3

[[img]https://i.ibb.co/DCWhBx5/20220214-170650-1.jpg[/img]](https://ibb.co/DCWhBx5)

---

### Post by VMC on 2022-02-15
Now from the '#' prompt, type: [FONT=courier new]```
journalctl -xb
```[/FONT]

---

### Post by #&amp;thj^% on 2022-02-15
> **webmanoffesto said:**
> cat /etc/fstab
Shows
/dev/sda2
/boot/edit
And
/dev/sda3

blkid Shows
/dev/sda1
/dev/sda2
/dev/sda3


Use VMC's suggestion first.
What I wanted to see was the output Like:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=9A36-7777                            /boot/efi      vfat    umask=0077 0 2
UUID=83a67b34-74db-4267-acf9-4748469b3625 /              ext4    defaults,noatime 0 1
/swapfile none    swap    defaults 0 0
[B]###All this was needed and not Shows
/dev/sda2
/boot/edit
And
/dev/sda3[/B]

```
And blkid:
```
/dev/nvme0n1p3: LABEL="Windows-SSD" BLOCK_SIZE="512" UUID="3C6263306262EDD8" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="526bfdb5-6921-42f9-8601-57fce85748ba"
/dev/nvme0n1p1: LABEL="SYSTEM_DRV" UUID="2A62-972E" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="2e9cbfda-caea-4767-954f-e64d6c7cbee1"
/dev/nvme0n1p4: LABEL="WINRE_DRV" BLOCK_SIZE="512" UUID="A45C638B5C635758" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="764800ce-f523-4241-bd80-92a4ab3bc9ab"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="f9c54a4f-7a56-401a-a0fd-40b2bb39a4e5"
/dev/sdb2: UUID="83a67b34-74db-4267-acf9-4748469b3625" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="root" PARTUUID="2f81f3d0-80d3-1342-8228-a34a87b36193"
/dev/sdb1: LABEL_FATBOOT="NO_LABEL" LABEL="NO_LABEL" UUID="9A36-7777" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="237b637f-e727-3f4b-ad0d-13d1632bb362"
/dev/sde1: LABEL="Movie_Drive" BLOCK_SIZE="512" UUID="5F05F2BF0F4C1873" TYPE="ntfs" PARTLABEL="My Passport-New" PARTUUID="ded14405-460a-4cb5-9e99-4a36938734b0"
/dev/sda2: LABEL="Data" BLOCK_SIZE="512" UUID="A2E4464BE4462241" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="d59c74d3-1108-443e-96e9-f258369bf3ca"
/dev/sda3: UUID="9771400b-7788-420b-819a-441e879fa107" BLOCK_SIZE="4096" TYPE="ext4" PARTLABEL="Back-Ups" PARTUUID="250b4ef1-7e03-495f-925e-b479bfc8d16e"
/dev/sda1: PARTLABEL="Microsoft reserved partition" PARTUUID="a2926684-dbaa-45f8-b331-927d0e7e1400"


```
I use a lot disks, so yours I would assume would be smaller in Text shown.

---

