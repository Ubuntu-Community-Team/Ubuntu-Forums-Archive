---
title: "Ubuntu 7.10 fresh install crashed on AMD 64 bit (dropping to shell... boot err_msg)"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by robinsingh on 2008-01-03
Hi there,
4 days ago I fresh installed Ubuntu linux 7.10 on a newly bought HP desktop computer with following hardware config:
AMD Athlon 64 X2 5000+
3GB PC2-5300 DDR2 SDRAM
400GB SATA 7200RPM
16X LightScribe Dual Layer DVD Burner
NVIDIA GeForce 6150 SE
512KB + 512KB L2

Even though I have a 64bit processor, I downloaded PC (Intel x86) desktop CD version from 
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)  (since it said it works for all PC's).

Everything has been working fine for past 4 days. I have restarted and hibernated the machine a couple of times. It booted up perfectly fine everytime until this last time. I was just doing regular development work, and restarted the box (since it was acting a little slow), and I got this error on startup
=============
starting up 
loading please wait
check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT ! /dev/disk/by-uuid/d5e557ca-6739-4642-94a0-02d096a4f1f3 does not existing.
Dropping to a shell.

Busy Box v 1.1.3 (Debian 1:1.1.3-5Ubuntu7) Built in Shell (ash)
Enter 'help' for a list of build-in commands.
=============

Although I have noticed a lot of people have reported this error (some have solved it too..) but the solutions doesn't seem to apply for me since they are either for ppl who have done an upgrade from  6.x to 7.x etc. or they are getting slightly different error message than mine. (like a similar one said "/bin/sh can’t access tty; job control mode off’ error" which is not my case).

I would appreciate if someone can help me in this case, 
I started my machine and ran a few commands to help diagnose this issue.

$ sudo fdisk -l output looks like following :
==============
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c4e4208

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          49      393561   83  Linux
/dev/sda2              50       36522   292969372+  83  Linux
/dev/sda3           36523       37251     5855692+  82  Linux swap / Solaris
/dev/sda4           37252       48641    91490175    b  W95 FAT32
==============

My machine is running only a Ubuntu linux . (No dual boot with windows etc.)
Also I could not locate my grub/menu.lst file either(isnt that strange).

$sudo find / -name "*menu.lst*" only lists the following files... (none of them points to an actual grub menu)
==============
/usr/share/doc/grub/examples/menu.lst
/usr/share/doc/memtest86+/examples/grub-menu.lst
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub
/rofs/usr/share/doc/grub/examples/menu.lst
/rofs/usr/share/doc/memtest86+/examples/grub-menu.lst
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_addwindowsentrygrubmenu
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_changegrubpasswordforgotten
/rofs/usr/share/ubuntu-docs/ubuntu/sample/menu.lst_displaysplashimagegrub
==============
And since my error message mentions /dev/disk/by-uuid/ directory , I ran the following command as well 
================
ubuntu@ubuntu:/$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-01-03 07:10 6d76946d-60c1-4c2e-b55c-7c5f8c967a7c -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-03 07:10 6eb77921-ae81-40dc-9258-1dbbcce5f846 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-03 07:10 C37D-4DA3 -> ../../sda4
================

I am very hopeful :-( that someone can help me resolve this issue without having to install 
an AMD v64 iso install image. But If someone can assure that that install image will fix this issue forever, I don't mind installing that as a last resort. I have a lot of tools installed on this box, so I would prefer to bring this current installation back to life.

THANKS A LOT FOR ANY HELPFUL POINTERS IN ADVANCE...
ROBIN

---

### Post by Partyboi2 on 2008-01-03
Can you post your grub menu.lst if you can find it at /boot/grub/menu.lst
```
cat /boot/grub/menu.lst
```

---

### Post by robinsingh on 2008-01-03
I really appreciate you trying to help me resolve this issue ..
Okay, 
I pressed escape at the initial grub boot prompt and pressed "e" at the 
Ubuntu 7.10, kernel 2.6.22-14-generic label , and got the following contents (which I assume are being read from my menu.lst file)

root (hd0,0)
kernel /vmlinuz-2.6.22.14-generic root=UUID=d5e557ca-6739-4642-94a0-02d096a4f1f3
initrd  /initrd.img-2.6.22.14-generic
quiet

Does that help ??

how come I cann't locate this file when I boot from liveCD and run the command
sudo find / -name "*menu.lst*"

( Please refer to my last post showing output of this command)..
Thanks,
Robin

---

### Post by Partyboi2 on 2008-01-03
Are you able to check manually if you can see grub menu.lst
```
cd /boot/grub
```then 
```
ls
``` You should see it listed
From what I can gather grub is trying to boot ```
UUID=d5e557ca-6739-4642-94a0-02d096a4f1f3
```which does not exist
where as
```
UUID=6d76946d-60c1-4c2e-b55c-7c5f8c967a7c
```is listed as sda1 and should be the UUID that grub uses to boot.

---

### Post by robinsingh on 2008-01-03
Also I booted from liveCD and got the output of /etc/fstab. here it is:

$sudo /etc/fstab

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

---

### Post by robinsingh on 2008-01-03
> **Partyboi2 said:**
> Are you able to check manually if you can see grub menu.lst
```
cd /boot/grub
```then 
```
ls
``` You should see it listed
From what I can gather grub is trying to boot ```
UUID=d5e557ca-6739-4642-94a0-02d096a4f1f3
```which does not exist
where as
```
UUID=6d76946d-60c1-4c2e-b55c-7c5f8c967a7c
```is listed as sda1 and should be the UUID that grub uses to boot.

Regarding the grub directory, I tried to "cd" to it from the liveCD terminal ... but couldn't. 
I don't understand why is it not there.. Is there someway I could restore it manually. (like create a dir, and put a menu.lst file there.. using some example template etc. ?? what do you suggest)

ubuntu@ubuntu:~$ cd /boot
ubuntu@ubuntu:/boot$ ls -l grub
ls: grub: No such file or directory
ubuntu@ubuntu:/boot$


But if I don't have the menu.lst file then when I press the Esc button at the intial Grub boot up  prompt, It shows some contents (that I posted in my previous post)...
where are these contents pulled from ?

---

### Post by robinsingh on 2008-01-03
Regarding changing the UUID .. I will give the following a shot..

root (hd0,0)
kernel /vmlinuz-2.6.22.14-generic root=UUID=d5e557ca-6739-4642-94a0-02d096a4f1f3
initrd /initrd.img-2.6.22.14-generic
quiet

I will change the UUID in the above line-2 to point to my /sda1 which points to /boot folder
UUID=6d76946d-60c1-4c2e-b55c-7c5f8c967a7c

I will do it from the command line by presssing escape and by editing the the (regular boot label , ie the non-recovery one)... please confirm if that's what you want me to try..

---

### Post by robinsingh on 2008-01-03
> **robinsingh said:**
> Regarding changing the UUID .. I will give the following a shot..

root (hd0,0)
kernel /vmlinuz-2.6.22.14-generic root=UUID=d5e557ca-6739-4642-94a0-02d096a4f1f3
initrd /initrd.img-2.6.22.14-generic
quiet

I will change the UUID in the above line-2 to point to my /sda1 which points to /boot folder
UUID=6d76946d-60c1-4c2e-b55c-7c5f8c967a7c

I will do it from the command line by presssing escape and by editing the the (regular boot label , ie the non-recovery one)... please confirm if that's what you want me to try..

Ok I tried doing the above mentioned, I got the following error message:
```

Starting up..
Loading Please wait..
kinit: name_to_dev_t(dev/disk/by-uuid/6eb77921-ae81-40dc-9258-1dbbcce5f846)=sda3(8,3)
kinit: trying to resume from /dev/disk/by-uuid/6eb77921-ae81-40dc-9258-1dbbcce5f846
kinit: no resume image, doing normal boot..
mount: Mouting /root/dev/ on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Busy Box v 1.1.3 (Debian 1:1.1.3-5Ubuntu7) Built in Shell (ash)
Enter 'help' for a list of build-in commands

```

Please let me know if you want me try something else..

---

### Post by Partyboi2 on 2008-01-03
When you get to the grub menu, press "e" to edit then find the line starting with Kernel eg.
```
kernel   /boot/vmlinuz-2.6.24-2-generic [COLOR=Red]root=62322ba8-1af4-4c15-8359-2cc45e52a24f[/COLOR] ro quiet
```change the numbers to /dev/sda1 so it will look something like this
```
kernel   /boot/vmlinuz-2.6.24-2-generic [COLOR=Red]root=/dev/sda1[/COLOR] ro quiet
```then press return.
If /dev/sda1 does not work try it with /dev/sda2
Let me know if this works.

---

### Post by robinsingh on 2008-01-03
> **Partyboi2 said:**
> When you get to the grub menu, press "e" to edit then find the line starting with Kernel eg.
```
kernel   /boot/vmlinuz-2.6.24-2-generic [COLOR=Red]root=62322ba8-1af4-4c15-8359-2cc45e52a24f[/COLOR] ro quiet
```change the numbers to /dev/sda1 so it will look something like this
```
kernel   /boot/vmlinuz-2.6.24-2-generic [COLOR=Red]root=/dev/sda1[/COLOR] ro quiet
```then press return.
If /dev/sda1 does not work try it with /dev/sda2
Let me know if this works.

I did the above mentioned, (tried with /dev/sda1, /dev/sda2, /dev/sda3) In all the cases I get the following error at startup...
```

Starting up..
Loading Please wait..
kinit: name_to_dev_t(dev/disk/by-uuid/6eb77921-ae81-40dc-9258-1dbbcce5f846)=sda3(8,3)
kinit: trying to resume from /dev/disk/by-uuid/6eb77921-ae81-40dc-9258-1dbbcce5f846
kinit: no resume image, doing normal boot..
mount: Mouting /root/dev/ on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Busy Box v 1.1.3 (Debian 1:1.1.3-5Ubuntu7) Built in Shell (ash)
Enter 'help' for a list of build-in commands

```

I WONDER why is it not finding anything on my main linux partition that resides on /dev/sda3 ?
Could I check the contents of this partition (using boot CD etc. ? ))
Do you think we have any other option that remains to be tried... :-(

---

### Post by Partyboi2 on 2008-01-03
Yes you can check the contents by using the live cd.
Boot live cd and when loaded open terminal
```
mkdir check
```
```
sudo mount /dev/sda1 check
```
Change sda1 to the partition you want to check

---

### Post by robinsingh on 2008-01-03
i think my hard disk is bad.. i am returning this pc to the store..
thanks for your time..

---

