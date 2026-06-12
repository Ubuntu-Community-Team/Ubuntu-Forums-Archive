---
title: "Grub shows gray screen when system in LUKS."
date: 2020-08-07
forum: Installation &amp; Upgrades
---

### Post by jhnur on 2020-08-07
Hi,

I would like that Grub starts without typing my password for LUKS, and only if I select Ubuntu then ask for the password.
Therefor I made three partitions:
[LIST=1]
[*]/boot/efi, fat32, EFI partition, 512 MB. 
[*]/boot, ext4, 512 MB. 
[*]/ in LUKS partition with ext4, 1 TB. 
[/LIST]

The Grub screen is gray with no text.
Is there a way to fix this ?
I'm using GPT + EFI, but no LVM.
The OS is Ubuntu Mate 20.04, and it does start after a few seconds.

Before I had my home folder in LUKS. That worked, but this time I wanted to have the /tmp and /var also in LUKS.
I have read this: [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019), but I rather don't want to type commands that I don't understand. I can not find the tool 'refreshgrub'.

---

### Post by TheFu on 2020-08-08
If you don't want to type in a password to unlike the storage, what's the point of using LUKS?  It isn't like a running system with LUKS is anymore secure than a running system without LUKS.  LUKS is about security when the system is NOT running and preventing anyone from having access to the data when they don't know the unlock code.

Setting up whole drive encryption is pretty easy during an Ubuntu Install.  Just check the box to have the installer do if for you.  After the fact, it is ugly.  But modifying or adding more methods to unlock does require typing commands. If you are unwilling, perhaps using LUKS isn't for you?  

If you want to understand commands, there isn't much more we can suggest than reading the manpage for **cryptsetup**.  Access it using **man  cryptsetup** or run the **xman** program.  Your system already has a full copy of the manpage for the exact version of the program on YOUR system.  A link found through a websearch; that information won't be the same, exact, version of the tool that is already on your system.

If something in the manpage isn't clear, feel free to copy/paste the parts here and someone can try to explain. We'll assume you looked up any word definitions already and just need clarification. Sometimes encryption terms have very subtle meanings.

If there is a text entry box on the first screen after boot, that's where you need to enter the grub password.  That can be a mix of static and dynamic entries.  It can be a challenge-response from a crypto-key.  LUKS supports 8 "slots" for different authentication methods.  I have 3 setup.
[LIST]
[*]Really, really, really, long not-sure-I-can-type, passphrase. It is static.
[*]Mix of a passphrase I type, plus a very long, static, entry from a hardware device.
[*]Challenge-Response solution from YubiKey.  The challenge is a passphrase that I know. Then the yubikey outputs a valid, crypto, response, that LUKS understands.
[/LIST]

There are some other methods, but those 3 above don't require any networking enabled to work.  I've heard about people using PKI keys stored on USB flash drives for their authentication. That just seemed too non-secure to me.  I know some enterprises have a network key server, so if a HDD it not on a specific subnet in their enterprise, then it is locked and cannot be unlocked by anyone ... who doesn't also get the key server.  That's a little much for a home user to setup.  Plus, when the govt comes, they will be taking all your computers anyway.

---

### Post by jhnur on 2020-08-10
I **do** want to use LUKS when I want to start Ubuntu.
My other operating systems are often on other SSDs, and I want to use Grub to start those as well, without having to unlock the Ubuntu partition.

My problem is with Grub. The screen stays gray instead of showing a menu. 
Clearly, I am making a thinking error somewhere. It is probably because previously I had my 'home' in a seperate LUKS partition and everything else in a normal ext4 partition. That worked.
Is it possible to fix my setup without having to run install, since I have spent a lot of time to set Ubuntu (Ubuntu Mate) to my preferences.

---

### Post by TheFu on 2020-08-10
All user preferences are stored in your HOME, so if you backup that, do a fresh install, then restore, all your settings will be back.

System settings are stored in a number of places. For desktop users, those typically are just new themes. I don't know where those go, since I use fvwm and all settings are stored in my HOME for that WM.

If you've made system-wide changes, backup those config files too. They'd usually be in /etc/ somewhere. If restoring to the same exact hardware and not reformatting storage, it is safe to just restore everything in /etc/.  If moving to new hardware or changing storage around, then it is best to selectively merge any manual updates made previously under /etc/.

If services have been installed, then the data and configs for those are known to the admin. Backups of them are that admin's responsibility.  For example, a static website would typically have those files under /var/www/ somewhere.  MariaDB, Postgres, MySQL would usually put DBs under /var/lib/ somewhere. Backup those things as needed.

I put custom code under /usr/local/ because that's the correct location for it.  This is all outside any package management, so I backup that area too.

Then there are just the list of manually installed packages and snaps and flatpaks.  **apt-mark showmanual** will get a list of manually installed packages. Save that to a file.  Do something similar for the other stuff.

Last month, perhaps the month before, I posted a simple backup script to do all the HOME directories for all users under /home. [https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172](https://ubuntuforums.org/showthread.php?t=2447368&p=13973172#post13973172)

So, do the backup, do a fresh install, restore the backup.  Should need 30-45 minutes, tops.  Obviously, this doesn't include the time needed to restore 25TB of videos, just typical email, documents, some software development stuff - say you use rvm, perlbrew, pyevn for your development stuff. It will all be under HOME, just like before.

---

### Post by TheFu on 2020-08-10
I hope you have excellent backups.  Anyone using encryption needs excellent backups or everything can easily be lost.  Backup skills comes way, way, way, way, before encryption skills.

---

### Post by jhnur on 2020-08-10
TheFu, thank you. I didn't know the 'apt-mark showmanual' command. That is very helpful. I'm still migrating from my old computer.
I will try to disable my NVMe SSD with my current Ubuntu and make a fresh install on a SATA SDD to check if Grub will run okay and check what is different from what I did. That will take some time.
The reason for my new install is that I bought a new computer to be able to organize my files and backups ;)

---

### Post by jhnur on 2020-08-11
A fresh install with "whole disk" and selecting LVM with encryption worked as expected. Grub starts and I can choose the OS, and when I select Ubuntu then the LUKS password is requested. Installing was just like in this video: [https://www.youtube.com/watch?v=KIvZVr6P4fc](https://www.youtube.com/watch?v=KIvZVr6P4fc)

I am forced to use LVM and since that is an extra layer that I don't need, I prefer not to use it. But it is no big deal.

There are some differences:
My partition for EFI is different. It is FAT32, but not the same as the one that install process created.
My Grub partition has a "x86_64-efi" folder, and the Ubuntu whole disk encrypted install made a "i386-pc" folder.
My "grub.cfg" is missing two lines for LVM. I think that is normal.
I don't have a "gfxblacklist.txt". The other two files "grubenv" and "unicode.pf2" are the same.

It seems that I have to start all over to install Ubuntu and transfer my files. I will try a few things a wait a week before doing that. Thanks for your help.

---

### Post by TheFu on 2020-08-11
> **jhnur said:**
>  
I am forced to use LVM and since that is an extra layer that I don't need, I prefer not to use it. But it is no big deal.
 

If you look at the disk layout, you'll see that all the LVM objects are contained inside the LUKS volume, so only 1 LUKS Open is needed, thus only 1 authentication need be requested.  That's the power of LVM.  

**Ignore the following, unless you "like" file systems and storage management:**
95% of the time an "LV" can be thought of as a normal partition, but on steroids.  LVs can be resized up and down. LVs can be created.  Only resizing down (lvreduce) requires downtime.  lvcreate and lvextend are 5 seconds and can be run safely while the file systems are in use.  Cannot do that with normal partition, which always need downtime for changes.

lvm snapshots are very handy for uncorrupted backups too.  To create a snapshot for backup purposes, storage to hold all changes made during the backup period must be available in the VG.  In short, never allocate the entire VG to LVs. Always leave some unused storage.

When it is time to move to a large HDD, pvmove is your friend. That 1 command can move a PV from disk 1 --> disk 2. It will take the VGs and LVs using that PV with it - all while the system keeps running.  

Want a mirror (RAID1)?  vgchange or lvchange can convert non-mirrored storage into mirrored storage.  A great way to move specific LVs to new storage. After the mirror is complete, we can have LVM break the mirror, choosing to remove the old storage. All while the system is running.

What to do thin provisioning?  This is a way to make different users think they have 1.1x to 100x more storage than they really have, then automatically increase the amount available as needed to a specific limit.

LVM does add some complexity for all the features it brings.  That's the trade-off.  Once you get just a few of these capabilities down and use them, you'll never use plain partitioning again.

Of course, if you like living on the edge, 20.04 has ZFS for the OS.  
[https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new](https://ubuntu.com/blog/zfs-focus-on-ubuntu-20-04-lts-whats-new)  ZFS will change the way you see and use storage completely.

I did a new install of 20.04 last week and found they finally got the LVM setup stuff easy to use (relatively). I almost cried it was so good. Almost as good as CentOS had in 2010.  Ah, someday.

---

### Post by jhnur on 2020-08-11
All my backups and all my 'home' files are in a ext4 LUKS without LVM. I like to keep it that way. Later on I might turn to btrfs.

The install that I wrote about with whole disk encryption turned out to be not a EFI.
I could not turn off my NVMe SSD in the BIOS, so I gave it a try and did a install on a SATA disk with EFI-only in BIOS.
Now I can boot into the new installed system, but it is still using the EFI partition of the NVMe and I can no longer boot into my NVMe Ubuntu.
So now I have a total mess, which I wanted to prevent by making Grub work.

---

### Post by jhnur on 2020-08-12
It seems that Grub does not work on my new computer.
Should I start a new topic or report this somewhere ?

I have not cleared all my disks, so I still have to do more tests.
What I did initially should have worked, it seems that Grub is the problem.

CPU: AMD Ryzen 5 3600
Motherboard: Gigabyte B550M Aorus Pro
SSDs: one in the first PCIe slot (NVMe) and one in the second PCIe slot (SATA mode) and a few SATA SSDs.

Grub should be able to start a LUKS with and without LVM, but for my tests I am using the whole disk encryption from the installer which also uses LVM.

Installing on a SATA SSD works. However, a LUKS system on my NVMe drive is not detected.
Installing on my PCIe SSD with SATA mode does not work. I starts after some delay, but the Grub menu is not visible. The screen is black for a few seconds.
Installing on my PCIe SSD with NVMe mode does not work. No Grub menu. The screen is gray for a few seconds.

I could install my Ubuntu on a SATA SSD, but that is not why I bought a new computer. I could also move over to Manjaro (not tested, but I assume that works).

I have been adjusting my new Ubuntu for two weeks. It is in a LUKS ext4 partition and perfectly fine, but I can no longer use it because I can not make Grub to detect it anymore. I can chroot into it, but that fails because there is not tutorial that uses both EFI and LUKS. So I can not try to install Grub from my new Ubuntu.

---

### Post by TheFu on 2020-08-12
Posted for lurkers, since the OP has rejected using LVM.

I'm running EFI + LUKS + LVM just fine.  A working encrypted storage layout:
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

The layout in that link was started with a default install, the "root" LV was **lvreduce**d, then other LVs were added as desired **lvcreate** and mounted using the **sudoedit /etc/fstab**.  The 16.04 installer always allocated the root LV to the entire disk.  With 20.04, the installer seems to use 200GB for the only LV created, if there is extra storage, or in the "do something else" setup, we can manually size the PV, VG, and LVs.

Oldfred has a few posts here on getting Ubuntu UEFI installed on multiple disks.  Seems the BIOS settings only want 1 /boot/efi/ directory on any connected disks, so tricking it is required.  If any OS on the system uses UEFI for boot, then all of them should to avoid BIOS resetting stuff.  Was in the BIOS for one of my systems and saw settings that provided these boot options:
[LIST]
[*]UEFI-only
[*]BIOS-only
[*]UEFI-preferred, Legacy BIOS fallback
[*]Legacy BIOS-preferred, UEFI fallback
[/LIST]
On that system, I'm using Legacy BIOS boot only. It has been migrated forward since around 2012 when UEFI boot was new and had lots of unsolved problems on Linux.

---

### Post by jhnur on 2020-08-13
TheFu, I have encountered a serious problem with Grub. The only solution seems to be to install Ubuntu on a SATA SSD, which would be a terrible solution because my computer is for organizing my files and sometimes I run scripts on thousands of files which could take half an hour.

As you can read in #7 and #10, I started to use the "whole disk" from the installer with LVM.
I have done many more tests, with all the EFI and Grub/boot partitions removed from all SSDs, so nothing gets in the way.

My conclusion:
Grub is not up to date. It does not work on my computer (AMD Ryzen 5 3600 + Gigabyte B550M Aorus Pro) when installing Ubuntu on a PCIe SDD (either NVMe or SATA mode).
The EFI and LUKS and LVM are not part of the problem, since a "whole disk" install without LUKS does not show the Grub menu either. I tried that a few times.

Everything works fine with a SATA SSD.

Manjaro linux **does** show the Grub/boot menu when installed on a PCIe SSD (SATA mode) without LUKS. 
Sadly, a Ubuntu partition with LUKS on the other PCIe SDD is not recogned and can not be started.
When I try Manjaro linux with LUKS, then Grub is inside the LUKS partition (that's a bad choice) and the password is requested before Grubs starts. However, when I type the password, then nothing happens.

---

