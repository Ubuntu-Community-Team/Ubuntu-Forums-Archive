---
title: "partition windows not found after try encrypted disk ubuntu"
date: 2021-06-23
forum: Installation &amp; Upgrades
---

### Post by ancien88 on 2021-06-23
hi,
in my computer i have to os linux and windows, i try to install ubuntu at linux partition, i selected use encrypted disk , i  thought that it will encrypt just linux partition, but when  i finish installation i can't find partition windows, and when i want to try to access to other partition in  computer with ubuntu, i find just one partiont with all size hard disk , it's ask for password ,when i confirm it , all the partition disappear,
before booting , i had 4 partition
-a partition with OS windows not encrypted disk
-a partion linux where i want to install ubuntu
-2 patitions  for data encrypted with windows10
thanks for helping , i'm developer java if some one want a help

---

### Post by oldfred on 2021-06-23
Stop using system. And only use live installer that does not mount swap as that also overwrites more data.

If you chose the automatic encrypted install which uses LVM, you may have erased the entire drive. Red warning says drive will be erased.
Best way to recover is to totally reinstall & restore from backups. There will be no way to recover all data as at least some was overwritten with new install.

Post this from live installer.
sudo parted -l

---

### Post by TheFu on 2021-06-23
To my knowledge, there is NO WAY to select encryption during any Ubuntu installation and not wipe the entire drive. Mixed use drive and partition setups are just too complex.

I have very bad news.

The Ubuntu Installer, when encrypt whole drive and use LVM is selected ... well, it wipes the whole disk, creates partitions, encrypts the 3rd primary partition, then lays down LVM volumes (PVs, VGs, LVs) inside the encrypted LUKS volume and performs an install.
I don't have a dual boot system to see exactly what that says, but I just grabbed some images during a 21.04 Desktop (Gnome3) install.
Three Choices displayed were:
[LIST]
[*]None
[*]Use LVM with the new Ubuntu Installation
[*]Erase Disk and use ZFS
[/LIST]
> Encrypt the new Ubuntu installation for security (You will choose a security key in the next step.)
Encryption was only offered if I chose to use LVM. It was a checkbox. On Ubuntu, LVM + LUKs are connected.

On the screen after those options are displayed, it says:
[LIST]
[*]Erase disk and install Ubuntu ... Advanced Features .... LVM and encryption selected
[*]Something else
[/LIST]
The first was pre-selected because of the prior selections.
Next, there was another warning with "Go Back" or "Continue" options.
> [B]Write the changes to disks?
[/B]If you continue, the changes listed below will be written to the disks......
WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.
Go Back      Continue

Anything on the disk before the install is gone.

All those times people online said to > backup anything you don't want to lose?
Well, this is the time for those backups.

BTW, whenever posting for help here, 2 things need to be included to get the best help.
[LIST]
[*]The Ubuntu Release - say 20.04
[*]The Ubuntu DE or non-GUI Server - say Gnome3 or Mate or KDE or LXqt or XFCE or .... "Server, no GUI"
[/LIST]
Things, especially around the installation, are very different for each of those.  For example, I did a 21.04 install by mistake. That's a non-LTS release supported only for the rest of this year.  In November, I have to upgrade to 21.10 to keep on a supported release.  The current, most recent LTS release is 20.04. It has 5 yrs of support for the Server and Gnome3 desktop, while most other DE flavors get 3 yrs only.  

I'm sorry about the data loss. Everyone here has lost plenty of data over the decades.  I have. Thankfully, nothing recent, but I've had backup-religion for a long time and testing the restore of backups happens a few times each year.

Time to get those backups working.

---

