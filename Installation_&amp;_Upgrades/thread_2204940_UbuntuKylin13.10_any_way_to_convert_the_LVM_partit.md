---
title: "UbuntuKylin13.10: any way to convert the LVM partition back to a common one?"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by hhtmp88 on 2014-02-11
Dear all,

During installation of UbuntuKylin13.10 ("ubuntukylin-13.10-desktop-amd64.iso"), I set to partition the 128GB SSD into:
sda1: /   --------------------- 30GB, ext4
sda2: /home ---------------- 85GB, ext4
sda3: Linux-swap -------------------- 4.24GB


After installation, the partitions became:
/dev/sda1: /boot ------------------ 243MB, ext2 (Flag&#65306;boot)
/dev/sda2: extended ------------- 119GB
    /dev/sda5: [SIZE=4]**ubuntukylin-vg**[/SIZE] ----- 119GB  ([SIZE=4]**Flag&#65306;lvm**[/SIZE])

which completely differs from what I want!

What's wrong?     
Are there any way to convert the LVM partition back into a common one?

Thanks for any kind of help!

==============================
* someone tell me: 
LVM: Logical Volume Manager&#65288;&#36923;&#36753;&#21367;&#31649;&#29702;&#65289; &#33021;&#21160;&#24577;&#25193;&#22686;&#21644;&#32553;&#23567;
vg: volume group --&#21367;&#32452;

---

### Post by hhtmp88 on 2014-02-13
no one can help?

---

### Post by robnils on 2014-02-13
What about deleting the partition and starting over? If you just installed it then you have nothing to lose, right? I have a LVM partition from a previous Fedora install that won't go away.. GParted makes odd threats when I attempt to delete it and since this partition is one of several on a 750 GB laptop, I'm a little nervous just chancing it. Does anyone know if it's okay to just delete the partition? I have something like

sda3/
   -> one partition 
   -> lvm
   -> ubuntu
sda4/windows
etc

I have a feeling deleting the lvm requires the deletion of the entire group,sda3, is that right? I can take a screen shot if helps but this isn't my thread...

---

