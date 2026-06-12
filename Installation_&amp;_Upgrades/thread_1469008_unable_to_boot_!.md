---
title: "unable to boot !"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by CheAmr on 2010-05-01
Hello 
now after upgrading ubuntu , It asked me to restart and I did , now I can not boot to windows xp or ubuntu 

this message appears everytime i try to start up my pc 

>   GNU  Grub version 1.79'' beta4

[ minimal BASH - like line editing is supported . for the first word TAB list possible command completions , anywhere else TAB list possibl device/file completions ]

sh: grub>   and thats it ......

I'm talking to you now through the live CD , please I need you help

---

### Post by CheAmr on 2010-05-01
somebody help me please..

---

### Post by garvinrick4 on 2010-05-01
In your live CD give me a copy and paste of this Code:

sudo blkid    (second letter is small L)

and

sudo fdisk -l    ( last letter is small L)


usually this is fixable to replace grub in sda do not fret.

---

### Post by CheAmr on 2010-05-01
Thanks for ur reply 

the first sudo blkid
gave me 
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A458C21358C1E460" TYPE="ntfs" 
/dev/sda5: LABEL="DISK 1" UUID="491A-1C73" TYPE="vfat" 
/dev/sda6: LABEL="DISK 2" UUID="491B-213D" TYPE="vfat" 
/dev/ramzswap0: TYPE="swap"


and the other 

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1be61be6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1548    12434278+   7  HPFS/NTFS
/dev/sda2            1549       19457   143854042+   f  W95 Ext'd (LBA)
/dev/sda5            1549       10676    73320628+   b  W95 FAT32
/dev/sda6           10677       19457    70533351    b  W95 FAT32


---

### Post by garvinrick4 on 2010-05-01
Use your LIVE CD: One at a time Code:

sudo mkdir /media/DISK1

 sudo mount /dev/sda5 /media/DISK1
                               
sudo grub-install --root-directory=/media/DISK1 /dev/sda

 sudo update-grub

sudo umount /media/DISK1  (that is not a typo umount is right)

---

### Post by CheAmr on 2010-05-01
all commands were ok except this one 
> ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.


---

### Post by arpanaut on 2010-05-02
I may be totally off here but what's with the references to vfat and fat32 on the partitions that I presume Ubuntu is installed on?

Or is this a wubi install?  If so pardon me... I know nothing about wubi

---

### Post by garvinrick4 on 2010-05-02
> **CheAmr said:**
> all commands were ok except this one
If it boots you are ok. If not it could not find / because I was not in "chroot" my fault.

We want to make sure the grub2 is replaced.


If does not boot go back to Live CD.

sudo mkdir /media/DISK1

sudo mount /dev/sda5 /media/DISK1

sudo chroot /media/DISK1

update-grub

Let me know if it upgrades the grub and finds your installs.

---

### Post by CheAmr on 2010-05-02
nope nothing new..

> ubuntu@ubuntu:~$ sudo mkdir /media/DISK1
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/DISK1
ubuntu@ubuntu:~$ sudo chroot /media/DISK1
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root
ubuntu@ubuntu:~$ root
The program 'root' is currently not installed.  You can install it by typing:
sudo apt-get install root-system-bin
You will have to enable the component called 'universe'
root: command not found


---

### Post by garvinrick4 on 2010-05-02
> **CheAmr said:**
> nope nothing new..
Did you upgrade a WUBI install, a folder inside of Windows? I see ramzswap in your blkid. There is nothing to mount at sda5 and I see now it is fat. Sorry I cannot help you with Wubi
or virtual install.

This project creates RAM based block device (named **ramzswap**)  which acts as swap disk. Pages swapped to this disk are compressed and  stored in memory itself. 
Compressing pages and keeping them in  RAM virtually increases its capacity. This allows more applications to  fit in given amount of memory. 
The usual argument I get is - **memory  is so cheap so why bother with compression**? So I list here  some of the use cases. Rest depends on your imagination :) 

[LIST]
[*]**Netbooks**:  Market is now getting flooded with these "lightweight laptops". These  are memory constrained but have CPU enough to drive on compressed memory  (e.g. [Cloudbook]("http://en.wikipedia.org/wiki/CloudBook")  features 1.2 GHz processor!).
[/LIST]

[LIST]
[*]**Virtualization**:  With compcache at hypervisor level, we can compress *any* part of *guest*  memory transparently - this is true for *any* type of Guest OS  (Linux, Windows etc.). This should allow running more number of VMs for  given amount of total host memory.
[/LIST]

[LIST]
[*]**Embedded  Devices**:  Memory is scarce and adding more memory increases  device cost.  Also, flash storage suffers from wear-leveling issues, so  its useful if we can avoid using them as swap device.
[/LIST]

---

### Post by CheAmr on 2010-05-02
I upgraded through ubuntu update manager , but first time i installed ubuntu was in windows with the ubuntu CD 

I can not boot to windows or ubuntu anymore after I have this message with a black background each time i try to reboot or open the pc
> GNU  Grub version 1.79'' beta4

[ minimal BASH - like line editing is supported . for the first word TAB list possible command completions , anywhere else TAB list possibl device/file completions ]

sh: grub>                      now I tried what you told me and nothing happened I dont want to lose my windows xp because of ubuntu's dumpness I have lots of VIP logins and stuff stored on my firefox and C partition on windows I can not take a backup from them through anything , 

if this problem can not be fixed ( the grub **** ) just tell me guys I lost my patience

---

### Post by garvinrick4 on 2010-05-02
[SIZE=5][COLOR=red]How to restore the Windows XP  bootloader[/COLOR][/SIZE]

For this you will need your Windows XP installation CD. Boot into it  now.

You will get to a part where it asks if you want to repair or recover.  To do so, press "r".

If prompted, enter your Windows XP administrator password. This will  leave you at at a command line, so type in the following two commands:

 	Code:
 	fixboot 
 	Code:
 	fixmbr 
Then type  	Code:
 	exit

---

### Post by CheAmr on 2010-05-02
thank you but the repair option isnt exist at all 

I wish I didnt upgrade ubuntu for sure 

thank you for offering help 
but I think I'll format the whole partition... its sad

---

