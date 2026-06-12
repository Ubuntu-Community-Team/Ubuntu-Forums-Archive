---
title: "Ubuntu installer is only detecting SSD partition from my hybrid disk drive."
date: 2021-03-01
forum: Installation &amp; Upgrades
---

### Post by jinoabraham on 2021-03-01
Hello everyone,

I've a hybrid SSD(256 GB)+ HDD(1 TB) drive Asus laptop which I recently brought. Windows 10 is already preinstalled on it.

I want to install Ubuntu v20.04, so I created a bootable USB and tried to install Ubuntu through it and dual boot both OSs.

But the installer is only detecting my SSD drive and not my HDD. [I]I prefer to install Ubuntu to my HDD as I've limited SSD space and also don't want to mess with Windows partition.

[/I]Things that I've already done:
[LIST=1]
[*] Disabled Windows fast boot.
[*] Disabled secure boot.
[*] Turned off encryption.
[/LIST]

I'm stuck & confused on what to do next as I've very easily installed Ubuntu on my old laptops and PCs, but this looks quite challenging.

Any help or advice will be much appreciated.

Thanks.

---

### Post by oldfred on 2021-03-01
What model Asus?

Did you change to AHCI? You need first to install Windows AHCI driver before changing drive settings in UEFI.
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

Post this:
sudo parted -l

---

### Post by jinoabraham on 2021-03-06
Sorry for the late reply.. 

Here's the result of sudo parted -l.
[ATTACH=CONFIG]288072[/ATTACH]

---

### Post by QIII on 2021-03-06
@jinoabraham:

We would prefer that all terminal commands and their results be copied as text and posted here between code tags.  An image has two drawbacks here:

1.  Even in this day and age, there are users with slow connections or data limits.

2.  It is impossible for others to cut and paste the text to attempt to reproduce the results.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Hagar Delest on 2021-03-06
I've a similar configuration with a 128GiB SSD and a 1TiB HDD. I've reduced my Windows 10 partition to 70GiB so that I've 2x30GiB partitions for my GNU/Linux distros. And the data are on the HDD (several partitions also, including the one for the Windows user data).
During the install, once you've configured the SSD partition, you need to select the HDD drive with the GParted drop-down list top right IIRC. Then you should be able to configure it as well.

---

### Post by CelticWarrior on 2021-03-06
@Hagar

Not quite. The HDD isn't seen. Answer - AHCI - is already in post #2.

---

### Post by Hagar Delest on 2021-03-06
Ah, indeed. Never heard of RST/AHCI before. I should have checked the parted -l result also.

---

