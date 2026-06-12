---
title: "Can't install Ubuntu on the volume I want."
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by parkergking on 2016-11-04
So, as the title says, I am struggling to install Ubuntu on the volume I want. The volume is the result of shrinking my secondary drive on my Windows 10 installation.

I have attached pictures of both the Computer Management screen, and my options when trying to install Ubuntu.


[ATTACH=CONFIG]271954[/ATTACH][ATTACH=CONFIG]271955[/ATTACH]


I greatly appreciate any help. Thanks!

---

### Post by alexjpowell on 2016-11-04
Try formatting it NTFS within Windows then trying again

---

### Post by parkergking on 2016-11-04
> **alexjpowell said:**
> Try formatting it NTFS within Windows then trying again


That was the first thing I tried.

---

### Post by alexjpowell on 2016-11-04
Can you post a current screenshot please?

---

### Post by parkergking on 2016-11-04
> **alexjpowell said:**
> Can you post a current screenshot please?


Of what?

---

### Post by alexjpowell on 2016-11-04
The screenshot in Windows you posted shows that the volume is unformatted
Was this taken after you formatted it? If not, I'd like to see another one please

---

### Post by Impavidus on 2016-11-04
There is a dynamic partition on that drive. Ubuntu can't handle Windows dynamic partitions. You have to get rid of that dynamic partition first to get back to basic partitions, then Ubuntu can create an ext4 partition for itself.

I don't think there's an official way to convert dynamic partitions back to basic, so that means backing up your 416GB of data on E:\ and formatting the entire drive.

---

