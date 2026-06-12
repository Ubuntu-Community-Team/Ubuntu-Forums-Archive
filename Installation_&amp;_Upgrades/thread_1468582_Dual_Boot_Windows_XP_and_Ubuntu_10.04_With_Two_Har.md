---
title: "Dual Boot Windows XP and Ubuntu 10.04 With Two Hard Drives"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by RockScissors on 2010-05-01
Hello.  I'm new to the whole Linux scene.  I got a virus on Windows a few days ago and really made me want to switch to Linux.  I downloaded the new 10.04 LTS ISO and have Daemon tools (do I need to burn it to a CD to install?) and have a an empty hard drive.  Basically, I want to install Ubuntu onto my F: drive (my small 30GB hard drive, slave) and keep Windows on my C: (large 160GB drive, master) and dual boot.  Can someone give me simple, step by step instructions to install Ubuntu to my F: drive and leave Windows on my C: drive?  From what it looks like, if I run the Ubuntu installer, it should take care of everything and allow me to choose to boot to Windows or Ubuntu when I turn the computer on, correct?  

Thanks for helping a beginner out.

---

### Post by thermopyl on 2010-06-01
Hi

I have the same requirement. My approach is that I have Vista on 'C' and want to install Ubuntu on 'D'.

I want too boot as a default first option to Ubuntu, but have Vista as an option in the Grub.

I plan to unplug my C drive and then install Ubuntu directly onto 'D'. I then change the BIOS to boot to 'D'. If you are doing this for the first time, follow the instructions!

Once i test the ubuntu boot, I will then reconnect 'C'.

I suspect that I will need to edit the menu.lst file to reference the 'C' drive...

...will this work guys??

---

### Post by darkod on 2010-06-01
> **thermopyl said:**
> Hi

I have the same requirement. My approach is that I have Vista on 'C' and want to install Ubuntu on 'D'.

I want too boot as a default first option to Ubuntu, but have Vista as an option in the Grub.

I plan to unplug my C drive and then install Ubuntu directly onto 'D'. I then change the BIOS to boot to 'D'. If you are doing this for the first time, follow the instructions!

Once i test the ubuntu boot, I will then reconnect 'C'.

I suspect that I will need to edit the menu.lst file to reference the 'C' drive...

...will this work guys??

It was really better to open your own thread than posting on a 4 weeks old one. However...

First you have to make a difference that C: and D: in windows are not always separate physical disks. MS calls them drives but that is very misleading because they can be partitions on single disk.

But I guess you should know whether you have one or two disks. There is no need to unplug the windows disk but you can do it if it makes you more secure. Just when you plug it back in make sure the ubuntu disk is still first in boot order because you need to be booting from it.

On first boot after you plug the windows disk ubuntu will still not know it's there. Once you boot ubuntu, in terminal do:

sudo update-grub

That will detect windows and create the dual boot grub menu.

---

### Post by thermopyl on 2010-06-01
Yeah fair point - thought it might help the guy who posted originally, that was the logic anyway

Thanks for the answer - deffo seperate disks so sounds nice'n'simple!

---

