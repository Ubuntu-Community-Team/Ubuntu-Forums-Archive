---
title: "can not start after installing update in ubuntu 9.10"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by lengjingmao on 2009-12-08
Dear all, 

I am using a 64 bits Ubuntu. Yesterday, after installing the update from the panel icon notification. After installation, I restarted the computer, then I can not go the log in panel, the system warning me that "GDUO_GET_IDENTIty failed for /dev/.tmp-block-8:0" and alert! /dev/sdb1 does not exist. Dropping to a shell. 

Then it shows a busybox shell. 

Please help about this problem

thanks a lot

---

### Post by zkriesse on 2009-12-08
Is the system a 64 bit system?

---

### Post by lengjingmao on 2009-12-08
> **ZachK_ said:**
> Is the system a 64 bit system?
yes. it is 64 bit system

---

### Post by zkriesse on 2009-12-08
Ok...now...let's research that error shall we? :)

---

### Post by lengjingmao on 2009-12-08
> **ZachK_ said:**
> Ok...now...let's research that error shall we? :)
yes, I am willing to provide more details. I am using a Dell T7400 workstation. I only installed the ubuntu OS on the machine. The OS was installed from a liveCD, 9.04 version. 

I update online from 9.04 to 9.10.

---

### Post by zkriesse on 2009-12-08
Hmmm did the system work fine before updating it to 9.10?

---

### Post by lengjingmao on 2009-12-08
> **ZachK_ said:**
> Hmmm did the system work fine before updating it to 9.10?
yes, even after I updated to 9.10. the problem started at yesterday, after I installed some updates. I forgot the exact name of the update package. but one of them is something like linux-header

---

### Post by zkriesse on 2009-12-08
Hmm....little side note...you don't have to quote every message :) Anyway..let me do some research.


[COLOR=Red]**EDIT HERE:** Take a look at this Ubuntu Forums post [http://ubuntuforums.org/showthread.php?t=881160](http://ubuntuforums.org/showthread.php?t=881160)[]("http://ubuntuforums.org/showthread.php?t=881160")[/COLOR]

---

### Post by lengjingmao on 2009-12-08
Hi, ZachK, 
__I read the post you give. I hit "e " on the kernal I am using "ubuntu, linux 2.6.31-16-generic". it is different with the post at  the "root = ......" the post is "root=uuid=......." and mine is "root=/dev/sdb1".

Do i need to change "root=/dev/sdb1" to "root=uuid=......."?

---

### Post by lengjingmao on 2009-12-08
I tried to edit the root=/dev/sda1 to root=uuid=............ but it didn't help

---

### Post by darkod on 2009-12-08
You didn't install with wubi did you? Because that's different.

You can boot with the ubuntu cd, Try Ubuntu option, download the script in my signature, put it on desktop for example and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with all the boot info. Copy the content of that file here and put CODE tags around it (with the text selected hit the # button in the toolbar above). That makes it easier to read.

---

### Post by lengjingmao on 2009-12-08
Hi, I have figured out where the problem is, after I changed the "root=/dev/sdb1" to "root=/dev/sda1" at the bootloader screen . The main problem is the OS didn't find the right boot partition. It used to be fine, I have no idea what happened after i installed the updates yesterday. 

BTW, is there a way to change "root=/dev/sdb1" to "root=/dev/sda1"  permanantly? 

Thanks~

---

### Post by darkod on 2009-12-08
There is, but you need to know why it happened. /dev/sda it the first hdd and /dev/sdb the second. It's entirely different device. It's good that it's working but why would sda be confused with sdb.
If you run in terminal:
sudo update-grub

that should update grub2 if that's what you're using.

---

### Post by lengjingmao on 2009-12-08
yes, this is a strange problem after installing the update. I guess maybe it is causing by the hard driver I am using is the second hard driver on this machine. The first one was totally crashed then I got a new one to replace it. But this kind of problem never happened after the replacement. I have run the command line you posted. 

Here is the response: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by darkod on 2009-12-08
It looks fine, now check if the booting works correctly.

---

### Post by jtliii on 2009-12-09
I have had this same issue three times after GRUB updates. For some strange reason when the update happens it changes my hd0,0 in the boot menu item from sdj2 to sdg2. The simplest solution is to edit the bootloader menu item to point to the correct drive and partition (if you don't know what this is you can find out by booting to LiveCD and running "sudo gparted" from a terminal session) then selecting ctrl+x to boot with the changes. At this point your computer should boot normally but you should run "sudo update-grub" from a terminal session to make sure the changes are permanent.

---

