---
title: "blkid shows ext4 as ext3"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-03-19
Can anybody confirm that blkid reports ext4 partitions as ext3?

---

### Post by taavikko on 2009-03-19
Reports them correctly here

```
blkid 
/dev/sda1: UUID="b4af46d0-9fea-48ec-9907-b70f0d1dbe70" TYPE="ext4" 
/dev/sda2: UUID="b6596275-e1e9-46c4-9142-da9e0abd4791" TYPE="ext4" 
/dev/sda5: UUID="32009148-23d7-4281-b5b7-75c5f14ecbcc" TYPE="swap" 
/dev/sdb1: LABEL="warehouse" UUID="0287d1b4-b14c-4596-b205-a523a69c7707" TYPE="ext4" 

```

If reporting as a bug, it belongs to "e2fsprogs" pkg.

---

### Post by taavikko on 2009-03-19
Also using "sudo vol_id /dev/sdxx" reports it correctly. 
But that's udev's function...

---

### Post by zenarcher on 2009-03-19
Reports them correctly here, as well....

zenarcher@zenarcher-desktop:~$ blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="3cef971d-9aa2-4020-b3aa-95aba1a2f60c" TYPE="ext4"
/dev/sda5: UUID="3acd1c79-9d6e-489c-9606-c808878cf1d2" TYPE="swap"
/dev/sda6: UUID="9d22cf8e-2a53-4901-ae99-381662ac2108" TYPE="ext4"
zenarcher@zenarcher-desktop:~$

---

### Post by plun on 2009-03-19
Ok also for me, 2 disks

```
plun@plun:~$ sudo blkid
[sudo] password for plun: 
/dev/sda1: UUID="18b2cb8e-50c1-47b8-a2a9-e867aed579a3" TYPE="ext4" 
/dev/sda2: TYPE="swap" UUID="e906f957-cd3c-4ab4-a090-ae300d69c94a" 
/dev/sda3: UUID="D64C-89B1" TYPE="vfat" 
/dev/sda4: UUID="3f6faeba-2573-4b06-8db3-888dc7d49e1f" TYPE="ext4" 
/dev/sdb1: UUID="22FC6BE3FC6BB029" TYPE="ntfs" 
/dev/sdb2: LABEL="Test" UUID="e6ba6337-144e-494d-8ec2-33b384867661" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap"
```

---

### Post by todak on 2009-03-19
Both disks reported correctly here ```
/dev/sda1: UUID="afd1c645-b30e-49e7-b1a3-363a6cd99f11" TYPE="reiserfs"
/dev/sdb1: UUID="6fce1d5c-4da7-427b-bd06-5c3b06d326a9" TYPE="ext4"
```

---

### Post by nyarnon on 2009-03-19
Think it's time to update my install CD :-) Sorry false alarm.

---

