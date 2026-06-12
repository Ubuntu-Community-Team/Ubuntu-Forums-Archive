---
title: "Hard Disk space for Ubunto 20"
date: 2020-07-21
forum: Installation &amp; Upgrades
---

### Post by gardenair on 2020-07-21
I am using windows 10 on my laptop. I am planning to switch to Ubuntu 20 Desktop. The major software which I want to install in it is **GIMP, Inkscape**, and **Kdenlive**. Well According to the Ubuntu documentation, a minimum of 25 GB of disk space is required for a full Ubuntu installation. I am using Core I5,4 GB Ram and a 320 GB Hard Disk. If I try to create a manual partition then how much space may I allocate for / ? 

```
/boot  = 1GB
 Swap  = Double of Ram Size
/home = As per user requirement
/     = ? GB 


```

---

### Post by CatKiller on 2020-07-21
You don't need a swap partition, since Ubuntu uses a swap file these days.

You don't need a boot partition. You'll have an EFI System Partition, but that's shared with Windows.

You don't really need a home partition. It's useful sometimes, particularly if it's actually a separate disk, but when you've only got part of a small disk to work with anyway it's not really worth the effort. If you did want to use a home partition, the balance between applications you're going to install and data you're going to generate isn't something that we can estimate for you. 

Just shrink down your Windows partition as much as you think you can get away with and then point the installer at the free space.

---

### Post by crip720 on 2020-07-21
Don't need swap partition anymore, so you can forget about it. / should be at least 20GBs to maybe 40GBs(a bit larger if you want), /home is the rest.  Can also just have whole drive as /root, but having /home also is nice.  /boot(EFI) formated to vfat, the others ext4 or your choice.

---

### Post by TheFu on 2020-07-21
There are many different opinions about how to best setup storage.  

Some people like the 1 huge partition because it is easier.  That's fine for someone new.  

As you learn more, you might want the typical /home/, /, swap, and perhaps /var/ setup. There are reasons.  

Then there are server admins who don't want a foolish end-user to be able to bring his servers down just by filling all the space, so she takes steps to prevent any non-admin from having that ability by setting up specific partitions sizes, with specific mount options to better control security.

I'm somewhere in the middle, but that isn't important. I typically would have /, /var/, /home/, /stuff and a swap partition (ok, not really partitions because I use LVM which provides logical volumes rather than partitions).  LVM is one of those things that you don't know you need it until 1-2 yrs later and by that point it is already too late. Alas, LVM is usually too complex for most people, including some long-time Linux users.  Just know that volume management exists and partitions aren't the only way to split out storage management.

For the first year or so, I'd setup 2 partitions - one for the OS, boot, and swap file AND the other for /home/.  30G should be sufficient for the OS, boot, applications and a 4.1G swap file.  For /home/, use whatever you think you'll need - if you are doing 4K video editing, you'll probably want at least 500G.  100G for 1080 video editing and 50G for 720p editing.  Images can become huge areas too. I'm using 80G for about 29K images in a gallery, but those are all post-processed.  I don't keep the raw files around.

Which file system to use is probably something a Windows user never considered before.  On Ubuntu, the safe answer is ext4, for everything except flash (sdhc/usb) storage.  Currently, Windows cannot access ext4 storage, which I consider a good thing.  Linux systems can access NTFS though it should only be used for data.  NTFS cannot be used for /home/ or for the OS.  

[https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is a primer "Linux for Windows Users"

---

### Post by GhX6GZMB on 2020-07-21
If you're switching 100% to (x)ubuntu, my suggestion would be:
/: 30 GB
[SWAP]: 6GB
/home: the rest

This is the simplest setup. Concerning swap file vs. swap partition: I've not been able to get a swap file to work, but a swap partition is painless. Probably my incompetence.

Having / on a separate partition is nice when updating the system.

---

### Post by TheFu on 2020-07-21
A swapfile is just a few steps.
[LIST]
[*]Create a file of the size you want.  I'd use dd for that, but there are other ways.
```
sudo fallocate -l 4.1G /swapfile
```
[*]Lay down a "swap" format on it - mkswap
```
sudo mkswap /swapfile
```
[*]Change the permissions to prevent evil from happening
```
sudo chown root:root /swapfile; sudo chmod 600 /swapfile
```
[*]Add the swapfile to the /etc/fstab file
```
/swapfile none swap sw 0 0
```
[*]Turn the swap on
```
sudo swapon -a
```
[/LIST]

Easy Peasey.
It is best to create the swapfile BEFORE hardly any files are on the file system being used so it is contiguous.

---

### Post by C.S.Cameron on 2020-07-22
It is most efficient to just have a EFI boot partition and a root partition, (/).
20.04 creates a swapfile, it is a little small for hibernation but very easy to enlarge.
A separate root and /home partition takes up space they may never use.
It is easy to backup and restore home directory if you choose to do a fresh install when upgrading.

---

### Post by GhX6GZMB on 2020-07-22
> **TheFu said:**
> 
Easy Peasey.
It is best to create the swapfile BEFORE hardly any files are on the file system being used so it is contiguous.

Yes, creating a swapfile is no problem. The issue comes when you want to use it.
I want to have hibernate on my system, and have never been able to get this to work with a swapfile. With a swap partition it works perfectly.

---

### Post by GhX6GZMB on 2020-07-22
> **C.S.Cameron said:**
> It is most efficient to just have a EFI boot partition and a root partition, (/).

Efficient in terms of what?
My experience is, that if you're a new user, it makes a lot of sense to separate system files and user documents. Playing around with settings, program installations and stuff, it's much easier if you don't have to worry about your documents all the time. A system rollback that does not touch /home is more efficient to me.

But that's just my way of working. As a newbie, I feel confident when I can do a system rollback any time.

---

### Post by C.S.Cameron on 2020-07-24
> **ml9104 said:**
> Efficient in terms of what?

In terms that it is hard for a newbie to predict the amount of space they will need for / and for /home. They may guess wrong and quickly run out of space on either. This then requires expanding and contracting partitions. If home and root are on the same partition there is never a need to adjust partition size.

> **ml9104 said:**
> My experience is, that if you're a new user, it makes a lot of sense to separate system files and user documents.

User documents are already in a separate directory from system files it is called home. The home directory is easy to back up or move to a new upgrade or move to a rollback, using Rsync or Grsync. In fourteen years I have never had to do a rollback and as often as not, I do a version upgrade rather than a fresh install.

The nice thing about Ubuntu is that we have a choice.

---

### Post by TheFu on 2020-07-24
> **C.S.Cameron said:**
> In terms that it is hard for a newbie to predict the amount of space they will need for / and for /home. They may guess wrong and quickly run out of space on either. This then requires expanding and contracting partitions. If home and root are on the same partition there is never a need to adjust partition size.



User documents are already in a separate directory from system files it is called home. The home directory is easy to back up or move to a new upgrade or move to a rollback, using Rsync or Grsync. In fourteen years I have never had to do a rollback and as often as not, I do a version upgrade rather than a fresh install.

The nice thing about Ubuntu is that we have a choice.

The main reason for keeping /home on a different storage area - partition, LV, file system - is so the OS can be reloaded and not touch that area.
For a system that has limited storage for Linux, say less than 50G total, then getting the sizes wrong can be a huge problem. However, if the system has 100G or more available, just allocate 25-30G for the OS, 4.1G for swap and the rest for /home/;  Keeping the OS separate (and swap separate from that), may never matter, but when it does matter, it really is great to have the flexibility.  Without that flexibility, a 15 minute OS reload becomes a multi-hour ordeal, risking all the files, for most new users.

We've all "accidentally" deleted files we didn't want to lose.  I've accidentally installed a Linux over the wrong partition a few decades ago when I was new.  It is easy to get in a hurry and not triple-check the partitions being used.  Perhaps that is a necessary failure to force people into learning the whole drive/partition details?  Wish it wasn't, but we all have failures. Over time, we setup things to reduce/limit those failures. At least I do. Then we each try to share our experiences so that nobody else need go through the same problems.  

Some people are lucky. They've never had the same failures as others for some reason.

---

### Post by C.S.Cameron on 2020-07-24
To enable Hibernation on a swapfile:

- Increase swap file size to match RAM size up to 8GB per above as required.

- Edit /etc/default/grub to add resume location and offset to grub.cfg:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX resume_offset=XXXXX"`

- Use UUID from root.

- Use offset from sudo filefrag -v /swapfile |grep " 0:"| awk '{print $4}' 

- Update GRUB

    `sudo update-grub`

- Test hibernation

    `sudo systemctl hibernate`

**A hibernate button can be added using gnome extensions.**

**NOTES:**

- There is a slight possibility of getting holes in a swapfile when creating it with fallocate. /var/log/syslog can be searched for the phrase `swapon: swapfile has holes` to ensure there will be no data loss.

---

### Post by gardenair on 2020-07-24
Thanks, everybody for the detailed replies. Well instead to make swap file, I think swap partition will be best. Though currently  I  have  320 GB Hard Disk but will buy a new 1TB Hard Disk. The only thing is the said software graphic and video editing software. If I use 30 GB for OS  it is quite sufficient for updating any software?  Instead, to use Hibernation I keep my windows in sleep mode especially when I  go rest.
What about /boot partition?


```
/   30 GB
/Swap  4 GB
/boot   ?
/home  (All Free space)
```

Any technical opinion /suggestion  about /boot  partition

---

### Post by GhX6GZMB on 2020-07-24
> **gardenair said:**
> 

```
/   30 GB
/Swap  4 GB
/boot   ?
/home  (All Free space)
```

Any technical opinion /suggestion  about /boot  partition

Hands off. The installer will do that for you.

---

### Post by TheFu on 2020-07-24
/boot/ only needs to be separate if you use LVM, ZFS, or encryption.  For a normal UEFI install, it doesn't need to be a separate partition from /.  I use LVM almost always and LVM+encryption on portable devices, so /boot/ sizing is important.  It may not be in your situation.

Assuming you are using ZFS, LVM, or encryption and having a separate boot makes since, then /boot should be whatever size lets you have however many old kernels you think you need, plus a few more to allow for system version upgrades.  3 is a common number of kernels, to 5 is my target.  I've run into trouble with only 300MB on /boot/, so I use at least 500MB now and 700MB is more comfortable. In the age of 500GB HDDs, does 200MB really matter?

TL;DR
[LIST]
[*]Avoid /boot unless necessary
[*]500-700MB, if necessary
[/LIST]

---

### Post by pbear42 on 2020-07-24
> **gardenair said:**
> If I use 30 GB for OS  it is quite sufficient for updating any software?
The big unknown there is Snaps (the Ubuntu version of portable apps).  If you're going to use many of those, you'll need more room.  With a 1 TB drive, I'd say go with 40 GB for the root/system partition.  That's still only something like 5% of the drive (bear in mind, a 1 TB drive = 930 GiB, and the latter is what most folks mean by GB).

---

### Post by C.S.Cameron on 2020-07-24
> **TheFu said:**
> /boot/ only needs to be separate if you use LVM, ZFS, or encryption.  For a normal UEFI install, it doesn't need to be a separate partition from /.  I use LVM almost always and LVM+encryption on portable devices, so /boot/ sizing is important.  It may not be in your situation.


One of the reasons that I have not been using a separate /home partition with 20.04 is that the installer's Advanced Features / Use LVM... /  Encrypt the new... option does not seem to allow a separate /home partition. The encrypted root / partition can not be shrunk. The swap partition that is created is too small for hibernation and like the boot partition, it can not be enlarged, so a swapfile must be created.

Paddy Landau's full disk encryption works great for me on 18.04 but not on 20.04.

Please explain how you manage to encrypt the disk and still choose the size of Boot and /home partitions? I have been looking for a method for quite a while.

---

### Post by gardenair on 2020-07-25
Again thanks for the guidance. Well as you have mentioned that  Ubuntu  will do all .There is no need to create a separate /boot partition. I agree with it but if you study an  old linux books  there they suggest to create a separate /boot partition.Sure with a latest  Ubuntu (for a home user) there will be no need to create /boot partition.  I am a Windows user and**_ I want to save my system from out side world ( especially hackers and Viruses)_**. *In that case Linux is the best Operating system* i.e secure and reliable. Well  LVM, or ZFS is a new thing for me. I will study it first and then can write.
So as to your technical suggestions I may install Ubuntu and let it to do all for me :) 

I am very very much  thankful for all of you for  the guidance and experiences you share .

---

### Post by TheFu on 2020-07-25
> **C.S.Cameron said:**
> One of the reasons that I have not been using a separate /home partition with 20.04 is that the installer's Advanced Features / Use LVM... /  Encrypt the new... option does not seem to allow a separate /home partition. The encrypted root / partition can not be shrunk. The swap partition that is created is too small for hibernation and like the boot partition, it can not be enlarged, so a swapfile must be created.

Paddy Landau's full disk encryption works great for me on 18.04 but not on 20.04.

Please explain how you manage to encrypt the disk and still choose the size of Boot and /home partitions? I have been looking for a method for quite a while.

I've been using encryption + LVM for years now.  **The installer defaults suck.**  It isn't worth my time to try and get them correct during the install (I tried a few times), so I just fix everything post-install.  That's the power of LVM.  

Post-install, post-first full-upgrade patch, I reduce the size of the "root" LV. Reducing an LV is a little bit of a hassle. Creating or increasing the size of an LV is trivial.  Here's my storage layout on a physical system with UEFI boot, encryption and LVM:
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)  sda3_crypt is the LUKS container that holds all the LVs. This is a real system.

Reducing "root" LV has to be performed from a Live-Boot environment.  Use cryptsetup to open the LUKS container.  Then use LVM commands to activate the VG, and normal LV commands to resize - Bob's your uncle.  From boot to complete takes about 5-10 minutes post-install.

For someone really new to LVM, this could be overwhelming. For someone confident in their LVM skills, it is pretty easy.  Since LVs are mounted by a path that doesn't change in the fstab, we don't need to screw with that at all, just resize as we like.

Anyone using LVM should know - DO NOT ALLOCATE ALL THE PV STORAGE TO LVs.  If you do, you've just prevented the main reason to bother with LVM - flexibility.  I try to allocate only the storage needed for the next 3-6 months. Adding more storage to an LV is 5 seconds; easily performed on a running, active, mounted, LV. Reducing an LV is a slight hassle since it can't be mounted at the time.

Through LVM, I've added storage as a new HDD to a running system, added storage to existing LVs. No reboot needed. All the commands:
[https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)
Without LVM, that wouldn't have been possible.


gardenair, I wouldn't suggest that you use LVM until you have at least a year of Linux Admin experience. The extra abstractions involved can be confusing.

---

### Post by ActionParsnip on 2020-07-25
I'd make a 30Gb / and use the rest for /home. Should give plenty of room

---

### Post by GhX6GZMB on 2020-07-25
> **TheFu said:**
> I've been using encryption + LVM for years now.  **The installer defaults suck.**  It isn't worth my time to try and get them correct during the install (I tried a few times), so I just fix everything post-install.  That's the power of LVM.  

Post-install, post-first full-upgrade patch, I reduce the size of the "root" LV. Reducing an LV is a little bit of a hassle. Creating or increasing the size of an LV is trivial.  Here's my storage layout on a physical system with UEFI boot, encryption and LVM:
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)  sda3_crypt is the LUKS container that holds all the LVs. This is a real system.

Reducing "root" LV has to be performed from a Live-Boot environment.  Use cryptsetup to open the LUKS container.  Then use LVM commands to activate the VG, and normal LV commands to resize - Bob's your uncle.  From boot to complete takes about 5-10 minutes post-install.

For someone really new to LVM, this could be overwhelming. For someone confident in their LVM skills, it is pretty easy.  Since LVs are mounted by a path that doesn't change in the fstab, we don't need to screw with that at all, just resize as we like.

Anyone using LVM should know - DO NOT ALLOCATE ALL THE PV STORAGE TO LVs.  If you do, you've just prevented the main reason to bother with LVM - flexibility.  I try to allocate only the storage needed for the next 3-6 months. Adding more storage to an LV is 5 seconds; easily performed on a running, active, mounted, LV. Reducing an LV is a slight hassle since it can't be mounted at the time.

Through LVM, I've added storage as a new HDD to a running system, added storage to existing LVs. No reboot needed. All the commands:
[https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156](https://ubuntuforums.org/showthread.php?t=2444855&p=13963156#post13963156)
Without LVM, that wouldn't have been possible.


gardenair, I wouldn't suggest that you use LVM until you have at least a year of Linux Admin experience. The extra abstractions involved can be confusing.

@TheFu: I have great respect for your knowledge and experience, but perhaps you should rein it in a bit in your answers? The OP asked a somewhat simple question about partitioning.
And now he's being carpet bombed with information about other filesystems, encryption, LUKS and whatever, something he might need in a year or two.
It's a good idea considering just what your audience is when writing a reply.

Please do not take this as a negative response, it's quite the opposite. It's a constructive and positive suggestion to make your answers even more valuable.

---

