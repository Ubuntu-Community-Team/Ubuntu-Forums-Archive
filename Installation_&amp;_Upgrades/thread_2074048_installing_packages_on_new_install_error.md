---
title: "installing packages on new install error"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by unibroker on 2012-10-20
I added another Ubuntu OS to my dual boot today and am having trouble with a respondent's suggestion for installing packages from the other OS's /home directory.  ```
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
```Everything is fine until the last line whereupon I get the following last few lines after a lot of output ```
0 upgraded, 1155 newly installed, 44 to remove and 0 not upgraded.
Need to get 1,537 MB of archives.
After this operation, 3,563 MB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/
```Not quite sure what this means because I installed the /home to a 100+GB partition.  Ideas/suggestions?

---

### Post by steeldriver on 2012-10-20
How big is the / partition though? /var is not in /home...

If necessary you could run apt-get clean beforehand to clear the cache of any packages left over from the install

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by unibroker on 2012-10-20
> **steeldriver said:**
> How big is the / partition though? /var is not in /home...

If necessary you could run apt-get clean beforehand to clear the cache of any packages left over from the install

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

I think I need to do this install over again.  I looked all day for partitioning schemes.  I think I only designated 2 logical partitions with /home being one taking up a majority of the space.  I'm glad I still have my original Ubuntu 12.04 32 bit.  This was added to give me a 64 bit platform for playing around with android.  I figured if I was able to duplicate my 32 bit configuration I'd just delete the 32 bit and absorb the space.  Any partition schemes suggested?

---

