---
title: "Set up multiple OS partitions, that both point to the same home partition, in LUKS"
date: 2018-03-23
forum: Installation &amp; Upgrades
---

### Post by roma24ster on 2018-03-23
[COLOR=#111111][FONT=Ubuntu]Encryptfs has been removed from 18.04, in favour of full disk encryption (LUKS). See [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1756613") for confirmation. This means that my current set up of having an encrypted home directory on a different partition is harder to replicate.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Basically, I like to have two OS partitions (sdb5 and sdb6), that both have their encrypted /home directories on a different partition (sdb8), because it makes it easier to distro-hop. All of this will have to be in a full disk encrypted LUKS container now I think.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
How can I set this up when installing ubuntu from a livecd?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
This is my[ set up]("https://i.stack.imgur.com/GDRy7.png") at the moment. I would like to get this within a LUKS container.[/FONT][/COLOR]

---

### Post by ubfan1 on 2018-03-23
Sounds like you'd be interested in fscrypt. See [https://www.kernel.org/doc/html/latest/filesystems/fscrypt.html](https://www.kernel.org/doc/html/latest/filesystems/fscrypt.html)
File level encryption, with improved efficiency over ecryptfs.

---

### Post by Herman on 2018-03-26
If you can create the encrypted partition first and create  your logical volumes using the Live CD before you start the installer, the Ubuntu installer will offer you the option to install into logical volumes if you choose 'something else' at the partitioning stage of the installation.

Here's a screencap,
[IMG]http://members.iinet.net/~herman546/Screenshot%20from%202014-02-22%2010_12_39.png[/IMG]

The method (for one OS) is explained pretty well in the following linked web page along with examples of all the commands you'll need, [Encrypted Custom Install]("https://askubuntu.com/questions/918021/encrypted-custom-install") - ask ubuntu.
Just create an extra lv for your other os's /
Also you are planning to dual or multi boot, make sure you leave room for a separate /boot for each OS outside the encrypted volume as they do not like sharing the same /boot. That can get messy real quick.
We don't need a separate /boot just for lvm these days as GRUB has an lvm module now. 
I don't know if there's a luks module for GRUB yet, I haven't heard of one yet so I think we still need separate /boot partitions outside the encrypted area.
You'll need to be able to unlock your encrypted partition again before starting the installer in the other OS too. (Install lvm2 if it doesn't come with it by default).

It has been a while since I took the time to try this sort of thing but it should be quite do-able.

Updates:
1. I was wrong, GRUB does have an luks.mod, but I'm not sure what it's for and what its capabilities are, [https://www.linux.org/threads/understanding-the-various-grub-modules.11142/](https://www.linux.org/threads/understanding-the-various-grub-modules.11142/)
2. According to this web page, [https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#Encrypted_boot_partition_.28GRUB.29](https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#Encrypted_boot_partition_.28GRUB.29) , we can actually have an encrypted /boot for LUKS but not for LVM2.
I'm sure GRUB works fine with LVM2 now, I have an installation I made back in 2016 recorded step by step where I did that. Maybe we don't need the separate /boot at all. I might try it for fun when I get time.

---

