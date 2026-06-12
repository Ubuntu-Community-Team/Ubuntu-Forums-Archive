---
title: "Can I install 64 bit while retaining raid array and /home partition"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by smilingralph on 2009-12-31
I've looked all over but been unable to find an answer to my question. I've currently got Xubuntu 9.10 32 bit installed in the following raid configuration:
md0 : active raid1 sda1[0] sdb1[1]
      96256 blocks [2/2] [UU] /boot
      
md1 : active raid0 sda2[0] sdb2[1]
      58588800 blocks 64k chunks /
      
md2 : active raid0 sda3[0] sdb3[1]
      195318016 blocks 64k chunks /home
Is it possible to install 64 bit Xubuntu 9.10 while retaining raid array and without formatting the /home partition so that my data remains intact. And if so how?

---

### Post by presence1960 on 2010-01-01
> **smilingralph said:**
> I've looked all over but been unable to find an answer to my question. I've currently got Xubuntu 9.10 32 bit installed in the following raid configuration:
md0 : active raid1 sda1[0] sdb1[1]
      96256 blocks [2/2] [UU] /boot
      
md1 : active raid0 sda2[0] sdb2[1]
      58588800 blocks 64k chunks /
      
md2 : active raid0 sda3[0] sdb3[1]
      195318016 blocks 64k chunks /home
Is it possible to install 64 bit Xubuntu 9.10 while retaining raid array and without formatting the /home partition so that my data remains intact. And if so how?

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by smilingralph on 2010-01-01
Thank you presence1960 for your reply. Unfortunately the link you provided didn't really answer my question. Did the installation anyway and found out the installer recognized the raid partitions and allowed me to keep the /home data just by making sure "do not format" section was checked. Happily running Xubuntu 64 bit on raid0 array. :P

Ralph

---

### Post by tgalati4 on 2010-01-01
Yes, you can.  Sorry for being late.

---

