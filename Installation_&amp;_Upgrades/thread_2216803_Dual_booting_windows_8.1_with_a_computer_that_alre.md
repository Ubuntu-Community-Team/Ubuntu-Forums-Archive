---
title: "Dual booting windows 8.1 with a computer that already has Ubuntu 13.10 installed"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by briangroat93 on 2014-04-14
Hey everyone, I've been looking online to find a good tutorial to dual boot Windows 8.1 onto a Toshiba Satellite that already has Ubuntu 13.10 and Kali Linux installed on it, and all I've been able to find were tutorials that were about installing Ubuntu onto a computer that already had Windows 8.1 installed. And doing a search on here all I found was guides on setting up a virtualbox, which I'm not really interested in, I'd rather have a proper dual boot. Is that even possible? I appreciate all of your help in advance.

---

### Post by ajgreeny on 2014-04-14
Yes, it's possible but potentially a bit more difficult than installing ubuntu after windows has been installed.

How exactly to go forward will depend on your partition setup, so using gparted either from a live system, or by installing to your current ubuntu installation, let's see a screenshot of the gparted window.

---

### Post by briangroat93 on 2014-04-14
Here's my screenshot from gparted[ATTACH=CONFIG]252057[/ATTACH]

---

### Post by oldfred on 2014-04-14
It looks like you have BIOS booting with MBR partitions. So you have to install Windows to a primary NTFS formatted partition with the boot flag.

But I have seen Windows corrupt extended partitions when it is installed to a primary that is after the extended and sometimes it just rewrites partition table and leaves out Linux partition in an extended partition. You need to fully document partitions by sector so you know where they are on drive.

You need to have good backups, and you do have a lot of data in sda6. Did you encrypt /home as gparted does not show swap, but that is normal with /home encrypted.

I would shrink sda6, move it to the right on drive, move extended start right so then you have unallocated right after sda1. Then you can create the NTFS primary after sda1. It will probably be sda3, but order on drive is not important. 
I do not like moving partitions around as I suggest. Any power failure or other interruption will totally corrupt system, so good backups are vital. I would not queue steps in gparted but run each to completion to make sure it has worked.
You have to use gparted from live installer, so all partitions are unmounted. Since swap is encrypted it should not mount it, but often live systems mount swap to speed up things. But with gparted moving partitions around all partitions must be unmounted (no little key symbols).

After moving partitions around and creating NTFS, run this before installing Windows,  just in case it does something to partition table. You will have to reinstall grub  and with Windows 8 make sure fast boot or always on hibernation is off.

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

