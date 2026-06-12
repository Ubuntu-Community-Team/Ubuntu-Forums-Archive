---
title: "Installing Mini Ubuntu, freezing"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by NintendoTogepi on 2008-10-04
So I downloaed the Mini Ubuntu ISO and have been trying to install it. I've tried twice and both times it has frozen when it gets to the "pick software to install" part. I have just picked Xubuntu desktop both times as I would like to try Xfce. However, both times it has gone to 6% and then frozen, and I have to redo the installation.

What should I do? Forgo getting a GUI and just run it with the command line? :confused: :(

---

### Post by Partyboi2 on 2008-10-04
Have you tried leaving it for awhile when its at the 6% mark to see if it will continue?

---

### Post by Vivaldi Gloria on 2008-10-04
> **NintendoTogepi said:**
> What should I do? Forgo getting a GUI and just run it with the command line? :confused: :(

You can install a CLI system (see my sig) and install a desktop on it later on:

```
sudo apt-get install xubuntu-desktop
```

But why aren't you using a regular xubuntu cd or the xubuntu alternate cd? How much ram do you have?

---

### Post by NintendoTogepi on 2008-10-04
I wanted to try it out this way.

I fixed that problem, but now I have another one.

When I start up the Mini Ubuntu OS, it asks for my "Login" and password.

I type in the name I chose for Login, then it asks me to enter the password. The only problem is, no text can be typed when I enter the password. No matter what letters are pressed, nothing shows up. So I press enter and it says "invalid problem".

---

### Post by Vivaldi Gloria on 2008-10-04
> **NintendoTogepi said:**
>  The only problem is, no text can be typed when I enter the password. No matter what letters are pressed, nothing shows up. 

That's normal. Just type in the password and press enter.

---

### Post by NintendoTogepi on 2008-10-04
Unfortunately that doesn't work.

:confused:

Ah well.

---

### Post by NintendoTogepi on 2008-10-04
I'll make a new thread.

---

### Post by cariboo on 2008-10-04
Linux will not echo back the password to protect your password from shoulder surfers. IF you are having a problem with your password not being valid, boot in to recovery mode and at the prompt type:

```
passwd username
```

where username is the name you entered when you set up ubuntu. This will allow you to create a new password for your user. You should then be able to log into your newly installed command line distribution.

Jim

---

### Post by lbrian5 on 2008-10-04
installing question, i had windows vista home edition on my pc, i decided to install ubuntu 8 and made 50gb partition out of 300gb free space, it was installed successfully, the bad thing is i cannot log in using my user name and password....so decided to re install the said ubuntu and set a 40gb partition, it was successful, i was able to log in play with it a little bit. when i boot on windows vista and check the free space i was missing about 100gb out of 300gb. how can i check and remove the first partition that i wasted? any suggestions? thanks.

---

### Post by preetamsingh on 2008-10-04
> **NintendoTogepi said:**
> So I downloaed the Mini Ubuntu ISO and have been trying to install it. I've tried twice and both times it has frozen when it gets to the "pick software to install" part. I have just picked Xubuntu desktop both times as I would like to try Xfce. However, both times it has gone to 6% and then frozen, and I have to redo the installation.

What should I do? Forgo getting a GUI and just run it with the command line? :confused: :(

Hi

I am new user to Ubuntu 8


I want to install it on mynew MB ASUS P5N32-E-SLI

Other configrations are

Mother Board    :    ASUS P5N32-E-SLI
PROCESSOR   : CORE 2 DUO E6750 2.66 1333 FSB
Graphic            :    Nvidia 8500 GT 512 MB DDR2
RAM                :    2 GB (2 X 1 GB) KINGSTON DDR2
HARD DISK     :    160 GB 


Please help me


thanks

---

### Post by Partyboi2 on 2008-10-04
> **lbrian5 said:**
> installing question, i had windows vista home edition on my pc, i decided to install ubuntu 8 and made 50gb partition out of 300gb free space, it was installed successfully, the bad thing is i cannot log in using my user name and password....so decided to re install the said ubuntu and set a 40gb partition, it was successful, i was able to log in play with it a little bit. when i boot on windows vista and check the free space i was missing about 100gb out of 300gb. how can i check and remove the first partition that i wasted? any suggestions? thanks.
boot the ubuntu live cd and open gparted (System>Admin>Partition Editor) then you can view you various partitions and delete and resize the ones you need to.

---

### Post by Partyboi2 on 2008-10-04
> **preetamsingh said:**
> Hi

I am new user to Ubuntu 8


I want to install it on mynew MB ASUS P5N32-E-SLI

Other configrations are

Mother Board    :    ASUS P5N32-E-SLI
PROCESSOR   : CORE 2 DUO E6750 2.66 1333 FSB
Graphic            :    Nvidia 8500 GT 512 MB DDR2
RAM                :    2 GB (2 X 1 GB) KINGSTON DDR2
HARD DISK     :    160 GB 


Please help me


thanks
Hi welcome to ubuntu, have you tried downloading and installing the full version of ubuntu? You can downloaded it from [[COLOR=Blue]here [/COLOR]]("http://releases.ubuntu.com/8.04.1/")make sure that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches then burn it to a disk at x4 or less as a iso file. Once that has been done boot your machine with the ubuntu disk in the cdrom making sure that your cdrom is set as the first boot option in your bios. Then when you get to the main menu select the choice to check the cd for defects if this  passes then choose to install ubuntu and follow the on screen instructions. Any problems then open a new thread with what what has gone wrong.

---

### Post by lbrian5 on 2008-10-04
Partyboi2....thank you so much, I'll try that.

---

### Post by lbrian5 on 2008-10-04
> **Partyboi2 said:**
> boot the ubuntu live cd and open gparted (System>Admin>Partition Editor) then you can view you various partitions and delete and resize the ones you need to.

question how can i open gparted? sorry new to this os...it's interesting.

---

### Post by Partyboi2 on 2008-10-04
> **lbrian5 said:**
> question how can i open gparted? sorry new to this os...it's interesting.
At the top left of your Desktop you will see on the top panel Applications, Places, System. select System then Administration and Partition Editor, this will open up gparted. Remember to use the ubuntu live cd.

---

### Post by lbrian5 on 2008-10-05
wow....quick response, i'll do that.

---

### Post by lbrian5 on 2008-11-09
> **Partyboi2 said:**
> boot the ubuntu live cd and open gparted (System>Admin>Partition Editor) then you can view you various partitions and delete and resize the ones you need to.

on gparted this is what i have


/dev/sda1    fat16              39.16GB
/dev/sda2    ntfs    RECOVERY   10GB
/dev/sda3    ntfs    OS        349GB
unallocated   unallocated        2.07MB
/dev.sda4    extended          106.46GB
/dev/sda7    ext3               47.75GB
/dev/sda8    linux swap          2.08GB
/dev/sda5    ext3               54.27GB
/dev/sda6    linux swap          2.36GB


I tried to delete /dev/sda5 because this is the one I was having log in problem, it was giving me message "Unable to delete /dev/sda5 Please unmount any logical partition having a number higher than 5" /dev/sda7 is the one I reinstall and working good. Any help would be appreciated.


Wondering if anyone can check if boot information on my pc is right. It looks like double entry (Ubuntu) because I install and reinstall it, since the first one won't log me in.If it is double entry, how can I remove the other one? Thanks.

Ubuntu 8.04.1, Kernel 2.6.24-21 generic
Ubuntu 8.04.1, Kernel 2.6.24-21 generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
Ubuntu 8.04.1 memtest86+
Other Operating systems:
Dell Utility Partition
Windows Vista/Longhorn (Loader)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+

---

### Post by Partyboi2 on 2008-11-10
> **lbrian5 said:**
> on gparted this is what i have


/dev/sda1    fat16              39.16GB
/dev/sda2    ntfs    RECOVERY   10GB
/dev/sda3    ntfs    OS        349GB
unallocated   unallocated        2.07MB
/dev.sda4    extended          106.46GB
/dev/sda7    ext3               47.75GB
/dev/sda8    linux swap          2.08GB
/dev/sda5    ext3               54.27GB
/dev/sda6    linux swap          2.36GB


I tried to delete /dev/sda5 because this is the one I was having log in problem, it was giving me message "Unable to delete /dev/sda5 Please unmount any logical partition having a number higher than 5" /dev/sda7 is the one I reinstall and working good. Any help would be appreciated.


Wondering if anyone can check if boot information on my pc is right. It looks like double entry (Ubuntu) because I install and reinstall it, since the first one won't log me in.If it is double entry, how can I remove the other one? Thanks.

Ubuntu 8.04.1, Kernel 2.6.24-21 generic
Ubuntu 8.04.1, Kernel 2.6.24-21 generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
Ubuntu 8.04.1 memtest86+
Other Operating systems:
Dell Utility Partition
Windows Vista/Longhorn (Loader)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+

To work on partitions they need to be unmounted first. Right click on sda7 and sda5 and select "unmount" then right click on swap (sda6 and sda8 and select "swap off"  then delete sda5 and you only need one swap so delete either sda 6 or sda8

---

### Post by lbrian5 on 2008-11-10
Thanks Partyboi, I'll try that instruction about working on partition. Do you have any suggestion what to do on boot sequence I have below.

It looks like double entry (Ubuntu) because I install and reinstall it, since the first one won't log me in. If it is double entry, how can I remove the other one? Thanks.

Ubuntu 8.04.1, Kernel 2.6.24-21 generic
Ubuntu 8.04.1, Kernel 2.6.24-21 generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
Ubuntu 8.04.1 memtest86+
Other Operating systems:
Dell Utility Partition
Windows Vista/Longhorn (Loader)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+

---

### Post by Partyboi2 on 2008-11-10
> **lbrian5 said:**
> Thanks Partyboi, I'll try that instruction about working on partition. Do you have any suggestion what to do on boot sequence I have below.

It looks like double entry (Ubuntu) because I install and reinstall it, since the first one won't log me in. If it is double entry, how can I remove the other one? Thanks.

Ubuntu 8.04.1, Kernel 2.6.24-21 generic
Ubuntu 8.04.1, Kernel 2.6.24-21 generic (recovery mode)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)
Ubuntu 8.04.1 memtest86+
Other Operating systems:
Dell Utility Partition
Windows Vista/Longhorn (Loader)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+
Open a terminal (Applications>Accessoires>Terminal) backup your current menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` then open you menu.lst
```
gksu gedit /boot/grub/menu.lst
``` then near the bottom find the section starting with:
> title        Other operating systems: and remove the entries for 

```
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+[/quote]
``` then save and back in the terminal
```
sudo update-grub
``` then reboot to check.

---

### Post by lbrian5 on 2008-11-13
> **Partyboi2 said:**
> Open a terminal (Applications>Accessoires>Terminal) backup your current menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` then open you menu.lst
```
gksu gedit /boot/grub/menu.lst
``` then near the bottom find the section starting with:
 and remove the entries for 

```
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (on/dev/sda5)
Ubuntu 8.04.1, Kernel 2.6.24-19 generic (recovery mode)(on /dev/sda5
Ubuntu 8.04.1, memtest86+
``` then save and back in the terminal
```
sudo update-grub
``` then reboot to check.[/QUOTE]

Thank you so much.....I got it removed.

---

