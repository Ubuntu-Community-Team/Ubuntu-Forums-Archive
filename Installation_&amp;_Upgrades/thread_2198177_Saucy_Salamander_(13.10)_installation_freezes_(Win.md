---
title: "Saucy Salamander (13.10) installation freezes (Windows 8 dual boot UEFI)"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by jaimeda104 on 2014-01-07
This is my first post in the forum, hope I can explain my situation in a good way.

I just received a Gigabyte P34G laptop with Windows 8 pre installed in two different drives (system = SSD 128 GB and data = HDD 1TB). As I regularly do, I created a bootable USB drive using unetbootin. The Ubuntu version I am trying to install is 13.10 with root partition in SSD and home partition in HDD. I have done everything I know I need to do for a UEFI dual boot installation in this case: 

- Removing hibernation (at the same time removing Fast Boot), because of space I needed in the SSD.
- Disabling Secure Boot from UEFI BIOS.
- Unallocating space from both SSD and HDD for / and /home.

After all this I boot from the USB drive and I enter the "grub" menu with the options: Try Ubuntu without installing, install Ubuntu, etc. So I try the first option Ubuntu starts loading (screen with Ubuntu logo and five dots). Suddenly all five dots turn red and screen freezes (at least that is what it seems). The USB drive works perfect in my desktop running Windows 7 + Ubuntu 12.04 with "regular" BIOS. Thank you for your time.

---

### Post by oldfred on 2014-01-07
I see it has nVidia. Is it dual video or just nVidia? And if dual can you control which video you boot with?

If booting with nVidia you need nomodeset. With UEFI you get grub menu like after an install and have to manually add nomodeset to grub entry. Use e for edit, scroll to linux line and replace quiet splash with nomodeset. But if Intel other options and perhaps settings in UEFI/BIOS may be required.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

See also info on Ultrabooks in link in my signature.

---

### Post by jaimeda104 on 2014-01-08
Hey oldfred, first of all sorry for the late reply (I did not noticed your fast answer yesterday). Thank you for the help, I have seen you are dealing with a lot of different problems affecting users in this matter. 

I tried using NOMODESET and everything was going well until I received the following message during boot: "error found in 1 file!". After that it asked me for any key to reboot. The thing is I am pretty sure my live usb is ok, I have checked the checksum for the ISO file and everything ok, I have booted to the live usb from a desktop and also ok. 

I run it a few more times and another result is just a black screen after all the boot phase (at least I think it finished). I can use Ctrl + Alt + F1 to enter a terminal and finally I can work something out. I have never had this issue before so I would like to know, what now? Do I need to install video drivers for the Nvidia card? or is there a better way to go?

---

### Post by jaimeda104 on 2014-01-08
Ok after digging in the internet for some time I found a very good blog (David Overton's blog) specifically talking about Ubuntu installation in a Gigabyte P34G ([http://overtond.blogspot.fr/2013/10/ubuntu-on-gigabyte-p34g-ultrablade.html](http://overtond.blogspot.fr/2013/10/ubuntu-on-gigabyte-p34g-ultrablade.html)). Here I learned this two things:

- I can install Ubuntu 13.10 without disabling secure boot.
- Disabling 3D acceleration from the BIOS fixed my black screen problem (I suppose that oldfred was right in the sense that there was a problem with the graphic cards).

This time I did not use NOMODESET or any other boot option. Thank you again oldfred for helping me out.

---

### Post by oldfred on 2014-01-08
Thanks for update on what works. Is the 3d graphics really the nVidia chip on/off. Then is that just booting or after you install bumblebee can you turn it back on?

With 13.10 there is a bug in grub that with secure boot on, you cannot boot Windows from grub menu. You should be able to boot both from UEFI menu. Or turn secure boot off.

---

### Post by jaimeda104 on 2014-01-08
Ok, I just finished installing Ubuntu 13.10 in dual boot with Windows 8 without disabling Secure Boot and what can I say, everything is ok and grub is working fine (I installed Ubuntu in UEFI mode) even though I was already prepared for using Boot Repair from the live USB. As I said, the only thing that I needed to do was to disable the 3D acceleration graphic in the UEFI settings. Also I am using an SSD + HDD dual boot with this config:

SSD (128 GB): 
- Recovery Windows (order of MB)
- Uefi partition (order of MB)
- WINDOWS (C: ) (around 60 GB)
- / (around 60 GB)

HDD (1 TB):
- DATA (D: ) for Windows (around 500 GB)
- /data for Linux (around 500 GB)

I followed this config from one of your answers in another topic. The thing is I had no problem with the /data partition, it automatically mounts at startup. Now I am going to make some symlinks for my /home to my /data partition in order to just leave the .xxxx files (for performance).

I have not tried to enable the 3D graphics again and neither installed bumblebee yet, that is my next step, I will post the results here. (I marked the topic as SOLVED, now I do not know if this is correct, please correct me if I am wrong).

---

### Post by oldfred on 2014-01-08
Boot-issues is solved. 
But further info to help others with your model computer always helps them.

---

### Post by jaimeda104 on 2014-01-09
Ok, I re enabled 3D acceleration in UEFI settings and I am happy to say that everything is fine. Still haven't installed bumblebee but at this point I don't think I will have a problem.

---

### Post by Bucky Ball on 2014-01-09
Bit off topic but just wondering ...

You have / on the SSD and /data for Linux (around 500 GB) on the HDD. On / you are going have a default /home partition as I presume the /data for Linux partition has not been assigned to Ubuntu as a /home partition. 

One tip (and I think I got this from oldfred origianlly) is to create your /Documents, /Music, /Video, etc. directories on the /data for Linux partition, delete the corresponding directories in your default /home directory in / and create symlinks to the directories on the /data for Linux partition inside your /home directory in / instead. See here:

[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

Just thought I'd mention it. Hope it makes sense. Not sure where you've got things pointing, but if you are keeping your personal data in the /home directory inside / then the SSD is going to get filled up pretty quick. You don't want data on there anyhow, just the OSs. ;)

---

### Post by jaimeda104 on 2014-01-09
Hey Bucky Ball, first of all thanks for the advice. I did exactly what you just said following oldfred advice in other thread. I created just a / partition in the SSD because I wanted to have all the little config files in /home on the SSD. With the large folders in /home (Music, Videos, Documents, Downloads, and others), I moved them to /data and created symlinks in /home. So in conclusion, I have the configuration you just suggested. Everything is running well and the speed in which I can reach my desktop from startup is amazing.

---

### Post by Bucky Ball on 2014-01-09
Good news! The symlink idea is great and, of course, if you decide you want to install another OS you can simply do the same thing; create symlinks in the new /home directory to the folders your current install is symlinked to, then regardless of what OS you have booted, you are always looking at and working on the same files, no redundancy or duplication.

Enjoy and good job! ;)

---

