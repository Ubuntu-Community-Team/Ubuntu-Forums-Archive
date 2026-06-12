---
title: "GRUB reboots computer when selecting win7 from menu"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by sdlvx on 2009-12-20
Hey guys, I urgently need and would really appreciate some help right now. I had Ubuntu 9.04 with GRUB 1 installed, and today I went to install windows 7, because there are NO options for having decent 3d support with my old ATI graphics card in linux. 

Anyways, I installed, and everything went fine. I went to boot and I got the windows 7 loader, so I went back and reinstalled GRUB with

root (hd0, 6)
setup (hd0)

and it worked. However, when I try and select windows from the GRUB menu (it showed up as windows XP instead of windows 7), it says something about missing media. (it was booting off of hd0,6). I changed it to (hd0,0) and it just reboots my computer. 

My partitions are a giant mess and they look something like 

free space | system reserved | free space | ubuntu | home | Windows 7

The boot flag is on system reserved, and it seems like if I fix the windows boot loader by going to the recovery console and tuping 

bootsect /nt60 c: 

it boots windows no problem and grub goes away

but if I run 

root (hd0,5)
setup (hd0)

GRUB comes back and I can't access windows 7, because when I access it from the GRUB menu it just restarts the computer. 

Please help, I've spent a few hours googling this and I couldn't find anything about it crashing like this. I need everything together tonight because I need both linux and windows 7 for work and I'm going out of town.

Thanks.

---

### Post by sdlvx on 2009-12-20
come on guys, please. any ideas would help. I'm really, really getting frustrated with this and I'm ready to smash something.

---

### Post by sdlvx on 2009-12-20
awesome, reinstalling windows 7 now. Nothing works now.

---

### Post by sdlvx on 2009-12-21
you guys, really. 

I reinstalled windows 7, booted into a live CD, ran

sudo grub
find /boot/grub/stage1

it told me hd0,5

root (hd0,5)
setup(hd0)

and it doesn't work. I tried windows 7 with hd0,0 to hd0,10 and nothing works. Everything I read just says "it's really easy to do, just run those commands".

What is wrong? PLEASE HELP.

---

### Post by oldfred on 2009-12-21
If your are using 9.04 your have old grub and installing grub does not fix the windows install just reinstalls grub to the mbr so you can boot both systems. You probably just need to edit grub's menu.lst if the windows install boots ok before you reinstall grub.

The boot flag has to be on the windows boot partition. If it is a new win7 install windows normally creates a small boot partition. If it is a install to an existing ntfs partition it will not create the small boot partition. If you have another windows installed it combines the win7 boot files into the existing windows boot that has the boot flag.

You should not have to reinstall anything but grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Other than the new boot partition for windows the install process is similar.
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

If you need specific help editing menu.lst run this:
Boot Info Script 0.41 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions:  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download: 
sudo bash ~/Desktop/boot_info_script*.sh
sudo bash ~/Downloads/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory.(Ver41 put mine in my home dir). Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by sdlvx on 2009-12-21
Thank you so much oldfred. I'm still confused because of the system partition windows 7 makes.

Even though find /boot/grub/stage1 returned hd0,5 should I use 
root (hd0,0)?

edit: nvm, it just says it can't mount the partition when I try that.

EDIT: Thanks oldfred for enlightening me about easyBCD. I installed the beta version of 2.0, and installed GRUB and pointed it to my old installation, and it works perfectly fine with my windows 7 bootloader. Thank you so much, you saved my life. Now it's time to reinstall all the drivers for my laptop from 2006 for windows 7 x64, i.e. try and find compatible drivers from other laptops because my laptop doesn't support win7 =[

---

### Post by oldfred on 2009-12-21
No you use exactly what drive/partition it gives as that is the partition that grub will look to boot from the mbr. It is BIOS says what drive to boot and looks in the mbr. The mbr finds a partition to boot. Windows mbr looks for the boot flag, grub embeds the partition number and looks for that.

#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)  # where 0 is first drive

---

