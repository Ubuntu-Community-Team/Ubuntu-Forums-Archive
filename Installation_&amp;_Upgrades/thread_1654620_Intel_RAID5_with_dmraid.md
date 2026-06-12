---
title: "Intel RAID5 with dmraid"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by ffixcollector on 2010-12-28
I am new at RAID volumes in linux, but I have 3 2tb samsung HDD that are set up as a RAID 5 in BIOS. dmraid recognizes them, but I do not know how to get the array to be recognized by Ubuntu 10.04. I also would like to install a fresh system on this array.
```
/dev/sdc: isw, "isw_cdiebbagbj", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdb: isw, "isw_cdiebbagbj", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sda: isw, "isw_cdiebbagbj", GROUP, ok, 3907029166 sectors, data@ 0

```
any direction or FAQ's would be helpful.

---

### Post by ronparent on 2010-12-28
You need to see this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Unfortunately it has not been updated for 10.04 or 10.10. Fortunately these later distros are friendlier with raids. A bug currently prevents gparted from seeing your raid partitions. Although it has been fixed upstream I don't believe the fix has yet shown up in these distros. The workaround is to boot to a live cd session and install kpartx to that session. Then start the instll and select the manual partitioning option at the partitioning step to create your partition to install to and a swap. If your existing partitions already number 2 or more, you will have to use gparted create an extended to install to (to keep your primary partition count to four or less. If this sounds daunting you had better make sure any existing data is well backed up before you proceed. Post if you have additional questions.

---

### Post by ffixcollector on 2010-12-28
Thanks for the info, I'll give it a try.

---

### Post by ffixcollector on 2010-12-30
Works great. One question though, How stable is ubuntu and fake raid? The FAQ site says > FakeRAID is not supported by Ubuntu. Trying to install Ubuntu on such a partition could easily result in the loss of all your data.
The reason I have a raid 5 is to prevent the loss of any of my data.

---

### Post by ronparent on 2010-12-30
> FakeRAID is not supported by Ubuntu. Trying to install Ubuntu on such a partition could easily result in the loss of all your data.
This statement is false and reveals a general disdain of fakeraid. RAID of any type adds a degree of complexity to the operating system and can result in loss of all data if misused! I would recommend a good backup plan to protect all essential data raid or not. Raid5 can be robust and normally protect against loss of data. Used in a non-professional environment where systematic data backup schemes are not consistently employed can invite data loss. 

I commend raid use only by individuals interested in experimenting with and learning how to properly use. Casual use of any raid system can be disastrous. Have fun.

---

