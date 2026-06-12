---
title: "ubuntu does not recognize partitions"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by restricted on 2012-03-31
im trying to install ubuntu 11.10 amd 64 but the setup of ubuntu does not recognize the windows 7
i have searched with google and i have find that i have to make extended partition for being able to make ubuntu find that partition  but i have no idea how to make it
here is my partitions table [IMG]http://i42.tinypic.com/157ur5.png[/IMG]
what i want is to install ubuntu on the free space at the right of the image
please help me :p

---

### Post by 23dornot23d on 2012-03-31
Your partition is ready now for a Ubuntu install

If you have downloaded the Ubuntu CD .... you can set your computer to boot
up from it 

It will run from the CD as a live session and allow you to install it then to the 

Unallocated space ....

(Free Space ... maybe needs setting to unallocated space ..... as that can be done using gparted)

or maybe your partition editor allows that ..... by deleting the one that says free space .....

does that then set it to unallocated space ?

---

### Post by darkod on 2012-04-01
If the disk has been used in raid earlier, this can happen. There could be remains of raid meta data on the disk which windows ignores but ubuntu doesn't.

Since you are not running raid right now, boot into ubuntu live mode and try in terminal:
sudo dmraid -E -r /dev/sda

If that asks you if you want to remove meta data, say yes.

After that try this and post the output:
sudo parted /dev/sda unit s print

That will print out your partitions with more details as ubuntu sees them.

---

