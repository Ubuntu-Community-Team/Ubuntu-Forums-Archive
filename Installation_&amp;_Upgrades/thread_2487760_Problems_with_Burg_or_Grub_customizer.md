---
title: "Problems with Burg or Grub customizer"
date: 2023-06-14
forum: Installation &amp; Upgrades
---

### Post by Larjk on 2023-06-14
Hi,

I have recently decided to reinstall Kubuntu on my old computer.

I would like to change the appearance of grub, for that, I tried to install Burg or Grub customizer but I could not.

I followed the steps in this tutorial: [https://askubuntu.com/questions/1263297/how-to-install-burg-bootloader-in-ubuntu-20-04](https://askubuntu.com/questions/1263297/how-to-install-burg-bootloader-in-ubuntu-20-04)

When I used the command "sudo update-burg" this is the problem:
[IMG]https://tinypic.host/i/oc9hTD[/IMG]
[https://tinypic.host/i/oc9hTD](https://tinypic.host/i/oc9hTD)

When I used the command "burg -emu" this is the problem:
[IMG]https://tinypic.host/i/oc9nhK[/IMG]
[https://tinypic.host/i/oc9nhK](https://tinypic.host/i/oc9nhK)

Can anyone help me?
Thanks

---

### Post by Rubi1200 on 2023-06-14
From what I remember, customizers like Burg cause more harm than good.

Please run the boot info script in my signature. Do not repair anything, just post the results here so we know what is where.

You can, with some work, customize GRUB following the various options starting here: [https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries](https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries)

---

### Post by yancek on 2023-06-14
What appearance would you like to change?  If you simply want a background image of your own, copy the image to the /boot/grub directory and run sudo update-grub.

The link below contains an explanation by a user who got burg to work on 20.04.  The site also indicates it is only for Legacy installs and not UEFI, don't know as I've never used it.

[https://askubuntu.com/questions/1263297/how-to-install-burg-bootloader-in-ubuntu-20-04](https://askubuntu.com/questions/1263297/how-to-install-burg-bootloader-in-ubuntu-20-04)

---

### Post by ajgreeny on 2023-06-14
I agree totally with Rubi1200 and would seriously suggest that you forget about either burg or GC, both of which can and have caused more difficulties than  help.
There are plenty of guides to using grub and how to edit the various configuration files safely in order to make changes without installing and using any other applications than are already in the default systems of the *Buntu family of OSs.

See:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275)
for a lot of detailed but easy to follow information.

---

### Post by Dennis N on 2023-06-14
> I would like to change the appearance of grub...
For this, you may like a grub theme.
Here are some:
[https://www.opendesktop.org/browse?cat=109&ord=rating](https://www.opendesktop.org/browse?cat=109&ord=rating)
They use a script for installing.
I've have the one named **vimix** on one of my computers. Others I haven't tried.

---

### Post by Larjk on 2023-06-15
Thank you all! 

Finally got my grub yo get prettier following this tutorial:
[https://ostechnix.com/change-grub-theme-in-linux/](https://ostechnix.com/change-grub-theme-in-linux/)

---

### Post by Rubi1200 on 2023-06-15
Happy to hear you found a solution that suits your needs.

Please mark Solved using the Thread Tools at the top of your post.

---

