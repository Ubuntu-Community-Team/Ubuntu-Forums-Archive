---
title: "Jammy &amp; Xenial dual boot cross-partition read"
date: 2022-08-23
forum: Installation &amp; Upgrades
---

### Post by col48 on 2022-08-23
I have a dual boot system (both Ubuntu, no Windows at all) and have just done a fresh install of Jammy in one leg.
I can boot successfully into either the theoretically obsolete Xenial or the fresh-off-the-USB Jammy.  (There has never been an adequate opportunity to install and migrate intermediate LTS in the last few years).

For some time to come, until I have fully migrated everything, I could do with being able to read Xenial files in Jammy and vice versa.  But neither seems to be able to see the other.  In past installations, this has always been possible.  [Maybe it is because Jammy insisted on EFI?]

How can I open files in the 'other' partition, Jammy to Xenial and Xenial to Jammy?

---

### Post by oldfred on 2022-08-23
If you used same user and password, it should not be an issue.
But user actually is user 1000, second user is 1001, etc. Live installer is user 999, so ownship is often different.

But you can change ownership and change permissions.
I use a data partition that all my installs can read/write. And since only data, I can easily reset ownership & permissions if issues. I sometimes use sudo when I actually should not and some data file is then owned by root.

---

### Post by col48 on 2022-08-23
Same user and same password.

Could it be more fundamental than just rw access?  For instance in Xenial, I was expecting to see the Jammy partition listed under 'devices' in the File Manager (I use nemo), but it is absent, not listed at all.  They are on the same hard disk, but I can't find a way to mount the Jammy partition.  gparted sees it (flag esp, no mount point, no label) but it refuses to give it a label, which itself would have been handy.

In case it is useful evidence, the error I get when trying to give the Jammy partition a label in gparted is this:

> e2label: Filesystem has unsupported read-only feature(s) while trying to open /dev/sda3
Couldn't find valid filesystem superblock.

---

### Post by oldfred on 2022-08-23
ESP - efi system partition is only FAT32. And that should be only partition with esp,boot flags.

I have used gparted, disks, and command line to set both file system label & gpt's partition label.
But ESP is normally mounted with 0077 in fstab, so you cannot access it from your install. That is for security reasons, I believe. 
Before 14.04, the ESP was mounted with defaults, and I still often change to that. Probably should change back.
If you do change mount options in /etc/fstab, you can unmount the ESP (with sudo umount /boot/efi), make the changes, and then re-mount the ESP (with sudo mount -a).
[https://ubuntuforums.org/showthread.php?t=2462726&p=14040458#post14040458](https://ubuntuforums.org/showthread.php?t=2462726&p=14040458#post14040458)
sudo cp /etc/fstab /etc/fstab.backup

To see labels:
lsblk -e 7 -o name,fstype,size,model,fsused,label,partlabel,mountpoint,partuuid

---

### Post by col48 on 2022-08-24
This is a murky area for me, and I want to be sure I get it right.  I have a good backup of my Xenial partition and nothing worth keeping on the Jammy one.

Currently, gparted (run in Xenial) shows

sda1 ext4, mount point /, label P16Xenial, no flags, size 228GiB, used 42GiB
sda3 ext4, no mount point, no label, flag esp, size 228GiB, used 13GiB
sda2 extended, size 9GiB
then, indented:
sda6 fat32, no mount point,, no label, flags boot esp, size 37MiB
some unallocated space and a linux-swap as sda5

and (also on Xenial) the fstab looks like this:
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4518fa94-7ee7-4575-b195-f9221af15353 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8296188-c078-4910-a6f2-a2b97f0c715e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


So should I just take off the esp flag from sda3, leaving boot and esp flags still on sda6?  If I do this from Xenial, will I then be able to put a label on sda3 using gparted in Xenial and read files in the Jammy partition from Xenial?
I can't see any read/write/execute bits in fstab - am I looking in the wrong place and is there more I need to do here?

---

### Post by grahammechanical on 2022-08-24
What partition is Jammy (22.04) on? Is it sda3? I am guessing that Xenial (16.04) was installed in BIOS/Legacy mode and Jammy (22.04) installed in UEFI mode. Every OS should be installed in the same mode.

Regards

---

### Post by col48 on 2022-08-24
@graham
You're right on all counts.
I didn't see any choice offered as Jammy installed.  It did initially raise a warning that it might not boot without an EFI partition, so I made one.  Perhaps if I had ignored the warning it would have installed in BIOS mode as the Xenial already was.

This is a bit off-topic, but is there a thread (or a link off-forum) which spells out the risks of a mixed mode situation - bearing in mind that Windows will never be an issue for me?

---

### Post by oldfred on 2022-08-24
Windows requires a boot flag for BIOS boot.
Grub does not use boot flag.
UEFI uses esp, but systems install boot flag also.
Only one boot flag per drive, so Windows in BIOS mode & UEFI's ESP cannot be on same drive.

Only if installing to two drives can you use mixed mode booting, but still not recommended.
If only grub, you have to install both versions of grub, grub-pc for BIOS and grub-efi-amd64 for UEFI. But updates may get system out of sync and then one boot loader may not work.

Advantages to newer gpt partitioning over MBR which is from 1980's. I have used gpt with BIOS only systems starting over 10 years ago.
And if gpt, you can easier convert from BIOS to UEFI. BIOS needs bios_grub partition and UEFI needs ESP on gpt drives.

Ubuntu does let you install in UEFI mode to MBR drives, Windows does not. Ubuntu probably should not either.

Microsoft has required vendors to install Windows in UEFI/gpt mode since 2012, so most hardware now UEFI based. Old BIOS mode was for older systems or large customers with some older hardware that wanted newer hardware but in older configuration for all users.

---

### Post by yancek on 2022-08-24
In your BIOS firmware, do you have options to boot under UEFI as well as Legacy/CSM?  I have that on one of my older laptops and if I have a Legacy install on the computer as well as an EFI install, I can go into the BIOS and select either and boot.  

>   but I can't find a way to mount the Jammy partition.  gparted sees it (flag esp, no mount point, 

If the filesystem for Jammy is set to flag esp, that isn't right.  THe EFI partition should have that.  Create a mount point in Xenial and try manually mounting it.  THen put an entry in /etc/fstab for it to have it mounted permanently.

---

### Post by col48 on 2022-08-24
@yancek
>  In your BIOS firmware, do you have options to boot under UEFI as well as Legacy/CSM?
The boot menu (Grub 2.06) looks very like that I am used to from Grub 2.02 and offers Jammy (as the default) and Xenial.  I presume booting into Jammy is UEFI and into Xenial is legacy.

> If the filesystem for Jammy is set to flag esp, that isn't right. THe EFI partition should have that. 
Referring to the gparted data in my post #5, the Filesystem partition for Jammy (sda3) has the esp flag.  The small fat32 partition has both esp and boot flags.  So should I remove (from gparted in Xenial) the esp flag on sda3?

> Create a mount point in Xenial and try manually mounting it I've never done this - can you tell me what the commands are, please?

> THen put an entry in /etc/fstab for it to have it mounted permanently I imagine this is a line to be added at the end of Xenial's /etc/fstab, using a Text Editor.  What would the line look like?

Sorry to be a nuisance but I know it would be easy to get things monumentally wrong and it is not an area where I have any expertise.

---

### Post by yancek on 2022-08-24
>  The boot menu (Grub 2.06) looks very like that I am used to from Grub 2.02 

I'm not referring to the Grub menu but the BIOS firmware boot options.  You should see a message on boot telling you what key to use to enter the BIOS firmware.  Usually there is an option to temporarily change boot options one time and another option to make permanent changes.  You must have these options or you would not have both a Legacy and UEFI install/

>  The small fat32 partition has both esp and boot flags.

That is correct.  Remove the esp flag from sda3, the jammy partition. 

Mounting a partition simply means making it accessible and a mount point is simply a directory.  Create a directory from Xenial for Jammy when booted into Xenial:

```
 sudo mkdir /mnt/jammy
```

If jammy is on sda3, then mount it:

```
sudo mount /dev/sda3 /mnt/jammy
```

Use the same procedure on jammy for xenial.  Simplest thing for permanent mounting is to go into xenial and get the entry for the filesysetm (/) and copy it to the jammy /etc/fstab file then do the reverse on jammy for xenial.  When doing this, you will have to change the mount point on xenial fstab for the jammy entry to the mount point you created, instead of / , change to /mnt/jammy.  From your post above, you show the below entry for xenial which you can copy to the jammy fstab.

> UUID=4518fa94-7ee7-4575-b195-f9221af15353 /               ext4    errors=remount-ro 0       1 

Change it to the below entry:  Basically removing / and replacing it with /mnt/xenial. Do the same for the jammy entry on xenial.

>  UUID=4518fa94-7ee7-4575-b195-f9221af15353 /mnt/xenial               ext4    errors=remount-ro 0       1

---

### Post by pbear42 on 2022-08-24
FYI to everyone, what the devs did with Jammy (a little earlier, actually, as I recall) is script it to install **both** the BIOS and EFI boot loaders when booted in BIOS or legacy mode.  Any system so installed should boot in either mode.  Anyone interested can test in VirtualBox.  Using the default erase-and-install method, will end up with a GPT disk, a BIOS boot partition, an EFI partition, and a system partition.  Will boot in standard mode (BIOS) or EFI mode (tick box under Settings > System).  By the way, anyone doing a manual installation in BIOS/legacy mode can ignore the squawk about no EFI partition.  Installation will complete without problems and the installed system will boot just fine (in BIOS mode).

[SIZE=1]ETA:  A default alongside installation is more complicated, as the installer can't use GPT.  Instead, it uses extended/logical partitions, one of which will be an EFI partition which (surprisingly) works.[/SIZE]

Anyhoo, what **yancek** said, the *esp* flag on the Jammy system partition can be removed.  Not confident that's what's preventing it from mounting, but no bright ideas for what is.

---

### Post by col48 on 2022-08-24
@yancek
Thank you for your patience.

Yes, I can access the BIOS firmware boot options as you describe and can see both Xenial and Jammy there.

Thank you for the detailed instructions in your post, which I will act on tomorrow - for me it is nearly midnight no and no time to risk a typo or even a mispaste.

@pbear42
I did not erase-and-install to the whole disk, just to replace one legacy partition, so I think that in my case the disk as a whole has not been converted to GPT. I am grateful for the reassurance your post brings that what I have represents one of the possibilities designed for.

---

### Post by Dennis N on 2022-08-24
You want to easily access files on the other Ubuntu?
The simplest way is with Files (the file manager).

In Files sidebar, at the bottom, is "Other Locations". Click that. The right pane opens to show "On this Computer" (see screenshot)
"Computer" is the root of the filesystem.
Below that, are the other OS on the computer. The screenshot shows 4 other OS on this computer.
Click on any to mount it - it will open in a new window.

---

### Post by Dennis N on 2022-08-24
You want to easily access files on the other Ubuntu?
The simplest way is with Files (the file manager).

In Files sidebar, at the bottom, is "Other Locations". Click that. The right pane opens to show "On this Computer" (see screenshot)
"Computer" is the root of the filesystem.
Below that, are the other OS on the computer. The screenshot shows 4 other OS on this computer.
Click on any to mount it - it will open in a new window with the other OS.
Then using two windows, you can copy and paste between the two OS.

---

### Post by yancek on 2022-08-25
col48

I neglected to suggest that before you modify either /etc/fstab file, you make a backup of that file so if there are problems, a mis-type for example, you can go back to the original.

---

### Post by col48 on 2022-08-25
@yancek
Removing the esp flag from the Jammy sda3 partition (using gparted in Xenial) did the trick.  I am surprised that's all it took.  I can access files on the Jammy partition from Xenial and vice versa.  I did not need to modify either fstab - but thanks for the prompt to back it up which I would certainly have done.

Thanks for all your input - the community is a great resource to have at one's back.


@Dennis N
I use Nemo as my file manager.  Without any action on my part the alien data partitions (all are ext4 so mutually compatible) appear in Nemo's side panel (which lists Documents, Pictures, Downloads etc) in a list under Devices - along with any device plugged into a USB port.  To mount them, just click on them.  They get mounted in /<username>/media.

---

### Post by oldfred on 2022-08-25
I am using Kubuntu with Dolphin file manager.
And have several drives & flash drives each with an ESP. Dolphin does not mount the ESPs.
I thought it was because they were actually my ESP with UEFI boot files, but it must be just that it has the esp flag.
Good to know.

---

