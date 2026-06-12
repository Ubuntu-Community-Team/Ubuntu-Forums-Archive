---
title: "Boot-Repair for cloned m2 drive"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by coppercoin123 on 2024-02-24
Hello all,

was linked here from the Boot-Repair community help wiki as the automatic procedure wont work for me.
I just got a new m2 nvme (Samsung 990 pro 4tb). I cloned my old drive (Samsung 970 EVO Plus 1TB). I wasn't able to fix the booting with GParted flags, windows tools like bcdboot or bcdedit. Now i used the live distro for boot-repair and get the following output.

[https://paste.ubuntu.com/p/DbrYHGNT3q/](https://paste.ubuntu.com/p/DbrYHGNT3q/)


[LIST]
[*]I read that even if have the EFI partition properly cloned, the boot manager need to be registered in the NVME RAM somehow. I did not succeed figuring out how, hard to find something in google,.. My PC is always stuck with old drive and properly boots the wrong drive, always - even if i remove the boot flag of the old drive in GParted. Its stubborn. Removing it in hardware to enforce my UEFI boot selection leads to BIOS bootloops (nothing found, even if i see the efi boot files as successful clone)
[*]I also recall that the UUID of the disk need to be changed in the boot manager, but i was not able to do that with windows tools or understand where it is, it seems it works with drive letters (?) and not UUIDs, but i wasn't able to find where it is stored.
[/LIST]

I would have liked to fix the windows boot first and then maybe use GRUB2 for ubuntu dual boot. However maybe its wiser to do first one thing and then the next, because i don't have a third 1tb for backup. If it works in one go, also fine. From my understanding the Ubuntu installation does not touch the windows boot stuff, so if its messed up beforehand it wont be repaired by itself.

Hope the necessary details are covered.

Help is very appreciated, thank you

---

### Post by oldfred on 2024-02-24
You need backups, but with two drives you at least have some duplicates to fall back on.
You do not show any Ubuntu install.
Boot-Repair is for fixing Linux installs, not Windows. It typically updates or reinstalls grub boot loader.

You cannot have duplicate UUIDs.
It does look like you have changed partUUIDs and then have two Windows UEFI boot entries as UEFI uses GUID/partUUID.
See lines starting at 203 showing UUIDs & partUUIDs. And at line 112 UEFI using each partUUID to find boot entry.

But then you have duplicate UUIDs.
We have seen cases where system will one time mount one install and next boot mount other install, really getting data mixed up.
Either unplug old drive and boot with Windows entry using ESP - efi system partition's partUUID of new drive.
Or change every UUID of old drive.

No idea how to do that with Windows. And if done from Ubuntu, if internally Windows will work.
I might try changing old einstall's UUIDs but that will break it anyway. Only one system can be bootable unless totally separate installs.

Examples are using sdX, you have newer NVMe, so /dev/nvme0n1 or nvme1n1, be sure to change correct drive.
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
Or:
[https://ubuntuforums.org/showthread.php?t=2462260&p=14039563#post14039563](https://ubuntuforums.org/showthread.php?t=2462260&p=14039563#post14039563)
with gpt partitioning change both UUID & GUID with gdisk & experts mode.
sudo gdisk /dev/sdX
Command (? for help): x
then see this line
f       randomize disk and partition unique GUIDs

I might just erase 1TB drive and install Ubuntu into it.
But older versions of Ubuntu using Ubiquity installer, will install grub to whatever drive UEFI sees as first drive, probably nvme0n1.
Newer versions let you choose drive and it works. With Ubiquity, the choice is there, but does not work.

I use Kubuntu and it still uses Ubiquity installer and grub installs to wrong drive unless I do an advanced work around. With 24.04, it supposed will change to calamares.
Ubuntu desktop installs proir to 23.10 use ubiquity, server uses subiquity & non-KDE flavors using Qt5 use calamares

---

### Post by coppercoin123 on 2024-02-27
Thank you. Your guide helped me understand what the computer thinks how it should be.

I solved it by removing the old drive and rerun the windows fixed of bootedit in repair mode and bootbcd. Not sure how to boot with the old drive to remove it's boot sector, but I might use the live version for this before installing Ubuntu there.

If someone will have the same problem the fixboot team from Linux seem to care also for the windows people to fix their problems and they have a legacy-windows fix. But I didn't try it because I didn't see it on a first glance.

Hopefully the switch to Grub2 will work fine next weeks.

Solved and happy, thank you.

---

