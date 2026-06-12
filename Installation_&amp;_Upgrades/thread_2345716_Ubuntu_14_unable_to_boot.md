---
title: "Ubuntu 14 unable to boot"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by abdirizaq on 2016-12-07
Since yesterday, one of my machines was unable to boot. I have tried boot repair using the live cd but it has failed. This is the output of the process. [http://paste.ubuntu.com/23592156/](http://paste.ubuntu.com/23592156/) the system contains critical data that I need and thus am reluctant to reinstall the entire system. What is the appropriate solution to do?

---

### Post by alexjpowell on 2016-12-07
What did you change?

---

### Post by gordintoronto on 2016-12-07
You might need to revert to your system backup.

---

### Post by oldfred on 2016-12-07
Boot-Repair usually dumps a printout of fstab.
Was it not able to read the LVM partition? Did you unencrypt it? Or is file missing or LVM ext4 partition corrupted.

I do not know nor use LVM.
But the first part of this is mounting LVM from live install and then it says you can run other task like repairs.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641) 

Then something like this, yours my be slightly different using /dev/mapper/lib-vg-root:
      
 sudo e2fsck -f /dev/ubuntu-vg/root

---

