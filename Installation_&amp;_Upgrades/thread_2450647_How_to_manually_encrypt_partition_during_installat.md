---
title: "How to manually encrypt partition during installation in Kubuntu?"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by peter1897 on 2020-09-18
I am trying to install Kubuntu 20 and on Disk Setup i select Manual, then i create one boot partition and one root partition. For the root partition i then select 'physical volume for encryption', but nothing happens. It doesn't ask me to set a password or anything. If i click 'Install Now' also nothing happens.

---

### Post by peter1897 on 2020-09-19
This installer is problematic. If i create boot, home and root partitions and try to encrypt home and root partitions the installer crashes every time.

---

### Post by tapucosmo on 2020-09-19
See [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) for info on how to manually set up LUKS partitions before installing the OS.

---

### Post by peter1897 on 2020-09-20
> **tapucosmo said:**
> See [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) for info on how to manually set up LUKS partitions before installing the OS.

I tried to follow the guide but faced problem when i tried to encrypt the partition for my root system. This is what i did: 
I booted Kubuntu from live usb and choose 'Try Kubuntu'. Then i used GParted to crate one partition for boot - /deb/sdb/sdb1, and one partition for root - /deb/sdb/sdb2. These are my partitions:

```
kubuntu@kubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   1.7G  1 loop /rofs
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0    50M  0 part 
&#9500;&#9472;sda2   8:2    0  48.3G  0 part 
&#9500;&#9472;sda3   8:3    0   505M  0 part 
&#9492;&#9472;sda4   8:4    0    63G  0 part 
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   500M  0 part 
&#9500;&#9472;sdb2   8:18   0  49.5G  0 part 
&#9492;&#9472;sdb4   8:20   0 881.5G  0 part 
```

Then i tried to encrypt /deb/sdb/sdb2 partition and i tried these two commands:

```
sudo cryptsetup luksFormat /dev/sdb/sdb2
```
and
```
sudo cryptsetup luksFormat --type luks1 /dev/sdb/sdb2
```

but for both i get this error:

```
Device /dev/sdb/sdb2 doesn't exist or access denied.
```

---

### Post by peter1897 on 2020-09-20
I found my mistake. I had to use /dev/sdb2 instead of /dev/sdb/sdb2. I encrypted the partition and installed Kubuntu but when i boot it drops in the initframes terminal. I am missing some steps but i don't know if i can fix this. It looks complicated to me. I'll probably install Fedora KDE or OpenSUSE KDE until Kubuntu fix this installer.

---

### Post by QIII on 2020-09-20
I've never had trouble with the installation of Kubuntu.  It seems you said you found "your" mistake.  Is that the fault of Kubuntu?  Are the KDE versions of Fedora (which I use nearly as often as Kubuntu.  If Ubuntu and Canonical popped out of existence today, I'd be perfectly happy to carry on with Fedora.) and OpenSUSE any less vulnerable to human error than Kubuntu?

Encryption isn't just a "click a button" proposition in either of those, I don't believe.

---

### Post by peter1897 on 2020-09-20
> **QIII said:**
> I've never had trouble with the installation of Kubuntu.

Have you tried manual partitioning and encrypting the partitions? Try to install Kubuntu 20 on virtualbox, create three partitions - boot, home and root, and try to encrypt the home and root partitions. I bet the installer will crash for you.

---

### Post by tapucosmo on 2020-09-20
Did you follow the post-installation steps in the guide? It seems like /etc/fstab or /etc/crypttab might not have been configured correctly, or the initramfs might not have been properly rebuilt.

---

### Post by QIII on 2020-09-20
> **peter1897 said:**
> Have you tried manual partitioning and encrypting the partitions?

Yes.

> Try to install Kubuntu 20 on virtualbox ...

Did you try a bare metal installation before adding the potentially problematic issue of VBox?  

I don't doubt that you are having issues.  But one cannot jump the the conclusion that the issues are the fault of Kubuntu.  If you want help, that is what we are here for.  We are not here for the "I'll use something else" statements.  Which distro you choose is none of our business.

---

### Post by peter1897 on 2020-09-21
> **tapucosmo said:**
> Did you follow the post-installation steps in the guide? It seems like /etc/fstab or /etc/crypttab might not have been configured correctly, or the initramfs might not have been properly rebuilt.

Yes, i tried to follow the post-installation guide but the steps for implementing chroot and installing cryptsetup-initramfs are confusing to me. If you can help me with more simple guide i will try to follow it.

---

### Post by peter1897 on 2020-09-21
> **QIII said:**
> Yes.

Did you try a bare metal installation before adding the potentially problematic issue of VBox?  



Yes, i tried to install Kubuntu 20 on my laptop HP Elitebook 8560w and every time i tried to encrypt my home and root partitions installer crashes. Then i tried to install it on virtualbox and installer crashes every time again. I prefer to use Kubuntu because i am used to apt package manager and deb packages, but if i can't encrypt my installation i have to look for other distro that uses kde desktop.

---

