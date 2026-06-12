---
title: "Raid 1 on Ubuntu 10.04.2 LTS Server"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by vortek on 2011-07-04
Hi there,

I followed this guide [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch) to configure my Ubuntu 10.04.2 LTS already running to use RAID 1 with another disk I installed.
The problem is that i had to adapt the tutorial to grub2 and it didn't come out very well...

At the moment i have the system running but with a minor problem.
Only the first disk's boot is working.

If i go into the bios startup device selection and select the first disk, the system then loads grub2 and asks me which OS i want to start, (hd1,1) or (hd0,1) with are in RAID 1 (md0). And both start fine and the server runs smoothly.

If i choose to startup from disk 2, i go into grub rescue with the message no such devide ...............-1ade8fc64980.

Anyone out there who can give me a hint? I believe that the boot from the second disk is messed up...

Best regards.

---

### Post by YesWeCan on 2011-07-04
It is good you are running Grub2. What's the output of grub-install -v?

It is hard to prescribe without know more details, but have you tried reinstalling Grub like this:
sudo grub-install --root-directory=/boot /dev/sda
sudo grub-install --root-directory=/boot /dev/sdb

---

### Post by vortek on 2011-07-05
Thanks for the answer.

```
$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu12)

```
My current setup is:

/dev/md0 contains /dev/sda1 and /dev/sdb1
/dev/md1 contains /dev/sda5 and /dev/sdb5

I am a bit scared to try grub-install on sda and sdb because one of them is working :)

---

### Post by YesWeCan on 2011-07-07
Your trepidation is understandable. :)
Your grub version is fine.
The installs are independent so if you try just the disk that does not work, the one that does work will still work.

---

