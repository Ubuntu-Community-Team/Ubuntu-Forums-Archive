---
title: "How to reinstall ubuntu on encrypted lvm partition without overwriting home partition"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by robpower on 2008-06-09
Hi to all!
I tried to search before posting, but I couldn't find any solution; here is my problem.
I have a Kubuntu installation (the flavuor isn't important) with full-drive encryption.
So I have 2 physicalpartition on the hd: a small "/boot" one (unencrypted) and a big one fully encrypted, which contains a LVM partition (Logical Volume Manager).
The LVM contains 5 logical partition: root, home, var, tmp and swap.
The is the following: due to complex problem i need to do a fresh (K)Ubuntu install, using the same "structure" and without overrwriting the home partition.
So i want to know how I could do.
Till now I tried to install from alternate cd, but when I manually set up the partitions, it asks me to overwrite the old encrypted and I couldn't find an option to simply open the old one. (I selected formatting: No)
Any help would be appreciated and any question about details is welcome.
Thanks in advance,
Rob

---

### Post by robpower on 2008-06-10
Any help?
In the meanwhile I tried to use the "repair an existing system" option, from alternate CD boot options; though it regnognizes the crypted device (/dev/sda5) and mounts it under /dev/mapper/sda5_crypt (i think), it seems that couldn't handle the LVM volume: logical disks don't appear in the "root partition selection for recovery".
Thanks again to anyone who could help.

---

### Post by ttwaro on 2009-04-19
I see that there hasn't been a reply to his question. I reinstall Ubuntu twice a year (or more) when new releases come out. I do this to keep up with any changes since I recommend and install Ubuntu on other peoples machines. I have a separate /home partition that I don't format when I install on top of the previous release. For the Jaunty release (9.04) I want to use LVM with Full Disk Encryption on my laptop. I've done a full backup of my /home directory for this time but in the future I would like to just remount my old /home directory when installing 9.10 and beyond.

So the question is still out there; is it possible to reinstall Ubuntu on top of itself using LVM with encryption and preserve the /home directory???

---

### Post by warjowuch on 2009-04-24
I also am interested in this option, is it possible??

Or would it be like "backup to external HD -> install and re-encrypt -> put backup back in place"?

---

### Post by mikereed on 2009-05-13
I had a similar problem a while back but have only just posted the solution. It is not exactly the same as your problem but I hope it helps.  Here is my original thread

[http://ubuntuforums.org/showthread.php?t=1009031](http://ubuntuforums.org/showthread.php?t=1009031)

---

### Post by hastala on 2009-06-12
hi,

i guess mikereed's link got everybody into the right direction, but there's some vital part missing: finding the encrypted volume

here's what i did:

start live cd

install LVM & Cryptsetup
```
sudo apt-get install lvm2 cryptsetup
```

load kernel modules
```
sudo modprobe dm-mod
sudo modprobe dm-crypt
```

unencrypt your encrypted partition (sda5 in my case) & enter your passphrase
```
sduo cryptsetup luksOpen /dev/sda5 sda5crypt
```

find the VG
```
sudo vgscan
```

check if all your LVs are presented
```
sudo lvs
```

and there you go. now just run the live-installer's "install" function and get going.

pretty easy... i don't get why they don't include the lvm & cryptsetup into the standard installation, or even the alternate one :(

edit:
WARNING: don't use the the 9.04 (jaunty) installer as live cd. it's most likely to show sth. like:

```
sudo modprobe dm-mod dm-crypt
FATAL: Module dm_mod not found.

```

I am performing the installation with the 8.10 cd and upgrading to 9.04 online... hope that works ;)

---

### Post by Aybara on 2010-09-05
Did this work out? I need to do the same to go from a 64-bit Lucid to a 32-bit Lucid while hopefully keeping my /home partition intact.

---

### Post by Aybara on 2010-09-07
Worked out for me on 10.04. Thanks.

---

### Post by atti84it on 2011-05-05
I've found this wonderful Howto:
[http://ubuntuforums.org/showthread.php?t=1205372](http://ubuntuforums.org/showthread.php?t=1205372)

---

### Post by tuliouel on 2013-03-06
This didn't work for me. I did everything hastala told us to do and started the install procedure. It failled in just substituting the previous system. It wanted to format the whole partition. Since I have /home and / in the same encrypted lvm partition, it wouldn't wwork for me.
The solution described in one of the two links above, using the alternate install, also failed. The system was installed but, since my user directory was encrypted in /home/username/.Private using encryptfs, it failed to mount, and I didn't find a workaround yet, since no username nor any passwork seems to work, even typing the exact terms I entered during install. So I can only access a Guest account, which dosn't allow me to access any Terminal nor sudo neither any graphical interface that requires root.

---

