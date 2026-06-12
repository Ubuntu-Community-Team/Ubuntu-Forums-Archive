---
title: "Dual-booting and encrypted partitions"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by lixoman100 on 2008-01-09
Hello again everyone. I'm here to hear from you some suggestions and tips regarding dual booting Ubuntu and XP involving a encrypted partition.


I purchased an ASUS G1S laptop that should be arriving by the end of this week and I'm considering making Ubuntu my default operating system on it, as opposed to a experiment/hobby thing I do on my main computer. I'm still installing XP on it, because it comes with a good video card and I intend to do some gaming every now and then, but I'll try to focus on using mainly Linux this time.

Since it is a laptop and since I've been very interested in full-partition encryption, I did some experiments under VMWare and I'm ended up with the following setup:

- A /boot partition, with 50-100mb running ext2 or ext3
- A encrypted partition, with a LVM on it
- A SWAP partition on the LVM
- A / partition on the LVM running ext3 or reiserfs

I did this on VMWare and was quite pleased with the results.


My problem is: I want to have access to my data on the HD from both systems. I know there are some tools that allow you to access a ext3 partition on Windows, although I have never tried any and don't know how reliable they are, but I don't know if there is any tool that can access an encrypted partition, and with a LVM on top of it, and with reiserfs on top of it. I'm willing to give up reiserfs, but not encryption. Based on that, are there any suggestions you guys can suggest me or any links I can follow do learn more on this?

On my dual/triple boots I usually use a NTFS partition to hold my data, since Windows uses it natively and Ubuntu 7.10 deals with it greatly, but, in this case, it wouldn't allow encryption. I wanted to stay away from a solution like TrueCrypt or anything too out of the ordinary; I'd really like to just encrypt the partition that hold swap and / and be done with it.


Thank you for any advice offered.

---

### Post by lixoman100 on 2008-01-10
I'll give this a little bump before letting it die.

---

