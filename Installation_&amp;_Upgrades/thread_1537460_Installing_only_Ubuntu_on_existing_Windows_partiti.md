---
title: "Installing only Ubuntu on existing Windows partition"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by icarus035 on 2010-07-23
Hi. I have 500GB HDD with 2 partitions: C (50GB, system) and D (450GB, data) and I have Windows 7 installed on C.

1) How do I install ONLY Ubuntu on C partition? I do not want dual boot, just Ubuntu.

2) Can I do this installation from USB stick?

I have not been able to find answers to these questions, but if someone already described this, please post a link.

Thanks!

---

### Post by CCoder on 2010-07-23
1) You can just use GParted from the Ubuntu Live CD & *wipe* the Windozzz7 installation off. Afterwards you can just install our lovely Ubuntu <3

2) U've got to use unetbootin, I suppose. I've never tried it. I, personnally, would consider using a CD (/DVD) :)

Without wax,
CCodeR.

---

### Post by linux18 on 2010-07-23
Just choose use entire partition/disk when installing ubuntu, but only if your ready. ( you would have been more ready if you said /dev/sda instead  of C: )

---

### Post by icarus035 on 2010-07-23
Thanks for the quick reply.

OK, after I launch GParted, I see my C partition.  After right click on it, I guess I should use "Format to..."  but I see lots of possible formats. Which one do I use?

---

### Post by wookieshaver on 2010-07-23
Ext3 would be fine as it is the  default file system format for Ubuntu and many linux installations. Here's a basic guide to file system formats:
 
[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
 
Welcome to Ubuntu!

---

### Post by icarus035 on 2010-07-23
Thanks!

---

### Post by CCoder on 2010-07-23
I would personnally use 'ext4'.

---

### Post by icarus035 on 2010-07-24
Ok. I formatted my windows C partition to ext3 and set it as root. Now I see as on the picture attached. When I say forward, it says something like "You have seleted any partitions to use as a swap space...". How do I do this without touching the widows D partition (sda5) with all my data?

---

### Post by icarus035 on 2010-07-24
Correction...it said "You have NOT selected any partitions to use as a swap space..."

---

### Post by icarus035 on 2010-07-24
Can I resize partition with GParted? Anyone pls help :(

---

### Post by ashwinrao on 2010-07-24
The minimum required partitions for installation are 'swap' , '/home' and '/'. Choose swap partition as double the size of your RAM and you can assign 20 GB for '/' and rest for '/home'.

---

### Post by ashwinrao on 2010-07-24
> **icarus035 said:**
> Can I resize partition with GParted? Anyone pls help :(

You can resize the current partitions while installing Ubuntu. Select Manual Advanced method and sda1. Allot the sizes as mentioned in previous post and proceed with the installation. Good luck and well come to the family :p

---

### Post by icarus035 on 2010-07-24
I do this by using the Resize/Move option?

---

### Post by icarus035 on 2010-07-24
OK thanks a lot! I will try this right now.

---

### Post by ashwinrao on 2010-07-24
Please start the installation from start and select the installation option as manual. You can get the option to re arrange the drive (sda1) partitions. The disk size will be in MB. Re arrange them properly. First, for swap and next for home and rest for /.

---

### Post by icarus035 on 2010-07-24
What type shoud each of them be (primary, extended or logical)?

---

### Post by icarus035 on 2010-07-24
I set them all as primary and successfully installed Ubuntu. Thanks for all the help!

---

