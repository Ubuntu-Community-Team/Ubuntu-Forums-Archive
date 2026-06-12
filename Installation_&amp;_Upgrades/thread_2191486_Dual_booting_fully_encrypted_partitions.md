---
title: "Dual booting fully encrypted partitions"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by augustrigmarole on 2013-12-02
I would like to have 2 installations of Ubuntu 12.04 LTS on my hard drive. I want to fully encrypt both partitions completely (not just the home folder) with different passwords, so that one partition cannot modify or affect the data on the other partition. One partition will be trusted, while the other one will be untrusted, so I don't want the untrusted partition to access or change anything on the trusted partition.

How might I go about setting this up? I know the alternate installer allows full disk encryption, but I am not sure if it will allow me to partition the drive this way.

I'm open to suggestions on how I might be able to go about this. If necessary, I would be willing to use other programs like Gparted to help me accomplish this, but the alternative installer may already be able to do this.

---

### Post by sudodus on 2013-12-03
Welcome to the Ubuntu Forums *augustrigmarole*,

You are starting with a hard nut :-)

One way is to have a basic system (encrypted or not) and let it be host for two virtual machines. Those virtual machines are independent of each other and can be encrypted as you wish. Such a system needs a fair amount of RAM, and it will be slower because of the virtualisation.

---

### Post by augustrigmarole on 2013-12-03
Yes, the idea of using virtual machines is tempting, but unfortunately I am a gamer, so even the best virtual machine will not be able to run some of the newer games.

---

### Post by sudodus on 2013-12-04
If it is a desktop machine, you can have two internal hard disk drives, and encrypt each of them.

If you need exactly what you specified in the first post, I cannot help you. ***[COLOR=#ff0000]Let us hope someone with more experience will see this post and start helping you[/COLOR]*** :-)

---

### Post by sioxs on 2013-12-04
Some essential reading should help steer you in the right direction:
[http://www.tldp.org/HOWTO/MultiOS-HOWTO.html](http://www.tldp.org/HOWTO/MultiOS-HOWTO.html)
[http://www.tldp.org/HOWTO/Disk-Encryption-HOWTO/index.html](http://www.tldp.org/HOWTO/Disk-Encryption-HOWTO/index.html)
[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html)
[http://www.tldp.org/HOWTO/Cryptoloop-HOWTO/index.html](http://www.tldp.org/HOWTO/Cryptoloop-HOWTO/index.html)
[http://www.tldp.org/HOWTO/Encrypted-Root-Filesystem-HOWTO/index.html](http://www.tldp.org/HOWTO/Encrypted-Root-Filesystem-HOWTO/index.html)
For a single list of topics see: [http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html](http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html)
peace
sioxs

---

### Post by augustrigmarole on 2013-12-04
I started reading those links posted, but it's going to take a while.

In the meantime, the closest procedure I can find that indicates what I want to do is possible is here:

[http://askubuntu.com/questions/264416/dual-ubuntu-installations-with-whole-disk-encryption](http://askubuntu.com/questions/264416/dual-ubuntu-installations-with-whole-disk-encryption)

In this case, the person asked for a Xubuntu/Ubuntu dual boot with different passwords on each encrypted OS. Maybe someone here can help provide the details on what Gilles suggested:

"You'll need to install from the alternate CD for dmcrypt. Select manual partitioning in the installer. If you want two separate encrypted volumes, make them both primary or extended or EFI partitions, and leave enough room for the other volume when you install the first OS."

I tried following this guide until I can finish reading sioxs's material. I do have the alternate CD. I also already used gparted to create 2 primary ext4 partitions. But beyond that, the details are pretty thin. There is no information on how to proceed with the alternate CD. And from what I've read so far, I can anticipate future problems; even if I manage to successfully install both operating systems, I will have to somehow set up grub so that I can pick which one to boot.

---

### Post by oldfred on 2013-12-04
I do not know encryption nor LVM.
But the few with boot issues that have posted have a /boot partition outside the LVM and the LVM for the rest of the hard drive. So you may need two /boot and two LVM.
But you cannot create LVM with gparted.

       LVM
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

### Post by augustrigmarole on 2014-01-06
I've done a lot of reading, but it doesn't seem like I'm getting anywhere close to doing what I originally posted. I've accepted that it's impossible (unless I see evidence to the contrary). However, I would still like to do what sudodus posted. It is very easy to encrypt two different hard drives separately. Suppose one hard drive used Ubuntu's default guided encryption (alternate CD) and the other hard drive used, say, Truecrypt to encrypt Windows. Is there a way I can pop up a boot menu so I can choose which hard drive I want to boot into when the computer is powered on? I would like to do this without having to edit the BIOS settings each time I power on the computer.

---

### Post by sudodus on 2014-01-07
If you have two drives fully encrypted, and do not want any of them to be decrypted or running, when the other one is used, it is a difficult situation. It could be solved with a third drive, a small and simple drive is enough, even a USB pendrive, that can chainload either of the other drives. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by oldfred on 2014-01-07
One user did post that he had truecrypt for Windows and installed Ubuntu on same hard drive, but put grub2 boot loader on flash drive. 
Have to be careful when installing not to install grub2 over truecrypt boot loader in MBR or you have to use Something Else or manual install to have option on where grub is installed.

---

