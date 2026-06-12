---
title: "How to install Ubuntu7.10 from the harddisk with the Suse10.3"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ganqing1234 on 2007-10-23
I only use the Suse10.3(no windows), now I want to install Ubuntu7.10 from the harddisk, but don't know how to do. I have donwloaded  the ubuntu-7.10-alternate-i386.iso,  hope some one can help me. Thanks a lot!

---

### Post by Pumalite on 2007-10-23
You don't have a CD-DVD drive?

---

### Post by Pumalite on 2007-10-23
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ganqing1234 on 2007-10-23
I have, but I have no installed CD. Thank you very much!

---

### Post by Pumalite on 2007-10-23
You cannot install Ubuntu with Suse, but you can use Gparted Live CD to resize your Suse partition and then install Ubuntu in that partition after following the guides I provided you with.

---

### Post by ganqing1234 on 2007-10-23
Ok, I will try. Thanks!

---

### Post by ganqing1234 on 2007-10-24
I copied the initrd.gz and vmlinuz to the /boot(Suse) and added something to the menu.lst, then I reboot the system, yes I can see the installed interface, but it couldn't detect or mount the iso, it can not find it. I put the iso in the directory of /home(/dev/sda6), I don't know how to mount /home when intalling. 

Is there any one has the same exprience? please help me, thanks.

---

