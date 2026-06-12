---
title: "Transfer Ubuntu to a new hard disk"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2011-09-07
I currently have a 1TB hard disk with Windows on it. I would like to keep my installation of Windows if possible, but I want to be able to transfer my old Ubuntu settings to the new one because my old hard disk is dying.

How can I go about this?

---

### Post by papibe on 2011-09-07
I can think of a couple of options:

[Clonezilla]("http://clonezilla.org/") is a live CD, text mode, that can be use to clone a complete hard drive or just partitions.

But I would recommend using Gparted Live (or Ubuntu Live). Gparted can copy partitions, so you can copy your Ubuntu partitions to the new hard drive.

Once they are copied, you would need to upgrade grub, so that it takes notice of the new hard drive. I don't know how to do that part.

Hopefully, someone else can add information on that part.

Hope it helps,
Regards.

---

### Post by oldfred on 2011-09-07
Many try to copy the entire partition and you can do that. But you have to edit fstab with new UUID and reinstall grub2's boot loader

You can also do a clean install and just copy /hoome over. If you have a few system wide settings in /etc you may want to review them and back them up but do not just restore them. If you have installed a lot of applications you can make a list from the old install and the new install will add them from the list.

Use Windows MMC to shrink the windows partition. Most Windows installus use all 4 primary partitions, so do you have a primary  partition to create as the extended partition for the logical partition of /, swap and /home? You also should have a shared NTFS partition for any data you want in both Windows and Ubuntu. 

My backup procedure is to have all my data and if necessary do a clean install. So this is what I backup.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

---

