---
title: "Installing Multiple Encrypted Distros on Single USB Flash Drive"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by james40 on 2015-01-14
Hi all,

Basically I'm trying to install LXDE and Kali Linux on a single bootable flash drive but I am not quite sure how to get this to work. My thoughts on the current configuration is as follows:

/dev/sdb1 FAT32 - Storage space to swap files from Linux to Windows
/dev/sdb2 /boot - Boot partition for LXDE
/dev/sdb3 /boot - Boot partition for Kali
/dev/sdb4 Extended - Extended partition for Encrypted LVMs
Extended: /dev/sdb5 crypt-luks - Encrypted Swap Space
Extended: /dev/sdb6 crypt-luks - Encrypted LXDE /
New Primary: /dev/sdb7 crypt-luks - Encrypted Kali /

My thoughts are to share the encrypted swap space between the two distributions but I'm not quite sure how to do that during the install of the second distribution. Am I also correct to do the boot partitions in the way I am planning? Is there a better way to do this other than using two separate flash drives?

I know using encryption is a pain but its company policy and I wont get approval to do this unless I can ensure all information is encrypted. 

Thanks for your help in advanced

---

### Post by Bucky Ball on 2015-01-14
I can't help with much, but a couple of points. Why FAT32? It has limitations. NTFS better.

As for the shared /swap. Install the first OS as you would, assigning a /swap partition. During the second install, partition manually, mark the existing /swap to not be formatted but to be used. The second install will then use the existing /swap. You don't need to create another. If the second install sees one there and it is available for use, it will use it. I have three installs and they all use the same /swap. 

Not much help, sorry, but a start. ;)

---

### Post by sudodus on 2015-01-15
I think it is complicated enough to have one encrypted system in a pendrive, and I would recommend to have two separate pendrives rather than to have two systems in one single pendrive, if you want encryption.

Also, I have noticed that with encrypted swap settings, an installed system in a pendrive can hi-jack existing swap partitions in an internal drive and make them encrypted too and change them which destroys them for the installed system (which they belong to). Afterwards I have had to run

```
sudo mkswap -U enter-the-uuid-from-the-installed-system-swap-line-in-fstab-here /dev/sdxy
```

where x is the drive letter and y is the partition number of the internal swap partition.

Maybe you should avoid swap in the pendrive or at least you should make sure it will not use any internal swap partition. This is no problem if there is no internal linux swap, but how do you know, when you borrow a computer to run your pendrive?

---

