---
title: "Install problem - grub"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by asramasarma on 2006-11-21
Hi,
I have installed 6.10 version ubuntu in my PC. My PC already had XP and redhat linux. I used the same diskspace of old linux for root and swap.  
Once I start the PC after the instalation, I have one terminal with prompt as grub>.

Is it that I lost my XP? or how can I make my system dual bootable from here?.

Thanks in advance,
Seetharam.

---

### Post by ingo on 2006-11-22
Have a look at this link

[http://www.smop.co.uk/node/43](http://www.smop.co.uk/node/43)

to find at least your ubuntu kernel. It is very short and easy to follow Don't know about winxp, but am sure there is plenty of advice available on the forum.

hth

---

### Post by Herman on 2006-11-22
Hello asramasarma,
Try reading this link too, 'Grub's [Command Line Interface'.]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
You should be able to see there [how to boot either Windows XP]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI") or [Ubuntu ]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI")up from the command line. However, if you want to, you can boot Ubuntu first and fix the problem.
Your Windows XP will be fine. You can also use [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") to boot any  operating system if you don't like using grub's command line.

When you get your computer to boot Ubuntu, you should go check that you have all the folders and files similar to those pictured in this link,  [(click here)]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation"),   Look in pictures numbers 4, 5 and 6 please.  In the sixth picture, (fig 6 grub), you should see a file named 'menu.lst', which is the file that normally gives us our Grub menu. Does your computer have one of those, (a menu.lst file in /boot/grub?).  Perhaps something went wrong in your install and your menu.lst file did not get made.
If you do not have any menu.lst file, the command 'sudo update-grub' should make one for you. ```
sudo update-grub
``` That should fix your problem, next time you boot up you should see a grub menu. 
You might (or maybe not), need to add your own entry for Windows XP by editing your menu.lst file. You can read about that [here]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries"). Be sure to make your Windows entry below the bottom of your automagic kernels list, or it will be deleted automagically whenever you receive a new kernel for Ubuntu during an update.

---

### Post by ingo on 2006-11-22
Great link, Herman! Bookmarked already :)

Cheers

---

### Post by Herman on 2006-11-22
Thanks for your link too, ingo, I hadn't realized the usefulness of that 'geometry' command before, so I learned something new! Thanks, I'm happy!  :D

---

