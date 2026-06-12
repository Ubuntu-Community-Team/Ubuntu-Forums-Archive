---
title: "Installing OpenSuse 11 RC1 hides Ubuntu 8.04"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by bineeshm on 2008-06-07
Hi! Folks,

I'm new to Linux - absolutely liked Ubuntu and just completely migrated out of Windows in my Laptop (HP DV5215). Just wanted to try OpenSuse 11 RC1 and decided to have a dual boot with Ubuntu 8.04. I installed OpenSuse few hours back; when the installer asked for Disk partition, I selected LVM Option as the Partition method asked to format the entire system. OpenSuse got installed in EXT3 (Please see attachment). After the installation I'm not able to see Ubuntu in Boot Loader and it just gets into OpenSuse.

Can you please assist me in fixing the boot loader and enable me to access Ubuntu?? Ubuntu is my primary OS and I dont want to miss that like this.

Thanks in advance for your help.

Regards,
Bineesh

---

### Post by Pumalite on 2008-06-07
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Then sudo grub update.

---

### Post by bineeshm on 2008-06-07
Hi!
Thanks very much for the quick response. Tried the method provided in the thread provided (the first method), but still I'm getting only the OpenSuse boot loader. What I actually wanted is to see both Ubuntu & Suse in the boot loader so I can select either of them. Attaching another screenshot of the LVM. Trust this helps.

Regards,
Bineesh

---

### Post by Pumalite on 2008-06-07
In 'find /boot/grub/stage1' you should get at least two posibilities. Try the other one.

---

### Post by bineeshm on 2008-06-07
Hi! I'm getting only one option when I tried. Please see the attached screenshot.

Has it got anything to do that I created only a Logical partition??

~B

---

### Post by Pumalite on 2008-06-07
Post a screenshot of Gparted.

---

### Post by bineeshm on 2008-06-07
What is Gparted and where can I find it?? I'm replying from LiveCD mode and should I boot to OpenSuse to get this Gparted??

Thanks in advance for your understanding, I'm really a beginner in Linux :).

---

### Post by Pumalite on 2008-06-07
I think it comes with the Live CD: 'Partition Editor'

---

### Post by bineeshm on 2008-06-07
Hi!

Got it. Please see the attachment.

~B

---

### Post by Pumalite on 2008-06-07
Where is openSUSE supposed to be? Where is Ubuntu supposed to be? At most is one there. The rest looks like empty space. Why do you have a /boot partition? And if so, why is it at the end?
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by bineeshm on 2008-06-07
It happened like this: I had only Ubuntu in my system and wanted to try OpenSuse as well. When the Suse installation started, it gave me 3 options - 
1 - User entire hard disk
2 - LVM
3 - Manual Partition

I selected the LVM, where it partitioned the system as you see in the Gparted. If you see the attachment in first thread, OpenSuse has took only 20 odd GB isnt it?

Please let me know whether I need to have a complete installation again or is there a way out.

Thanks,
~B

---

