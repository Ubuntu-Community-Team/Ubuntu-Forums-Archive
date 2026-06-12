---
title: "UBUNTU 7.10 server with RAID"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by InfoTech on 2007-12-29
I will be installing file & DHCP server for a small company, using Ubuntu 7.10 server. I have ASUS P5K motherboard, 2x1024MB Transcend RAM, one 160GB WD SATA II for OS and two 400GB WD SATA II for data storage, which I intend to use in RAID 1. The MB is equipped with jmicron RAID controller, which is, as I understood what I read on the net, a "fakeRAID" controller. Also, I am not a Linux wiz. 

Since the OS is not going to be on the RAID disk, I was wondering what would be the procedure to do that? Also, should I use softRAID or fakeRAID? Which is more reliable? Easier to install and use?

I appreciate any suggestion. Thanks.

---

### Post by Pumalite on 2007-12-29
Even if you install in different drive, you'll have problems because Grub will try to install to the Raid and will fail. So, read this carefully:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Pumalite on 2007-12-29
Even if you install in different drive, you'll have problems because Grub will try to install to the Raid and will fail. So, read this carefully:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by InfoTech on 2007-12-29
So, the advice is to go with FakeRAID?

---

### Post by Pumalite on 2007-12-29
I think so. Less headaches. Myself, I prefer no Raids at all.

---

### Post by InfoTech on 2007-12-29
Thanks. I believe that data will be safer with RAID 1than without it.

---

### Post by Pumalite on 2007-12-29
I understand you. You are running a Server and I'm at a Desktop.

---

### Post by InfoTech on 2007-12-29
Btw, how much space on hard drive is enough to install it as second OS on my desktop?

---

### Post by Pumalite on 2007-12-29
I wouldn't run Ubuntu on less than 20 GB:
10 GB for '/'
1 GB for /swap
The rest for /home.

---

### Post by InfoTech on 2007-12-29
I guess the smallest HDD I can find would be 80GB... so... no need to bother :) 

On the other hand, I do not intend to repartition my Win drive. I'll just buy new HDD.

---

### Post by Pumalite on 2007-12-29
It's the best choice. Let Grub install to MBR (by default) and you'll have dual boot.

---

### Post by InfoTech on 2007-12-29
Tell me, what are precautions not to screw my XP drives?

---

### Post by Pumalite on 2007-12-29
Installing a new OS means backing up as a matter of good practice. As for screwing your XP, if done well, none.

---

