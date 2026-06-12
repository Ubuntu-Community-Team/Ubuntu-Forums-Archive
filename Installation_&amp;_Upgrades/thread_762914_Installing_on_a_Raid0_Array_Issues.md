---
title: "Installing on a Raid0 Array Issues"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by @xi0m on 2008-04-22
I'm trying to install Ubuntu 7.10 on a Raid0 array consisting of two empty 500GB SeaGate drives and it's been a complete nightmare.  I'm using this guide: [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)

I'm able to successfully install dmraid and list my array.
```
ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_bdcfcchd", stripe, ok, 976773166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bdcfcchd", stripe, ok, 976773166 sectors, data@ 0

```
Now, when I try to create my partitions, I end up with...
```
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/nvidia_bdcfcchd

Unable to open /dev/mapper/nvidia_bdcfcchd

```

I had previously tried to use this guide using the alternate install CD: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
I was able to create all my partitions and install Ubuntu but the installation would fail when I tried to install GRUB.

---

### Post by Pumalite on 2008-04-22
Have you read this?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by @xi0m on 2008-04-22
> **Pumalite said:**
> Have you read this?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I did and I run into the exact same issue.
```
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/nvidia_bdcfcchd

Unable to open /dev/mapper/nvidia_bdcfcchd
```
The only file located within /dev/mapper/ is a file called 'control'.

---

### Post by Pumalite on 2008-04-22
Maybe this would help:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by @xi0m on 2008-04-22
> **Pumalite said:**
> Maybe this would help:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

No dice.  It appears that only dmraid can see my array.  gParted and fdisk cannot for some reason.

---

