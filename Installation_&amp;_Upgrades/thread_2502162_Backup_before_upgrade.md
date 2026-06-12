---
title: "Backup before upgrade"
date: 2024-11-04
forum: Installation &amp; Upgrades
---

### Post by kalvaro on 2024-11-04
I have a Lenovo laptop running Ubuntu 22.04 LTS that I'd like to upgrade to 24.04 LTS. This model does not have official Linux support and many features have never worked. Laptop has UEFI secure boot, encrypted Ext4 disk, hybrid graphics  (AMD+Nvidia) and this same year a kernel upgrade broke multi-monitor  support, which I could only restore many days afterwards when I figured out how to restore the  old kernel.

I'm very scared because it's a work laptop and I work (very) remotely. If something breaks, I can't really get assistance or a replacement, and if I install from scratch I'll need to go through company enrolment process again and potentially lose an unknown number of work days.

I make regular backup copies into an external SSD but only for my files in home directory. Is there a program or utility I can use to make a full system backup to be able to revert all changes should the upgrade fail? It needs to be easy to use (i.e. a menu with preselected options as opposed to typing commands and partition IDs). I can get a second external USB disk for this purpose.

---

### Post by grahammechanical on 2024-11-04
Have you heard of Ubuntu Pro? You can extend the life support for Ubuntu 22.04 LTS by another 5 years and it is free for the single users with up to 5 machines.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

> 30-day trial for enterprises. Always free for personal use.

[https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe)

> Free, personal subscription for 5 machines for you or any business you own, or 50 machines for active [Ubuntu Community members]("https://ubuntu.com/community/membership"). If you need phone support or need to cover more than 5 machines, please select "My organisation"

Alternatively, dual boot with Ubuntu 24.04 LTS. Have a separate partition for all your data or a second drive for your data.

Or, checkout Backups - Also called Deja Dup. It should be installed by default. Open the Ubuntu Desktop Guide (HELP) and find the section on Backing Up .

> *Backing up* your files simply means making a copy of them for safekeeping. This is done in case the original files become unusable due to loss or corruption. These copies can be used to restore the original data in the event of loss. Copies should be stored on a different device from the original files. For example, you may use a USB drive, an external hard drive, a CD/DVD, or an off-site service.

> The easiest way of backing up your files and settings is to let a backup application manage the backup process for you. A number of different backup applications are available, for example *Déjà Dup*.
[COLOR=#000000][FONT=sans-serif]The help for your chosen backup application will walk you through setting your preferences for the backup, as well as how to restore your data.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]

Regards

[/FONT][/COLOR]

---

### Post by makitso on 2024-11-04
> **kalvaro said:**
> I make regular backup copies into an external SSD but only for my files in home directory. Is there a program or utility I can use to make a full system backup to be able to revert all changes should the upgrade fail? It needs to be easy to use (i.e. a menu with preselected options as opposed to typing commands and partition IDs). I can get a second external USB disk for this purpose.         I have a simular situation.  I use the timeshift application (for / ) and a custom set of rsync commands for my home partition.  And yes I have this machine on Ubuntu Pro.

---

### Post by grahammechanical on 2024-11-04
> I can use to make a full system backup to be able to revert all changes  should the upgrade fail?

To have that function we must use a different file system such as the B-Tree file system (BTRFS). That system allows us to take a snapshot of the operating system that we can revert back to.

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Regards

---

### Post by oldfred on 2024-11-04
I like to have multiple bootable systems.
Even with one system, you can do a full install on your external SSD and make it bootable if you have an ESP - efi system partition on external drive. Installer defaults to "first" drive, usually internal drive. 

I used to have multiple flash drives with full installs even those larger ones mostly for data. I found external SSD so much faster (newer flash drives are not as slow as my older ones), that now I primarily use external SSD with Windows laptop. It really is just a copy/backup of my desktop Kubuntu install. I still like to have a few flash drives with installs.

My first external SSD was my desktop's M.2 drive in a USB adapter. Wanted a larger drive in desktop and needed a way to use M.2 drive.

---

