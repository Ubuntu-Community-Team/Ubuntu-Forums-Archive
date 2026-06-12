---
title: "Installing ubuntu 12.04 on a computer with old BIOS"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by jsvidyad on 2013-03-29
Hello,

   I read on some website that you need to take certain precautions if installing ubuntu on a computer using UEFI. I want to install ubuntu 12.04 on a computer with the older BIOS. Do I need to do anything special during the installation for the older BIOS? I am going to install ubuntu 12.04 as the only OS for now. But, I will leave some space on the hard drive just in case I feel like installing windows 7 later and make it a dual-boot system.

---

### Post by oldfred on 2013-03-29
If it does not have Windows it is not much of an issue. Most BIOS systems have all four primary partitions used so it can be difficult to install. You can only have 4 primary partitions and Windows normally uses 2. Ubuntu boots fine from logical partitions in the extended partition.

If not installing Windows first, I would still allocated sda1 as a primary partition formatted NTFS with the boot flag. I might make sda2 a data partition NTFS for any data you might want to share. Then make sda3 the rest of the drive as an extended partition. Then you can install Ubuntu into the extended partition with as many logical partitions as you want.

With BIOS and wanting Windows you have to use MBR(msdos) partitioning. Windows only boots from gpt partitioning with UEFI. If drive is over 2TB, it does have to be gpt.

If a desktop system, often better to have two drives, one Windows and the other Ubuntu.

---

### Post by jsvidyad on 2013-03-30
While installing ubuntu 12.04 on such a machine with an old BIOS, do I have to do anything special? Or do I just do the normal steps for the installation?

---

### Post by jsvidyad on 2013-03-30
If I don't want to install windows, can I use a gpt partitioning system even with the old BIOS if I want to install ubuntu 12.04? I have heard that there are issues with using gpt for intel boards. Is that right?

---

### Post by fantab on 2013-03-30
> **jsvidyad said:**
> If I don't want to install windows, can I use a gpt partitioning system even with the old BIOS if I want to install ubuntu 12.04? I have heard that there are issues with using gpt for intel boards. Is that right?

Though GPT is new and has certain advantages over DOS, I'd recommend that you DO NOT use GPT unless your HDD is more than 2TB, on OLD BIOS. Is there any special need that you want to use GPT?

Just follow the usual Ubuntu install procedure, you should be fine. If you plan on installing Windows later then remember that Windows will only boot from GPT if the Mobo has UEFI.

---

### Post by oldfred on 2013-03-30
I do not agree with fantab, but to his point the vast majority of users here that will help you know the 30 year old MBR(msdos) partitioning. 

But gpt is the future. And it does work. Once I converted to it, I really do not notice any difference other than no issues of primary and logical partitions. But you have to be sure you will never want Windows on a gpt drive, if you ony have BIOS to boot. And if you decide you want Windows later, it is not easy to convert. Usually best to fully back up & erase drive, but the creator of gdisk does have a tool that works if partitions have a couple of sectors between them.

Just to learn about gpt I converted my old original 160GB drive that started with 6.06 to gpt and installed 10.10 when it first came out. Intel Core2Duo system from 2006, upgraded motherboard in 2009. I had a few minor issues which had easy work arounds. I since have used gpt on my 16GB flash drive with a full install and my SSD. Arch suggests gpt also for SSDs unless you want Windows with BIOS booting. You do have to have bios_grub partition or grub does not install correctly.

I do believe it is best to keep Windows on a Windows drive and Ubuntu on all your other drives. And I really like the poster a few weeks ago that said when he buys a new laptop, he buys a better system, but with a hard drive. Then removes Windows hard drive and puts it on the shelf in case he sells system later. He then installs a SSD and Ubuntu. Best use of Windows hard drive I have heard. :)

---

### Post by grahammechanical on 2013-03-30
> **jsvidyad said:**
> While installing ubuntu 12.04 on such a machine with an old BIOS, do I have to do anything special? Or do I just do the normal steps for the installation?

Please do not get confused. It is new machines with UEFI, Secure Boot and Windows 7 or 8 pre-installed that seem to be giving people problems. I base this on the posts on this forum asking for help with these types of machines.

If you only intend to have Ubuntu on the machine then simply running the Live Session and selecting Install Ubuntu and choosing Use the Entire disk will work very well.

According to the advice already given by those who know about this subject, you should make advance preparation if at any time in the future you may want to install Microsoft Windows. It will avoid problems at the time.

I do not have Windows. I had no problem installing Ubuntu on my machine with BIOS when it was new 6 years ago. I install ubuntu into different partitions for testing and I have no problems.

But if I was to install Windows I would expect problems especially if I was trying to get it to share an hard drive with Ubuntu. So, do not forget it is not the BIOS system that has been giving problems over the years. The problems are coming from the changes brought in recent years, especially with machines that have Windows pre-installed.

Regards.

---

