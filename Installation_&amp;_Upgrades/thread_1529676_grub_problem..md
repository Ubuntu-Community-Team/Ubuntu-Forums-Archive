---
title: "grub problem."
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by sailor123 on 2010-07-12
m beginner to linux,for the curiiousity i installed ubuntu on vista.it worked very fine & i was able to access ubuntu from vista partition s well.Later i uninstalled ubuntu s program & gave try to opensuse.nw i ddnt like it either so i tried to reinstall it bt couldnt succed,so i formatted that partition..which turned into nightmare...
vista didnt start only,so i again booted from dvd & again installed ubuntu,vista started workin back again...then i understand that windows boot mananger was overridden by grub.
Is there any way that i can get back my vista boot loader as default again and ll i b able to access linux partion from vista???

---

### Post by Rubi1200 on 2010-07-12
I will try and explain this as simply as possible.

You need either the installation CD for Ubuntu or any other so-called live distro (Knoppix would also be a good choice).

You need to put the CD in the CD drive and boot the computer. I assume you have already set BIOS to boot from the CD/DVD drive?

When the Ubuntu CD starts choose the option to try Ubuntu without any changes.

Do NOT, I repeat, not choose to install!

Once the CD has done its job you should be looking at the Desktop in Ubuntu.

Open a web browser and click on the link at the bottom of my post.

Follow the instructions there and post the results back here.

We will then be better able to advise you how to fix things.

Good luck!

---

### Post by rogerdg on 2010-07-12
The easiest way to fix this problem is to configure GRUB to load windows as the default with a very short timeout (2-3 seconds) to permit an override to boot Linux if you wish. 

When you reboot the computer count down the number of menu items to the Windows Menu Item for example:

Linux Boot
Linux Recovery
Memtest
Windows

The item # for Windows would be 3

Edit /etc/default/grub and change the line GRUB_DEFAULT=0  changing the 0 to the number you determine is the correct number for Windows
Change GRUB_TIMEOUT= to a small number (I use 3 for a 3 second delay)  This gives you an opportunity to boot to Linux if you decide you want to.

from a terminal run

sudo update-grub

When you next reboot the computer Windows will be the default and will start 3 seconds after the GRUB menu appears.

---

### Post by thahir1986 on 2010-07-13
I also have the same problem....

I have been vista in my office system and after i installed the ubuntu , we can't get back vista after uninstall ubuntu...i tried didn't find any solution,  still i have the vista and ubuntu as dual boot....

If u find the solution dont forget to inform that....

---

