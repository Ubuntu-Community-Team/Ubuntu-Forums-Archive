---
title: "Help with booting"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by terry45 on 2016-03-16
Hello,

I installed Ubuntu this evening on my Dell laptop which was running win10. I created a new partition and a swap partition and installed Ubuntu. On restarting the laptop I didn’t get an option to select windows or Ubuntu. Have I lost my windows 10 install?

I used boot-repair. It did not work. Here is the paste it created if this helps.

[http://paste.ubuntu.com/15405014/](http://paste.ubuntu.com/15405014/)

Thanks for reading.

---

### Post by terry45 on 2016-03-17
Going to try use windows recovery disk to repair boot table just to try something!

---

### Post by howefield on 2016-03-17
Does the machine boot straight into Ubuntu.

Appears that you have overwritten your Windows installation.

---

### Post by terry45 on 2016-03-17
Yes it boots directly to ubuntu.I don't think I've overwritten the partition as it's installed on a separate partition I created.

Gparted says unknown beside win partition!

---

### Post by justen_m on 2016-03-17
When Ubuntu boots, what happens when you run
sudo update-grub

Does it find the Windows partition at all?

---

### Post by yancek on 2016-03-17
The boot repair output does not show any windows partitions.  If also shows you are using GPT partitioning and it shows Grub code in the MBR.  If you are using GPT partitioning, you need windows installed UEFI and then you need to install Ubuntu UEFI.  Post an image of your GParted window showing the partitions.

---

