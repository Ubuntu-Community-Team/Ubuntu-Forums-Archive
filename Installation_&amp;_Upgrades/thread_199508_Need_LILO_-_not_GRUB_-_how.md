---
title: "Need LILO - not GRUB - how?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by zambizzi on 2006-06-18
I need to use LILO as my boot manager instead of GRUB - I've got a piece of hardware that has just *never* booted w/ GRUB...and just now failed to boot Ubuntu 6.06 w/ GRUB after trying.

How do I customize the installation to do this?

Thanks!

---

### Post by Lux Perpetua on 2006-06-19
I think the "alternate" install CD allows you to install LILO instead of GRUB. If I remember correctly, you just need to select "install LILO" from the installer main menu.

---

### Post by zambizzi on 2006-06-19
I don't think so...I just tried it in both text mode and OEM mode w/ the alternate CD and there's no option to "...install LILO" (nor is there a "main installer menu"...just the text-mode wizard.)

What am I missing?  It's not at all obvious if it's available on the alternate CD.

Thanks again!

---

### Post by Lux Perpetua on 2006-06-19
There is actually a main menu on the install CD. You get sent to it if you select "Go back" at any stage. For example, when it enters the partitioning step, you can choose "Go back" (at the bottom) instead of continuing with the partitioning, but you don't need to "go back" at exactly that point; any other point should do just as well. I didn't test this, but it would probably be best to go through the installation normally and then "go back" right when it prompts you to install GRUB, and then install LILO from the main menu and complete the remaining steps. 

You'll know you're at the main menu when it says > This is the main menu for the Ubuntu installer.

Choose the next step in the install processOne of the options in the menu is> Install the LILO boot loader on a hard diskI know it's there because I just checked.

---

### Post by aqwabawks on 2006-06-21
Just curious, is the LILO boot manager any different looking than the Grub one (also for some reason I have 4 options to select Ubuntu from Grub, when I selected either it started Kubuntu, is it possible to change that?)... I prefer a graphical boot manager, and if Lilo is like that, is it possible to install LILO as the boot manager after Ubuntu has been installed?

---

### Post by Herman on 2006-06-21
Hello, aqwabawks
A good graphical boot manager is  [GAG Boot Manager]("http://gag.sourceforge.net/")
and you can see how to use GAG and how to install either Lilo or GRUB to your Ubuntu partition after install on this page, [*click here*]("http://users.bigpond.net.au/hermanzone/p12.htm").
It is possible to change GRUB in almost any way you want by editiing  your /boot/grub/menu.lst file. For more info about how to use GRUB, [*click here.*]("http://users.bigpond.net.au/hermanzone/p15.htm") 
Regards, Herman :)

> I don't think so...I just tried it in both text mode and OEM mode w/ the alternate CD and there's no option to "...install LILO" (nor is there a "main installer menu"...just the text-mode wizard.)
What am I missing?  It's not at all obvious if it's available on the alternate CD.zambizzi, to see illustrations of the 'alternate' cd installation, click one of my signature lnks. To see how the bootloader install options work, [*click here*]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").
Regards, Herman :)

---

