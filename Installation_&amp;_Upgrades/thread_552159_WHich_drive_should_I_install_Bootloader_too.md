---
title: "WHich drive should I install Bootloader too?"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by madhatter64 on 2007-09-16
I have two HDs. The main OS drive is known as SDA1 (where WIndows XP is installed.

I have attempted installation to SDA7 (root) a swap partition, and SDA9 (Home).

It went well. Reboot however coughed up blood and gave me soem gibberish about not finding an operating system or no boot record, (can't remember)

I tried again and this time I noticed that 'Advanced' on the installation (just after you partition your drive) gives one a choice as to where the bootloader goes. The default is HD0.I have a feeling that's where my problem (as described) begins. Should I try again and install the bootloader to my WIndows boot partition (SDA1)?

Please advise.

Thanks!

---

### Post by eggdeng on 2007-09-16
Some linux utilities still use the traditional method of numbering partitions: if hd0 is the first HDD, then hd0,0 is the first partion on the first HDD, hd0,1 is the second partition on the first HDD etc.
Other utilities now call the first HDD sda, the second sdb etc, which means that the first partition on the first hard disk is sda1.
So sda1 is the same partition as hd0,0.
When you install ubuntu over W*nd*ws, unless you specify otherwise, GRUB will write itself to the MBR (first sector, first partition, first HDD). It overwrites the old MBR but recognises and provides the option to boot into legacy OSs. It's unusual to have problems with this with XP.

---

### Post by patsfan on 2007-09-16
i have a dual boot machine and i installed ubuntu on my slave  drive and it used ab loader on the master with no problems

---

