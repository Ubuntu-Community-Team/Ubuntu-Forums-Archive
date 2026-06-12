---
title: "Fresh installation of Ubuntu."
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by mlvmhn on 2015-04-26
Hello. 

I am about to help a friend with installing Ubuntu. But i am not sure how to begin?

Should i download the file to an usb-drive first, and then run the installation?

How do i get started with the installation?

---

### Post by ajgreeny on 2015-04-26
Where to start - - ?

How much do you know about installing any OS on a computer; have you ever done such a thing before?
What machine are we dealing with; does it already have an OS on it that you want to keep and run the two as a dual boot system?
Do you know what kind of BIOS/UEFI it is using? If it's a new machine it will probably be UEFI enabled, though you should also be able to use legacy BIOS/CSM (what it is called depends on the motherboard and the way it has been setup by the OEM).

Have a look at [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) and 
[UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

### Post by yancek on 2015-04-26
More information would be required before anyone could give you any realistic suggestions, particularly answers to the questions above by ajgreeny.  If you are new to this, you could start by checking the link at the Ubuntu site below explaining the most basic installation of Ubuntu.  The second link is considerably more detailed but you will definitely need to know a little about UEFI if it is a new machine.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Bucky Ball on 2015-04-26
You [download the ISO]("http://www.ubuntu.com/download/desktop") (you can also find a torrent further down the link at 'Alternative downloads' if you prefer) to your computer and then burn a disk image from that to either USB or a disk. You then boot from this install media to install. You need free space on the hard drive to install to. You do not install from the ISO you download. You need to make that USB or disk to install from. I would stick to the 14.04 LTS long-term support release for this.

And +1 to the last two posts.

---

### Post by mlvmhn on 2015-04-26
Ok. So i burn the iso and follow the instructions. 

Will the installation delete all of the old Windows then as i want?

---

### Post by Mark Phelps on 2015-04-26
Some points you need to consider BEFORE you charge into installing Ubuntu ...

First, never force an installation on an untried machine; instead, create the install media, boot using it, and select the Try option.  You need to do this to see how well it detects the hardware and installs all the necessary drivers.  IF you just force an install and (for example) the video chipset is not well supported, you could easily end up with no display and a very hard time fixing that.

Second, you didn't really answer the questions regarding what you want to do; nor, apparently, did you read through the links that folks provided you -- because your question about removing Windows was answered in the second link from post #3.  IF you're not going to answer questions, and not going to read -- you're going to have a very hard time getting adjusted to the Linux world.

---

### Post by mlvmhn on 2015-04-27
K, but the untested machine is just standing and no one is using it, so i will give it a shot. If it does not work, there is no loss. 
 i have also read the links, and decided to give it a shot with the "try option". 

if it is working fine in the "try Ubuntu" mode, do i have to do the installation process all over again?

if it is working w/ 14.10 LTS, is it a good idea to upgrade to Vivid Vervet?

---

### Post by ajgreeny on 2015-04-27
Actually, I suggest you try 14.04 which is the most recent LTS version, supported until 2019, whereas VV is supported only for 9 months.  Dependingon the specs of the hardware you may also find another DE version such as Xubuntu or Lubuntu run better than Ubuntu which needs a good 3D graphics card and requires plenty of grunt for the best experience.

Boot to the DVD or USB and choose to try without installing.  If it runs OK (it will be quite slow as a live system, particularly from a DVD) you can double click on the install to hard disk icon on the desktop.

Good luck!

---

### Post by MikeMecanic on 2015-04-27
Your not telling us what computer your dealing with?  Do you have at least an i3 chipset to run 15.04 Final Release?  If so, to achieve stability, choose the **LVM option (checkbox)** during installation.

---

### Post by Bucky Ball on 2015-04-28
DO NOT choose to install in LVM unless you absolutely know what you are doing and have a good reason to. If you are not au fait with it and completely aware of what it does and the consequences of using it, it can drag you in to a world of pain later on.

You do not have to start all over again from 'Try Ubuntu' desktop. There is an icon, or should be, on the desktop which says 'Install Ubuntu'. Lower specs, go for Xubuntu or Lubuntu, as suggested. Good luck.

---

### Post by mlvmhn on 2015-04-30
> **MikeMecanic said:**
> Your not telling us what computer your dealing with?  Do you have at least an i3 chipset to run 15.04 Final Release?  If so, to achieve stability, choose the **LVM option (checkbox)** during installation.

I am not sure what kind of computer i will install Ubuntu on. But the hardware should be enough since the computer is about 2 years old. I would guess about 2-3 GB of RAM, and i3 processor. 

Is Ubuntu the best choice for slower performance computers?

---

### Post by MikeMecanic on 2015-04-30
On a LVM manner and with systemd, Ubuntu 15.04 runs faster.  There is a little maintenance to do regarding to boot up partition (255MB) later on,  **but your friend will run a quite a stable machine**.  You'll not only get rid of Windows registries but among all, you'll get rid of that old fashion way of partitioning a hard drive.  Get the 15.04 ISO image here (1.1Mb file): [http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/)   

Choose amd 64 if you got a 64 bit computer (you should because it's not that old).  Otherwise if you got 32 bit, choose the other one (x86).
You must built an ISO image USB stick or a DVD.  Set the BIOS to boot-up in USB or press F9 or F1 (it's written on startup at the beginning) to boot-up with the USB stick of minimum 2Gb or a DVD.  Follow the steps, don't change the clock setting (New-York) and check the LVM option.  It takes 15 minutes to install it.
All the best,

---

### Post by MikeMecanic on 2015-05-01
```
[COLOR=#000000]You must built an ISO image USB stick or a DVD[/COLOR]
```

If you succeed under Windows to built an ISO USB or a DVD, **you should see in ti** (don't open it) **14 files **including the purple one  wubi.exe.  After installation and  first, beside the clock:System setting/Software & updates/Other Software:click on both Canonical Partners reload and close it. Upper left in the dash board (there is a good chance that you see it already asking to update), type S or soft for software updater and apply updates.  Reboot and do a second installation.  **You'll never reach stability unless you install 15.04 LVM from 15.04 LVM ** There's things to do on post-installation after...

---

### Post by Bucky Ball on 2015-05-01
> **mikael.hansson.967 said:**
> I am not sure what kind of computer i will install Ubuntu on. But the hardware should be enough since the computer is about 2 years old.

Not sure if I understand. You don't know what you're going to install on, but the hardware should be enough as the computer is about 2 years old?

> **mikael.hansson.967 said:**
> Is Ubuntu the best choice for slower performance computers?

No. Try Xubuntu or Lubuntu, but if the mystery computer has an i3 and 4Gb of RAM, Ubuntu will run fine. If less RAM, try one of the others.

---

### Post by mörgæs on 2015-05-01
If you are a beginnger then forget about LVM. It's a good approach but let's try to keep it simple for now. 

Just accept the default settings when installing.

---

### Post by mlvmhn on 2015-05-01
What is LVM?

---

### Post by gmoutso on 2015-05-01
You would install ubuntu on some (physical) hard disk partitions. It is usefull to actually have separate partitions for the root system (eg sda1) and the home folder (eg sda2) so that if you ever need to reinstall linux, you would just overwrite sda1 and not lose your home folder. And swap would get a separate partition. 

LVM changes this: it stands for Logical Volume Management. It is not the default in ubuntu. Essentially, you have one partition (eg sda1) which is then logically partitioned into smaller blocks called logical volumes. LVM comes with the notions of Physical Volume, Volume Group, Logical Volume. The benefit of LVM is that you can change the size of each logical volume, add (or remove) more space to the whole volume group, add/remove physical volumes to the lvm etc, something you cannot do with partitions *on a live system*. 

Another benefit of lvm is the lvmcache, which allows you to use a fast SSD as a cache. It is the only reason I installed ubuntu on an lvm. I wouldn't say my experience was difficult (but I have quite a few years of linux user experience)... Furthermore, this was a fresh install so I could experiment a bit and see if it works. If you are new to ubuntu/linux it would be far easier to accept the default installation (which does not use lvm). For my lvmcache experiment see ubuntuforums.org/showthread.php?t=2247232.

---

### Post by mlvmhn on 2015-05-01
K, which version of Linux is best for a all new user coming from the Windows world?

---

### Post by MikeMecanic on 2015-05-01
**The more peoples that run Ubuntu 15.04 alone the better Ubuntu 16.04 LTS will b**e** (April 2016).**  If you got 4 Gig of Ram, shoot for Ubuntu 15.04 Final Release.  If you only got 2, your border line.  Give it a try, it takes 15 to 20 minutes to do so with an USB stick.  Otherwise,for older machine (I don't think it's your case) Lubuntu is more suitable.
Take care,

---

### Post by mlvmhn on 2015-05-01
k, when will the final release of 15.04 be available for dl?

i am running "Vivid Vervet" atm, and is very satisfied with it. 
Chances are that i probably will install it on my friends laptop. 

Are Lubuntu similar to Ubuntu in forms of UI?

---

### Post by MikeMecanic on 2015-05-01
The link on post 12 is the daily image of Ubuntu 15.04 final release (there ain't nothing else available since April 21st).  Lubuntu is a lighter O/S.  Good luck and welcome in the Linux family.

---

### Post by mlvmhn on 2015-05-01
K, what are the system requirements for Lubuntu / Ubuntu? 

Will we need more than 4 GB RAM, and a dual-core processor for regular use w/ the OS?

---

### Post by MikeMecanic on 2015-05-01
You don't have to worry, just choose the default installation and check the LVM option.  You can do almost anything with 4Gig of Ram + you'll get a Swap partition of 4.2 Gig with the default installation.
[http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by mlvmhn on 2015-05-01
K, when i boot from the ISO installation CD, i get to format my hard drive and wipe it all clean?

I dont want any traces of the Windows crap left on it.

---

### Post by Bucky Ball on 2015-05-01
No one has mentioned that 15.04 is an interim release that runs out of support nine months from now, at which point you will need to upgrade the OS via the net or install media or reinstall. 14.04 LTS, out since last April and rock solid, is a long-term support supported until April 2019. I, personally, don't think a wet behind the ears release that was released a few days ago is a good place for a newbie. But that's just me. ;)

On lower spec machines, Xubuntu or Lubuntu are the go. Ubuntu uses the Unity desktop, which people seem to love or hate, while Xubuntu and Lubuntu use xfce and lxde respectively, more like Windows and possible a better place to start anyway. Good luck.

---

### Post by MikeMecanic on 2015-05-01
The Mikael friend computer remains a mystery?  Indeed, in October or around October will have to switch to 15.10.  I see it more like something to increase their friendship.  I didn't format my hard drive when I switch to Ubuntu 10.LTS in January 2011.  
At the beginning, Install this third party software should remain unchecked.  Ubuntu comes full equip and it cause me problems in the pass when I install it. ** if you don't have enough RAM you will have to consider the advice of Bucky regarding Xubuntu or Lubuntu.**

You won't be able to create an ISO image from a CD because the file is 1.1Gb. You need a DVD.  For your desire of removing Windows, the installation will take care of that.  Don't waste your time and energy.  You won't get a better result because to achieve stability you'll have to install it twice. 
All the best,

---

