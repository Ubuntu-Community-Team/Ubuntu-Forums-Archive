---
title: "Ubuntu installation through windows XP - Problem"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by dhammikai on 2012-01-25
Dear Friends,
I installed ubantu (ver 11.04) through Windows XP, after installation both OS are worked smoothly. But now I got a problem with starting of Windows XP, it is still restarting when I boot it. Ubantu is working properly and Windows XP is need to format. I install Ubantu in separate partition in my computer. My problem is if I format Windows XP partition, it might me lost that menu which displays during the booting of computer (selection menu of Ubantu and Windows XP). Some one  please help me to find safe way to install Windows again without loss (or any option) starting selection menu.

Thanks 
Dhammika

---

### Post by carl4926 on 2012-01-25
It's a little difficult to understand your post.

You can format the XP partition and the computer will still boot.

But, honestly I'm not too sure what you want to do...

---

### Post by dhammikai on 2012-01-25
Hi,
Thanks carl4926, my problem is if I format my XP partition, it will lose that menu which is used to select Ubantu or XP during the boot. I need to know how I create this menu again. 

dhammika

---

### Post by carl4926 on 2012-01-25
If you format the XP partition it should be OK

If you do loose the boot menu, don't panic. 

I suggest you get yourself a copy of SuperGrubDisk
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)
It can boot you in to ubuntu. Once there do:

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

But I'm wondering what you plan to do in the space where you delete XP?

---

### Post by critin on 2012-01-25
> **dhammikai said:**
> Hi,
Thanks carl4926, my problem is if I format my XP partition, it will lose that menu which is used to select Ubantu or XP during the boot. I need to know how I create this menu again. 

dhammika

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

This will install boot repair on your live ubuntu cd or thumb drive so you can run it and fix grub menu.  After formatting Windows, run the live cd again, find this link and install the boot repair via the terminal.  Run it.
[]("http://ubuntuforums.org/member.php?u=809261")
The suggestion given by carl4926 may be easier for you.

---

### Post by dhammikai on 2012-01-25
Hi Thanks for the quick reply,
I need these two OS (Ubantu and XP) with my PC. Because some of my programs are running under XP. My XP partition is already currepted and I need to format it. Then I am plan to reinstall XP. My problem is if I re-install XP, that OS selection menu (This menu was created automatically when I install Ubantu through XP. ) which is display during the booting of computer might be lose. So how I make it again?

Dhammika

---

### Post by carl4926 on 2012-01-25
OK
Get supergrubdisk first if you can. If not a ubuntu live cd can be used
So re-install XP and follow my advice in this post
[http://ubuntuforums.org/showpost.php?p=11638341&postcount=4](http://ubuntuforums.org/showpost.php?p=11638341&postcount=4)

With a Ubuntu live cd the process is

> * Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

    *

      When that is done you need to run update-grub to create the configuration file.

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sda

---

### Post by larrypg on 2012-01-25
Hello,

Before you go any further you need to determine if this is a Wubi install or a regular install.  You seem to say that you installed Ubuntu through XP which sounds like a Wubi install.  There are very different ways to fix it depending on what kind of install it is.

---

### Post by Mark Phelps on 2012-01-26
> **dhammikai said:**
> Dear Friends,
I installed ubantu (ver 11.04) through Windows XP, after installation both OS are worked smoothly. 
Wubi install ...
> But now I got a problem with starting of Windows XP, it is still restarting when I boot it. Ubantu is working properly and Windows XP is need to format. I install Ubantu in separate partition in my computer. 
If the Windows filesystem gets corrupted, it often can not launch Ubuntu.  That's a major downside of using Wubi.
> My problem is if I format Windows XP partition, it might me lost that menu which displays during the booting of computer (selection menu of Ubantu and Windows XP). 
There are two menus:
1) Created by the Windows boot loader -- for Wubi installs
2) Created by GRUB -- for separate partition installs.

Since you apparently do NOT want to use Wubi, reformatting and reinstalling XP will not remove the GRUB menu -- but you will then have to regenerate it.
> Some one  please help me to find safe way to install Windows again without loss (or any option) starting selection menu.
Simply not possible ... to keep GRUB or Wubi intact with a Windows reinstall. In the first case above, the Wubi file will be erased with the Windows reinstall; in the second case, the MBR will be overwritten by the Windows reinstall -- even though the GRUB code will remain intact in the Linux filesystem.

You need to tell us WHICH version of Ubuntu you want to keep using -- an Wubi install, or a separate partition install.

---

### Post by baqar on 2012-01-26
I am going to format my HDD and start from the beginning
I will first install XP
then Win 7
and then Ubuntu 11.10
Then will update i will succeed or what :P

---

### Post by dhammikai on 2012-01-27
Hi, Thanks for more details abt. my problem. I am using Ubantu 11.04, it is installed in my Partition E:. Today I format windows XP partition (C: and reinstalled it. Then, now I starting of my computer it's only start Windows XP, it not display that selection menu ( actually I dont what that menu called GRAB or wubi). If I need to start Ubuntu, it didn't display any option (menu)!!. But my ubuntu installtion is still in my E: partition.  So, now I want to create that menu

---

### Post by carl4926 on 2012-01-27
Do you have an Ubuntu Live CD
or a copy of SuperGrubDisk on a CD?

I posted the 2 solutions earlier
1. [http://ubuntuforums.org/showpost.php?p=11638341&postcount=4](http://ubuntuforums.org/showpost.php?p=11638341&postcount=4)

2. [http://ubuntuforums.org/showpost.php?p=11638367&postcount=7](http://ubuntuforums.org/showpost.php?p=11638367&postcount=7)

---

### Post by dhammikai on 2012-01-27
Hi, 
Yes I have Ubantu setup DVD 11.04. Now I already format windows XP partition and I installed win XP now.  Could you please give me instructions of when I boot my PC with ubantu DVD then how I open a terminal? 

Dha

---

### Post by carl4926 on 2012-01-27
> **dhammikai said:**
> Hi, 
Yes I have Ubantu setup DVD 11.04. Now I already format windows XP partition and I installed win XP now.  Could you please give me instructions of when I boot my PC with ubantu DVD then how I open a terminal? 

Dha

Before following the text below, please tell me if you are able to burn a copy of:
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

Place the Ubuntu disk in the DVD drive and reboot the computer
Choose to try Ubuntu
[http://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu%2010.04%20Install/2.%20boot_menu_try.jpg](http://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu%2010.04%20Install/2.%20boot_menu_try.jpg)

At the Desktop:
Open a terminal (you must know how to do that, if you have been using Ubuntu)
Then follow the info here
[http://ubuntuforums.org/showpost.php?p=11638367&postcount=7](http://ubuntuforums.org/showpost.php?p=11638367&postcount=7)

---

### Post by dhammikai on 2012-01-27
Yes I can burn a copy of "[http://www.supergrubdisk.org/categor...2diskdownload/]("http://www.supergrubdisk.org/category/download/supergrub2diskdownload/")" in CD

Dha

---

### Post by carl4926 on 2012-01-27
> **dhammikai said:**
> Yes I can burn a copy of "[http://www.supergrubdisk.org/categor...2diskdownload/]("http://www.supergrubdisk.org/category/download/supergrub2diskdownload/")" 

Dha

Do that
Then boot from it and it should find your Ubuntu installation and let you boot it.

Once there, open a terminal and do

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

Remove supergrubdisk from the drive and reboot
It should all work again normally

---

### Post by dhammikai on 2012-01-30
Thanks I got it done.
Dhammika

---

### Post by carl4926 on 2012-01-30
> **dhammikai said:**
> Thanks I got it done.
Dhammika
That's good to know

---

