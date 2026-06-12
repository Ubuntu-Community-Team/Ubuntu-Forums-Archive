---
title: "How to Multi Boot the Easy Way With GRUB2"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by Herman on 2010-04-25
:) I was just talking with one of my friends and of course we're all looking forward to the upcoming release of Ubuntu Lucid Lynx LTS.
My friend wants to resize Windows Vista and install Ubuntu Lucid Lynx after it in a dual boot configuration.
 After that he wants to be able to install other Linux distros just for fun.  
He's a little worried about how he's going to manage to set up multiple booting in GRUB2 though, and asked me if I thought it would be harder than with Legacy GRUB.

There are still a lot of people who are a little worried about how they will cope with GRUB2 when Legacy GRUB was more than enough of a learning curve for most people. 
The general perception is that GRUB2 is supposed to be harder and that might be scaring some people away from the latest Ubuntu releases.
GRUB2 isn't harder at all, that's a myth, GRUB2 is actually easier then Legacy GRUB, (at least most of the time, and for normal uses). 
We don't need to go editing our GRUB menus by hand any more and we mostly only need to know one or two commands now.

Here's a simple trick I tell my friends for an easy way to multi-boot Ubuntu with most other operating systems using GRUB2. 
Probably I should have posted this in here in the forums earlier, but for some reason it didn't occur to me until now, and I have a few minutes of idle time on my hands, so here it is.

**You will need:** a USB flash memory stick and your Ubuntu CD plus the CDs for other operating systems you want to multi boot with. A 16 or 8 GB flash memory would be preferred, but you should be able to get away with a 4GB flash memory stick if that's all you have.



**1. Install Ubuntu** in your computer, by itself or dual boot with other operating system(s), it doesn't matter, just install Ubuntu, and of course install GRUB2 to MBR.

**2. Install Ubuntu in your USB flash memory stick** in the same manner as you just installed it to hard disk. 
NOTE: Install real, complete, normal Ubuntu operating system which boots with GRUB2, NOT a 'persistence' type of USB installation, (which boot with syslinux). 
Remember in step 7 of 7 to hit the 'advanced' button and install GRUB2 to the flash memory stick's MBR and not to the computer's first hard disk MBR.

**3. Install any other distro(s) you like**. It doesn't matter where they install their boot loader for the time being, the operating system's own partition would be ideal, but for most distros, GRUB2 wil be booting them directly later anyway, so mostly it won't matter too much where their boot loader gets installed. To MBR if you have to, it won't matter.

**4. Reboot your computer with the Ubuntu flash memory stick** inserted in a USB port and press whatever key causes the computer to bring up a BIOS boot menu. 
For some computers it's 'Esc', for others it's 'F2', many use 'F8' or 'F12'.
A few computers might even use some other key like the 'Tab' key or some other, to bring up the BIOS boot menu.
Some computers don't have any BIOS boot menu. In that case you would need to have a boot CD instead, to boot the USB drive's GRUB2.
[COLOR=Blue][COLOR=Navy]If your USB flash memory stick already has an entry to boot your internal hard disk's Ubuntu, (it should have), select that and you can skip to step 6.[/COLOR]
[/COLOR] 
**4. Run 'sudo update-grub'**, once you have Ubuntu in the USB flash memory stick up and running, and let the USB stick's GRUB2 detect all of your operating systems in the computer. 

**5. Reboot the USB for the second time**, again press whatever key is necessary to bring up a BIOS boot menu and again select and boot your USB drive. 
This time the USB's GRUB2 menu will include your Ubuntu install's you can choose any of your computer's internal operating systems.
[COLOR=Red]Some computers BIOSes might not allow GRUB in a USB to detect internal hard drives and vice-versa, so this trick might not work for everyone, but it should work for most of us.[/COLOR]

**6. Choose Ubuntu and boot into it.** (Your internal hard disk installation I mean).

**7. Run 'sudo update-grub'**, now that your internally installed Ubuntu is up and running, for Ubuntu's GRUB2 to automatically scan your computer for other installed operating systems and write entries for them in your GRUB2 menu.
[COLOR=Navy]NOTE: You can leave the USB plugged in to be automatically included or unplug it first, so it won't be included, it's up to you.[/COLOR]

**8. Run 'sudo grub-install /dev/sda'**, to re-install Ubuntu's GRUB2 to MBR again.
NOTE: You might need to check first to make sure /dev/sda is your first hard disk, some computers might number USB drives before internal drives, and if you have a mixture of IDE and SATA drives inside the computer it can also be confusing as to which kind of drives are counted first.
[COLOR=Navy]If you still have Ubuntu's GRUB in MBR, you can skip this step, but if you had to let some other distro install its boot loader to MBR, you will probably want to do this.
[/COLOR] 
**That's it.** Enjoy multi-booting with modern versions of Ubuntu featuring the new GRUB2 boot loader. 
[COLOR=Navy]For some people this would have only required four or five steps.[/COLOR]

You can reformat your USB flash memory stick to use for something else if you want, or keep it as a utility disk and install GParted in it and other softwares in case you ever want to use it for maintenance tasks or other operations on your installed Ubuntu or other OSes. It makes a good portable operating system and you can use it to boot up and/or repair other computers belonging to friends and relatives. :)

---

### Post by Herman on 2010-04-25
:P Another, even easier way would be to:

[B]1. Install Ubuntu
[/B]
**2. Make your own GRUB2 Rescue Disk** with the grub-mkrescue commend, see [How To make Your Own ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")[GRUB2 Boot CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM") .

[B]3. Install your other operating system or distro(s).
[/B]
**4. Use your GRUB2 Rescue Disk to reboot into Ubuntu.**

**5. Run 'sudo update-grub'** and possibly 'sudo grub-install /dev/sda' if you need to.

---

### Post by arpanaut on 2010-04-26
Excellent information for all!

Well Done & Thank You

Your website on dual booting and Grub issues has saved me many times!

Great timing for this post/tutorial.:!:

---

