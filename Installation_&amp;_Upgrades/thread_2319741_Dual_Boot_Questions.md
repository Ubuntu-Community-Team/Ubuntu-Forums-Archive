---
title: "Dual Boot Questions"
date: 2016-04-06
forum: Installation &amp; Upgrades
---

### Post by maineman2 on 2016-04-06
Hi I have a couple dual boot questions. My laptop is kind of old. I bought it from dell w feisty fawn installed. Its 32 bit. I have resisted buying  a windows laptop for years now but it looks like I will finally  have to bite the bullet and buy windows and do a dual boot. So my questions are can I run windows 8 on a 32 bit computer?I tried to do an opensuse ubuntu dual boot but could not resize my partition I encrypted my hard drive. Can I unencrypt my hard dive, then install windows? Most windows dual boot instructions I see are for windows installed first. Would it be easier for me to install windows and run ubuntu from a usb drive?Or even a 2nd hard drive? I will only use windows for 1 or 2 things. I really only use my laptop for ripping cds and downloading music. So I don't have the need or the money at the moment  to buy a new computer. I saw a site called getintopc where they advertise free windows 8.1, does anybody have experience with this?So Thanks for any advise  Dan

---

### Post by RobGoss on 2016-04-06
Hello and welcome Dave, From what I gathered from your post you're wanting to dual boot correct?

If you're planing to get a new computer then you might want to read this on how to setup a dual boot, most of the new computers today have UEFI bios and will have to be changed accordingly

**Dual Boot UEFI **
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have a 32-bit machine I don't see why **Windows 8 **can't run on it as long as you have the correct specs required.

I'm a little confused about your post you stated you wanted to buy a Windows computer but your asking if you can install Windows 8 on it, why would you want **Windows 8, **when** Windows 10,** should be on the new machine you buy, them all you would need to do is install Ubuntu and following the instructions from your link I provided and dual boot as you requested.....

A far as encrypted hard drives I'm not an expert in this sort of thing but I'm assuming if you can encrypted your drive you should be able to reverse it.

Here are the Ubuntu System Requirmements
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by maineman2 on 2016-04-06
Well i have resisted buying a new one and just decided to do a dual boot on my old one. i will buy windows 8.Would it just be easier to install windows 8 then  run ubuntu on a usb on my old laptop? Dan

---

### Post by RobGoss on 2016-04-06
What are the specs for your old machine it will help to know what kind of machine you have and if it meets standards

---

### Post by maineman2 on 2016-04-06
2 intel  T2080 processor 2 ram for whatever reason i can get the system specs on the screen but cant copy and paste them.

---

### Post by RobGoss on 2016-04-06
Are you planing to use a older computer or are you  using a new machine you were not clear in your first post

---

### Post by Bucky Ball on 2016-04-06
You have a few options with a new machine. Dual-boot, yes, install Windows first then Ubuntu, no need to run Ubuntu from a USB or whatever (just a note: if you intend upgrading Win8 to Win10, install, upgrade and then install Ubuntu as the Win10 upgrade screws up the boot if you install Ubuntu before doing it). 

Another option is to install Ubuntu and run Windows as a virtual machine using Virtualbox. This is easier than it sounds.

With your old machine and 2Gb of RAM, you might want to try a lighter flavour, Xubuntu or Lubuntu should run well on that machine.

(BTW, preinstalled Windows on any laptop you buy is free pretty much. Wouldn't worry about 'free Windows' offers. Laughable. They give it away anyhow. All you need to do is buy a laptop. Try asking a store to remove Windows first and make a discount as you don't want it! There are user experiences of that posted here and elsewhere.)

---

### Post by grahammechanical on 2016-04-06
You have an old computer with a version of Ubuntu that is years out of support. In my mind the simplest method would be to install Windows 8 and then install the latest version of Ubuntu. Version 16.04 LTS will be released at the end of April. It will be supported for 5 years.

You need to upgrade to a supported version of Ubuntu and the best way to do that is to  do a fresh install of the latest version. It is not a simple process to do an internet upgrade from an out of support version of Ubuntu to a supported version. Ubuntu 7.04 (Fiesty Fawn) became out of support October 2008. You will have to work your way through 9 unsupported Ubuntu releases to get to 12.04. So, I recommend a fresh install.

If you install Windows 8 after Ubuntu is installed then the Windows installer will over-write the Linux boot loader with the Windows boot loader. You will then not be able to load Ubuntu. The solution is to load a Ubuntu live session, install an application called Boot Repair and let it re-install the Linux boot loader (Grub).

I once installed a 32 bit version of Windows 8 preview edition. So, there will be a 32 bit version of Windows 8. 

Regards.

---

### Post by Bucky Ball on 2016-04-06
> **grahammechanical said:**
> 
You need to upgrade to a supported version of Ubuntu ...

+1. Doesn't matter how you look at it, this is the bottom line, but looks like you're heading there anyway, one way or the other. ;)

---

### Post by RobGoss on 2016-04-07
Any new computer you buy these days will have a 64- bit version of Windows unless you buy it used there fore depending on how old the machine is it might have a 32-bit version on Windows

I have doing a bit of research on used machines and they do have recycled computers with out any operating systems on it if this is something you might be interested in and I priced one with about 2-GB of ram and a 250-GB hard drive for about $60.00 which I thought was a reasonable price, just an idea.

As far as Ubuntu goes as everyone recommend you should install the latest version this way you bypass all the headaches that come along with upgrading.

---

### Post by maineman2 on 2016-04-07
I have the latest version of Ubuntu mate on my laptop looks like I will buy windows 8 then reinstall everything. As directed above. Thanks Dan

---

