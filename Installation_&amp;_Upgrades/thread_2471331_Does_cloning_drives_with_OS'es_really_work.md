---
title: "Does cloning drives with OS'es really work?"
date: 2022-01-27
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2022-01-27
So I have just purchased a new SSD drive and want to replace the old one containing all the operating systems on it (triple-boot).

Can I just clone it? Are there any risks regarding this type of operation?

Thanks!

---

### Post by tea for one on 2022-01-27
Before deciding to clone your Operating Systems, are you already using UEFI with GPT?

---

### Post by username2758 on 2022-01-27
Some of the machines, yes I think so (not quite sure). There are some older machines that only boot up in Legacy Mode apparently.

I'm still don't know much about UEFI, MBR, GPT etc. All I know is that in order to successfully set up a triple-boot between Mint, Ubuntu and Windows, I had to first disable 'secure boot' on the pre-built machines (Lenovo and Acer), but I don't know why that is actually necessary.

---

### Post by tea for one on 2022-01-27
UEFI and GPT is the way forward - more future-proof.
Secure boot is more of a trust issue - I have disabled secure boot because I trust myself ;)

GPT allows more than four primary partitions (older mbr only allowed 4 or 3 plus extended )
UEFI allows more flexible boot options (even when Grub is compromised)
If the PC vendor has supplied an advanced iteration of UEFI firmware, you can control the hardware without booting into an OS.

[https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)
[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)

You do not really have to know UEFI and GPT inside out because it is impossible (I include myself) to absorb every detail.
Have a look around these forum pages and you will see how often it is mentioned and recommended.

Back to the cloning question:-

How many partitions are involved?
Is your new target SSD larger than the source HDD?

---

### Post by rsteinmetz70112 on 2022-01-27
You didn't say what OSs you're cloning so this is generic. 

In my experience cloning drives with an OS installed works, provided you use the same hardware and the new drive is the same size or preferably larger than the old drive. Windows will sometime not run on the new drive because it doesn't recognize the hardware but you can usually fix that by simply reactivating Windows. If you start making changes like adding UEFI or GPT you may run into problems, I'd make any such changes seperate from the cloning process.

---

### Post by ubfan1 on 2022-01-27
Alignment requirements are another consideration for the partitions.  Some cloning tools, like Macrium Reflect, claim to do the clone correctly (even to a smaller target -- personal experience is that it works).  No experience with multiple boot cloning though. I'd expect that doing one at a time would be fine.

---

### Post by coley9225 on 2022-01-27
When I upgraded to a ssd, I had a multi-boot setup. At the time I had windows 10 home, lubuntu 18.04, and linux mint. I purchased a dual bay hard drive dock with direct clone capabilities. I removed hdd and placed in source bay, put new ssd in target bay and cloned 1 to the other. This faster than other methods available. When the clone operation completed, I put the ssd in my lenove laptop, booted, and all os's worked exactly as they did with the hdd. IMHO, this is the best method, not only because of the speed( 1TB hdd to 1 TB sdd), but I didn't need to worry with compatibility of cloning software with the different os set ups. Before you make any attempts, remember the cardinal rule of system modification...make up to date backups, just in case things go sideways. Good luck.

---

### Post by username2758 on 2022-01-27
Thank you all for the answers!

So far I have 6 partitions in total containing Ubuntu, Mint and Windows operating systems and system reserved partitions that Microsoft creates automatically.

Yes the target drive is larger in size, and yes I intend to use the cloned drives with the exact same hardware. And I do have a hard drive dock that has a cloning feature but never tried to use it. The problem is that this new SSD is NVMe not SATA, so this dock won't work for this kind of operation.

So what cloning tools/software would you guys recommend?

---

### Post by tea for one on 2022-01-27
Please backup your personal date from each OS first.

[https://clonezilla.org/](https://clonezilla.org/) Device to device using disks

If you have not used Clonezilla before, please proceed cautiously.

---

### Post by MAFoElffen on 2022-01-27
I just put both drives in my drive bay and used dd to clone the drive. I ensure the target is same size or larger. Afterwards, if the target was larger, I expand the partitions and filesystems.

---

### Post by rsteinmetz70112 on 2022-01-27
I usually use gddrescue. It can also make an image of the drive.

---

