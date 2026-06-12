---
title: "Installing Ubuntu External Drive"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Mr|C on 2007-05-09
This has been asked a lot of times before. I'm sorry, but none complete fitted my actual question.

I just bought a Digital Western 250GB hard drive, and decided I'd put Linux on this one, instead of partitioning my internal one. (My parents said they'd prefer to use Windows). 

There was a guide about it, and I'm not 100% sure if it applies to me because I WANT Linux to boot up ONLY when my external HD is connected. So, surely it doesn't matter that GRUB goes in to the internal HD if I set my BIOS to load from any USB device first, then my internal HD.

The guide also said I can't use the LiveCD to install Ubuntu on to my external HD. Does this apply to me? 

**_Anymore important information would be appreciated._**

***_<3_***

---

### Post by fotios on 2007-05-09
You should first check out your BIOS. See that you can make it boot from usb port, configure your port and remember to connect the Drive in the specific port always. Then, when you install your linux, be careful on the boot sector, f.e. in FC you can choose if you want to install a boot loader or if you want to make start up disk.See what option best suits your needs and good luck!

---

### Post by Mr|C on 2007-05-09
> **fotios said:**
> You should first check out your BIOS. See that you can make it boot from usb port, configure your port and remember to connect the Drive in the specific port always. Then, when you install your linux, be careful on the boot sector, f.e. in FC you can choose if you want to install a boot loader or if you want to make start up disk.See what option best suits your needs and good luck!

I just checked my BIOS. I can definitly boot from a USB device and I can definitly change the order in which the booting happens. That is no problem for me right now. 

However, what do you mean by the boot sector? I'm relatively new to Linux. The version of Ubuntu I'll be using is Edgy Eft. 

My ideal scenario of booting in to Ubuntu is that when my USB HD is not connected, it will auto boot to Windows. When it is connected, it will auto boot to Ubuntu. I'm sure this is possible with just configuring the BIOS which is as easy as pie, but I'm not sure if it's that simple. (As if anything ever is).

---

### Post by Mr|C on 2007-05-09
Anybody?

---

### Post by bulldog on 2007-05-09
Yes,you can install ubuntu to the external disk with no problems at all.

You have to install GRUB [at the end of the install] ** on your external disk as well**
By default it will be installed on (hd0) which is your internal hdd,you don't want to do this,change the (hd0) into (hd1) and all should be as you want it to be.

GRUB will only show if you boot the external hdd,otherwise it will boot right into windows.

---

### Post by Mr|C on 2007-05-09
> **bulldog said:**
> Yes,you can install ubuntu to the external disk with no problems at all.

You have to install GRUB [at the end of the install] ** on your external disk as well**
By default it will be installed on (hd0) which is your internal hdd,you don't want to do this,change the (hd0) into (hd1) and all should be as you want it to be.

GRUB will only show if you boot the external hdd,otherwise it will boot right into windows.

Thanks a lot :)

Just one last final question, how do I change the hd0 in to hd1?

---

### Post by bulldog on 2007-05-09
I know you don't have a choice with the Dapper live cd,you can choose when you install from the alternate cd.

If I remember correctly,you can choose with Edgy and Feisty live cd's where you want to install GRUB.
But I know for sure you have this option with the alternate cd install from all of the ubuntu distro's.

When GRUB will be installed,a dialog opens which show the default (hd0) option.
Take a good look and you should be able to change this option into (hd1) maybe a drop down box or something like that.

In the case it goes wrong,there's nothing lost,however,you can easily reinstall GRUB to the external hdd with any live cd .
In that case it would be handy if you have a windows install cd to fix the windows MBR.

So don't be afraid,it can be fixed if you make a mistake.

---

### Post by Mr|C on 2007-05-09
> **bulldog said:**
> I know you don't have a choice with the Dapper live cd,you can choose when you install from the alternate cd.

If I remember correctly,you can choose with Edgy and Feisty live cd's where you want to install GRUB.
But I know for sure you have this option with the alternate cd install from all of the ubuntu distro's.

When GRUB will be installed,a dialog opens which show the default (hd0) option.
Take a good look and you should be able to change this option into (hd1) maybe a drop down box or something like that.

In the case it goes wrong,there's nothing lost,however,you can easily reinstall GRUB to the external hdd with any live cd .
In that case it would be handy if you have a windows install cd to fix the windows MBR.

So don't be afraid,it can be fixed if you make a mistake.

Once again, a massive thanks. I'll be using Edgy LiveCD but on the last install, I don't remember an option of where to install GRUB. 

However, I don't have my original Windows XP install CD. Is this a big problem?

---

### Post by bulldog on 2007-05-09
No BIG problem,just a problem :) 
There are other way's to restore your MBR,but any windows install disk would be easier.

If you want to be sure you get the option to choose were to install GRUB,download the alternate cd.

---

