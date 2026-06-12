---
title: "Installing ubuntu 10.10 instead of 8.04, and alongside with vista"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by ubu- on 2011-04-02
I have Windows Vista and Ubuntu 8.04 on my PC. I'd like to remove Ubuntu 8.04, and install ubuntu 10.10 without changing the Vista partition.

So I should manually specify the partitions. However when I delete the Ubuntu partition I get a popup "No root file system is defined". I don't want to mess up with my partition so I thought I'd post this here.

Could you please send me the steps to proceed with my installation?

---

### Post by Quackers on 2011-04-02
Welcome to UF.
No need to delete the ubuntu partition, you can just over-write it with 10.10
Select the 8.04 partition during installation, check the box to format it, use ext4 file system (from the drop-down box) and don't forget to select the mount point (which is "/" for root - also from a drop-down box).
The error message you are getting is because the mount point has not been selected.

---

### Post by ubu- on 2011-04-02
Thank you :)

I selected the partition of the 8.04, changed the type from ext3 to ext4, checked the format checkbox. I assume this is not supposed to affect my vista partition.

After selecting my timezone, keyboard layout and entering username and password, I am stuck in the "Who are you page". Although "Ready when you are" is displayed, I can't click the forward button, I can only click the back button

---

### Post by Quackers on 2011-04-02
Have you started the username with a capital letter? No capitals allowed there :-)

---

### Post by ubu- on 2011-04-02
Haha true. Thanks!

---

