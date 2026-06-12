---
title: "Grub problem"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by fgp_uk on 2007-10-29
Hi, I'm new to Ubuntu have been using Feisty without problems, thought I'd try the new version 7.10. The upgrade itself went well enough but I wasn't happy with the poor sound quality so decided to go back to Feisty. Thought I had been smart by making a backup with Acronis true image before the upgrade, so restored the backup but now when booting into Ubuntu it gets as far as displaying "GRUB" and a flashing cursor. All the files and directories are there so I'm guessing I need to reinstall grub or something but can't work out how to do it! My Linux partition is sda5 and I install grub to this partition and use another boot manager to fire it up... well I used to anyway. :)

---

### Post by shane2peru on 2007-10-29
> **fgp_uk said:**
> Hi, I'm new to Ubuntu have been using Feisty without problems, thought I'd try the new version 7.10. The upgrade itself went well enough but I wasn't happy with the poor sound quality so decided to go back to Feisty. Thought I had been smart by making a backup with Acronis true image before the upgrade, so restored the backup but now when booting into Ubuntu it gets as far as displaying "GRUB" and a flashing cursor. All the files and directories are there so I'm guessing I need to reinstall grub or something but can't work out how to do it! My Linux partition is sda5 and I install grub to this partition and use another boot manager to fire it up... well I used to anyway. :)

I'm not familiar with Acronis backup program.  But I have my fair share of backups and failed restores to take a guess that your menu.lst is incorrect.  Ubuntu started using the UUID method, and even put it into the grub menu.lst so that when you try an new install and then restore it doesn't boot.  What you need to do.  Boot into a live CD or something that will allow you to edit your /boot/grub/menu.lst.  
(First mount your Ubuntu partition and cd to that partition.)
1.  Backup your menu.lst file (all of these steps I'm going to assume you are in a linux type distro)
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
2.  Now we are going to edit it and get rid of those awful UUID things:
```
sudo gedit /boot/grub/menu.lst
```
Now scroll down to the Ubuntu that you boot into and find the line:
root=UUID=asdikzc89u7asdfkl88a9s0d  or some long string like that and change it to:
root=/dev/**your partition**
3.  Reboot and it should boot right up.  This is my guess at what the problem is as well as a solution.  Let me know if you need more help or this doesn't work.  I'm assuming that you know a little of command line, so if you don't know a command please feel free to ask.  

Shane

---

### Post by fgp_uk on 2007-10-30
Thanks for that Shane, I tried what you said but unfortunately it made no difference, I've wasted so much time on this now that I'm going to have to give up on it for now, thanks anyway.

---

