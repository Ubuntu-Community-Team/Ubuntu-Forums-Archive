---
title: "Unable to Install 20.04 LTS"
date: 2020-07-30
forum: Installation &amp; Upgrades
---

### Post by monsuj on 2020-07-30
Hello Everyone,

I am new to Linux and Ubuntu. I am trying to install Ubuntu 20.04 LTS along with my (Pre-installed) Windows 7. 

I have total 7 partition in my HDD. 1 for windows 7 installation rest of the drive for other file saving purpose. 

There is one drive which is fully empty (dev/sda7) but when I am selecting Something Else while installing Ubuntu I am only seeing 3 partition.

Where as using Ubuntu live CD I can see and mount all 7 partitions. 

Could you please let me know how can i proceed further

---

### Post by gdesilva on 2020-07-30
Assuming that you are using an older BIOS and not UEFi, one possible reason could be that under BIOS only 4 PRIMARY partitions are allowed. The way around is to make the fourth partition an EXTENDED partition and then create others are LOGICAL partitions. AFAIK, one of the design benefits of UEFI is it removes this limitation. However, DO NOT change the partition types now unless you are prepared to back them up, create a new partition table and restore them back as it will break your Windows 7 installation.

Perhaps, a better alternative will be to install Linux on another drive (if you have two) or on an external drive. You can still dual boot without running the risk of screwing up Win 7 installation.

---

### Post by Impavidus on 2020-07-30
Your Windows uses dynamic partitions. This isn't supported by Linux. In a sense, the Ubuntu installer shows you the real partitions, but Windows pools them together and then splits them in a different way to form the dynamic partitions that it shows to you. I don't think there's an officially supported way by Microsoft to convert those dynamic partitions back into normal partitions. There may be third-party tools that can do the job.

---

### Post by pbear42 on 2020-07-30
> **monsuj said:**
> Hello Everyone,
Where as using Ubuntu live CD I can see and mount all 7 partitions. 
Can you post a screenshot of how sda looks in GParted?  Alternatively, run [COLOR=#ff0000]sudo parted -l[/COLOR] (that's an L, for list) and post the output.

---

