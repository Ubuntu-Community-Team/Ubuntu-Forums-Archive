---
title: "Natty is not starting"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by jpwie on 2011-06-03
Hello,

today I've upgraded my Maverick installation to Natty using the "do-release-upgrade" command. The upgrade completed successfully according to the tool, but after I rebooted my system and chose "Ubuntu, with Linux 2.6.38-8-generic" in GRUB my screen went black showing an blinking underscore and rebooted after approx. five seconds.
When I entered the Safe Boot environment the last thing my system did before rebooting was attaching the SCSI devices but didn't show any error message.
Same with (successfull) clean installation from Desktop-CD and Alternate-CD on a clean HDD.
After I upgraded I still had access to the "Previous Linux Versions" option in Grub, but when I started the Maverick kernel my system displayed a blinking underscore for about 30 minutes - until I shut it off. In the Safe Boot environment of the old kernel the "Failsafe X" option resulted in the blinking underscore again.
This happens with the final version, but also happened with the alpha and beta versions.
Ubuntu is the only OS on my PC.
I only tried this with the GNOME version of Ubuntu, but will try to use Xubuntu now.

By the way: I have an Pentium 4 HT, 2 GiB of RAM and a PCI 2.3 based AMD/ATI Radeon 4350 HD in an DELL Dimension 3100 if that helps.

Can anybody please help me to get my PC working again?

Joshua

---

### Post by jpwie on 2011-06-03
UPDATE: The same thing occured to me when I tried booting from an Xubuntu CD in both live mode and installation mode.
I suppose I should try Linux Mint now…

---

### Post by ChrisKu on 2011-06-03
> **jpwie said:**
> UPDATE: The same thing occured to me when I tried booting from an Xubuntu CD in both live mode and installation mode.
I suppose I should try Linux Mint now…
 
Don't know if you've got a CD with a previous Ubuntu Version (e.g. 10.10) at hand and try that. It might (cough) after all be possible that you do have a hardware issue.

---

### Post by ronparent on 2011-06-03
Linux mint is also based on Ubuntu and you may find with the same problems. Have you tried booting with various kernel options. Check the section on Commnon Kernel Options in this reference: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

You might start with 'nomodeset', though depending on the age of you computer, the maker of your graphics chipset various boot options may be needed. Tedious I know, but, you have to append a boot option or various combinations of them to a menu boot line until something works. If you have only the one install on your system you  have to strike the space key immediately following your system bios output to bring up a boot menu. Instruction on how to edit the boot line are on the menu screen as well as the reference I gave you. 

Although you initially got to 11.04 through an upgrade, It is usually necessary to ferret out needed boot options with a live cd. Usually (but not always) if you can get the live cd to boot you will be able to boot the installed system with the same boot options as with the same boot options as needed with the live cd, if any. You will have to eventually edit /etc/defaults/grub to make any required options permanent. Post how you make out and good luck.

---

### Post by jpwie on 2011-06-05
Thanks for the reply, both of you.
Using a Maverick CD worked quite well in the past. I had this issue with Natty alphas as well.

Using "nomodeset" with the Xubuntu Live CD actually did something:
Plymouth did show, for some seconds the message "Welcome to Ubuntu 11.04" appeared on the screen, but the screen went black after that. It seems that the underlying system is working because when I hit the power button of my PC the CD was ejected from my drive and when I hit enter it shut down. Entering ```
xinit
``` before shutting down was of no use.
When I tried any of the VGA modes displayed when appending ```
vga=ask
``` the issue occured again.:(

Interesting thing: I had this problem with a Fedora 15 Live USB but managed to install Fedora in the low-graphics mode – it actually worked! A Fedora 14 CD even worked in the normal live mode. I've got an idea: maybe the kernel of the new distros are not compatible with my system.
Ubuntu 11.04 uses 2.6.38, Fedora 15 uses 2.6.38, but Ubuntu 10.10 and Fedora 14 used 2.6.35.
I might try booting different live distros with 2.6.38, but I don't know which other distros include 2.6.38 :confused:
Any ideas?

Thanks for your help and greetings from Germany!
Joshua

---

### Post by ronparent on 2011-06-05
When you edit a boot line to insert a boot parameter it is often useful to erase the 'quiet splash'. The last lines of messge often give a clue as to what may be causing a glitch with your system.

---

### Post by jpwie on 2011-06-06
Hello folks,

I was able to narrow down the issue to my add-in graphic card. When I removed it and used the on-board chip the issue seemed to be solved. Problem is: my on-board chipset is not really good which means it is not sufficient for games. Maybe the reason for the problem with my Radeon HD 4350 is the new driver/support for the Radeon HD 6000 series which is included in the 2.6.38 kernel. I think Linux tries to apply this driver for my graphics, but ot doesn't work since I don't have a HD 6000 card.
The problem might be solving with blacklisting the HD 6000 driver with kernel parameters. But i don't remember the parameter for driver blacklisting and I don't know the driver name for the HD 6000 series.
By the way: I tried to boot the Xubuntu CD with my brother's PC with my graphic card attached. This didn't work as well.
Another idea would be using a different kernel such as 2.6.37. But how do you use another than the default kernel? Is it sufficient just to copy the kernel data to /proc and enter the different kernel version in GRUB boot parameters?

Greetings from Germany!
Joshua

---

### Post by tubunt on 2011-06-11
Hello, 

I am facing the same problem. Except that I am using VirtualBox. I have just booted the VBox using a 10.10 CD and retrieved some of the necessary files on my virtual disk. Its very annoying.

Can somebody help with what I need to change so that I can boot Natty. I am using VirtualBox on a HP 8540w.

thanks in advance

---

### Post by linuxinstalledfromhdd on 2011-06-11
You can using VMWare.  That should work.

---

### Post by tubunt on 2011-06-11
> **linuxinstalledfromhdd said:**
> You can using VMWare.  That should work.

Can you pls share steps to convert a VirtualBox vdi to VMWare? And I think this problem is related to upgrade from Maverick to Natty, somebody mention issue with graphics drivers - but nobody mention a virtualization technology issue...

---

### Post by tubunt on 2011-06-11
As I was already booted from CD, I did the following from reading around the forums:
- mounted my old partition to /mnt
- set acpi-off for GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub
- umount partition
- shutdown
- remove iso from cd (remember I am using VirtualBox)
- boot

In the grub menu, everything was fine except a message about my hardware not able to support unity. I am upgrading nvidia and will reboot to see what happens.

---

### Post by jpwie on 2011-06-27
I tried to circumvent the issue by compiling a custom kernel (2.6.39.1, 2.6.36.8 and 2.6.36.4) in which I compiled the VESA VGA and the Radeon drivers into the kernel. When I booted my custom kernel the issue seemed to be solved, but a ext3fs error appeared: «Error: /dev/sda5: couln't mount because of unsupported features (240)» or something like that. Same with /dev/sda6. sda5 is my root partition formatted with ext4, sda6 is my ext4-formatted home partition. How can I solve this problem?

Greetings,
Joshua

---

