---
title: "Installed OK  with XP but now wont boot"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by mrgee on 2008-06-06
Hi..
Bit of a linux newbie.. so apologies.. I have installed ubuntu on a seperate partition from win xp.. Install went smoothly but when I reboot there is no option to load ubuntu..the machine boots straight to XP.. I know this has something to do with the boot loader.. but not sure what I need to do in order to get an option on boot to select the OS..
Any help?
Thanks..

---

### Post by baldino on 2008-06-06
Same problem with me !
just installed ubuntu, and a newbie too

---

### Post by housam on 2008-06-06
boot from ubuntu live cd and go for application >> accessories >> terminal . type in the terminal the following code :
```
sudo fdisk -l
```

where -l is a small L ,press enter. and post the results.

---

### Post by Hans Fastolfe on 2008-06-06
I have a similar problem.  My PC won't boot at all after installing Ubuntu.  I get a "disk read error" message, followed by "Press ctrl+alt+delete" to continue.  At first, I could boot into Ubuntu, but not XP.  Shortly thereafter, I could not boot into either.  

I had tried to install Ubuntu 8 on a Compaq PC as dual boot with the existing XP Home Edition.  I used the CD I just received in the mail.  I ran Checkdisk and Disk Defragmenter first.  The hard drive had plenty of free space, and I assigned 20 GB to Ubuntu.  The first installation was not entirely successful; Firefox would not work, and I could not figure out how to reinstall.  I can do this in Windows and Max OS X, but I was utterly baffled by Ubuntu (I don't claim to be a computer whiz; I hadn't studied computers since I took COBOL in college--with punch cards!).  

So I started over and reinstalled Ubuntu.  When the PC rebooted, I saw the expected boot menu, but with twice as many Ubuntu options; they seemed duplicated.  Ubuntu booted properly, but not XP.  On trying to boot into XP I received the "disk read error" message.  After that, Ubuntu would not boot.  

The PC recovery tools do not work.  When I try to run the Windows System Recovery utility, I receive the same "disk read error" message.  I did not try the Destructive Recovery utility, as that would erase the entire hard drive.  I wish to avoid that, if possible.  Unfortunately, I need Windows on the PC.  

I do not think the Ubuntu installation disk is corrupted.  I used the same disk the preceding day to successfully install Ubuntu on an XP PC as a dual-boot system.  That works properly, both XP and Ubuntu.  The Live CD function works properly, as I ran Ubuntu from it on the now-unbootable PC.  I seemed to see the files on what should be the Windows partition.  

A friend suggested I might have corrupted the Windows boot.ini file on the second Ubuntu installation. 

Am I frakked?

---

### Post by meindian523 on 2008-06-06
@Hans
Please post an new thread linking to this,because it will get confusing with three people posting their respective ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
```

@mrgee
Please post the results of the above commands.Also,no need to apologise for being a newbie.We were(and in my case,am) all newbies once.

---

### Post by Hans Fastolfe on 2008-06-06
[QUOTE=meindian523;5128368]@Hans
Please post an new thread linking to this,because it will get confusing with three people posting their respective ```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
```

Done.  Thanks.

Was the "cat /boot/grub/menu.lst" command meant for me?

---

### Post by meindian523 on 2008-06-06
Both the commands were meant for all three of you.Also,please post the link to your new thread in this one to make it easy for future searches to find everything which is related together.

---

### Post by mrgee on 2008-06-06
> **housam said:**
> boot from ubuntu live cd and go for application >> accessories >> terminal . type in the terminal the following code :
```
sudo fdisk -l
```

where -l is a small L ,press enter. and post the results.

Hi..
thanks for the reply..
When you say boot from the live cd.. I am not sure what you mean.. If I boot from the live cd, I see a menu with option like install mythbuntu..check cd.. install from hdd.. etc.. I can see no where to load a terminal window.. If I load from the first hdd..this takes me to windows..
Any help..
And thanks again..
Mike..

---

### Post by housam on 2008-06-06
> **mrgee said:**
> Hi..
thanks for the reply..
When you say boot from the live cd.. I am not sure what you mean.. If I boot from the live cd, I see a menu with option like install mythbuntu..check cd.. install from hdd.. etc.. I can see no where to load a terminal window.. If I load from the first hdd..this takes me to windows..
Any help..
And thanks again..
Mike..

when you boot from the live CD , the first line should be " try ubuntu without any change to your computer " . click on that line , it will install the system to your ram only to allow you to try it. look at the attachment

---

### Post by razvi on 2008-06-06
Try to edit /boot/grub/menu.lst file. You should have something like this: "title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
**makeactive**
chainloader	+1". 
You have to make active the Windows partition.

---

### Post by mrgee on 2008-06-06
> **housam said:**
> when you boot from the live CD , the first line should be " try ubuntu without any change to your computer " . click on that line , it will install the system to your ram only to allow you to try it. look at the attachment

Hi..
OK I can load the live cd..2 things.. how can I get a dual boot menu working.. and when I try to load the mythtv frontend I receive and error..?
Thanks
Mike

---

### Post by mrgee on 2008-06-06
> **housam said:**
> boot from ubuntu live cd and go for application >> accessories >> terminal . type in the terminal the following code :
```
sudo fdisk -l
```

where -l is a small L ,press enter. and post the results.

Hi..
OK the results are below
---------------

--------
Thanks
MikeDisk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0070d568

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23426   188169313+   7  HPFS/NTFS
/dev/sda2           23427       36481   104864287+   f  W95 Ext'd (LBA)
/dev/sda5           23427       36481   104864256    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff21ff1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x08627da4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2292       14742    94129528+   7  HPFS/NTFS
/dev/sdc2           14743       25841    83908409    f  W95 Ext'd (LBA)
/dev/sdc3               1        2289    17304808+  83  Linux
/dev/sdc4            2290        2291       15120   82  Linux swap / Solaris
/dev/sdc5           14743       18851    31064008+  83  Linux
/dev/sdc6           18852       23918    38306488+   7  HPFS/NTFS
/dev/sdc7           23919       25841    14537848+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdd: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         953     1966064    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 128, 32) logical=(952, 71, 32)
ubuntu@ubuntu:~$

---

### Post by meindian523 on 2008-06-07
Please also post
```
cat /boot/grub/menu.lst
```

---

### Post by mrgee on 2008-06-07
> **meindian523 said:**
> Please also post
```
cat /boot/grub/menu.lst
```

cat: /boot/grub/menu.lst: No such file or directory

Seems grub is not installed..?

---

### Post by meindian523 on 2008-06-07
You are on Live CD,aren't you?me bad](*,)

Ok,run this:
Create a direcory to mount a partition.
```
mkdir /mnt/abcd
```
Mount your / partition [which is either /dev/sdc3 or /dev/sdc5]
```
mount /dev/sdc<> /mnt/abcd
```
Then change directory to /boot/grub
```
cd /boot/grub/
```
Then ```
cat menu.lst
```
and post it here.

---

### Post by mrgee on 2008-06-07
> **meindian523 said:**
> You are on Live CD,aren't you?me bad](*,)

Ok,run this:
Create a direcory to mount a partition.
```
mkdir /mnt/abcd
```
Mount your / partition [which is either /dev/sdc3 or /dev/sdc5]
```
mount /dev/sdc<> /mnt/abcd
```
Then change directory to /boot/grub
```
cd /boot/grub/
```
Then ```
cat menu.lst
```
and post it here.

Thanks for your help so far..
I get a permission denied error when trying to make the /mnt/abcd dir..?

---

### Post by meindian523 on 2008-06-07
Use sudo for all the above commands.aargh,what am I thinking.](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by mrgee on 2008-06-07
> **meindian523 said:**
> Use sudo for all the above commands.aargh,what am I thinking.](*,)](*,)](*,)](*,)](*,)](*,)](*,)

Hi again..
Am now getting the following response to your suggested commands

ubuntu@ubuntu:~$ sudo mount /dev/sdc3 /mnt/abcd
mount: special device /dev/sdc3 does not exist
ubuntu@ubuntu:~$  sudo cd /boot/grub/
sudo: cd: command not found

Thanks
Mike

---

### Post by meindian523 on 2008-06-07
That's strange,since fdisk -l clearly shows a partition /dev/sdc3.I'm afraid I can't think of anything to do about that right now.

I've got to  leave for college,I will try to think over these errors and get back in the evening.Am sorry couldn't help you out there.

---

### Post by housam on 2008-06-07
Try to reinstall grub using [[COLOR="Red"]_Herman guide _[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

