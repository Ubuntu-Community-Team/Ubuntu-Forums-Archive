---
title: "start-up manager ineffective w/r/t Windows boot"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2012-01-08
New 11.10 installation on a Dell D630 (2GB RAM) running XP. (Absolutely GORGEOUS interface, btw, this "Unity."  I love everything about it.)    

Everything seems to be fine except that I need it to default boot to XP, and, even though I can select "XP" as the default boot in the Startup Manager program, upon a reboot Ubuntu is still selected.

It will successfully execute instructions to boot to other OSs - the recovery mode, for example.  I uninstalled and re-installed the Startup Manager, and it didn't make any difference.  

I'm OK with a command line/terminal approach to this issue. 

Thanks in advance,
Scott

---

### Post by darkod on 2012-01-08
I'll tell you my personal preference, which you may or may not like.
By default grub2 boot system number '0' and it's starting to count from 0, which means the first system in the menu. The preference about this is in /etc/default/grub.

But to avoid the menu position of windows to change if new kernels of ubuntu get added on top, I change the number in the filename of os-prober which detects other OSs. If you look in /etc/grub.d the main files are 10_linux which is for ubuntu, and 30_os-prober which detects all other OSs including linux OSs. The 10 means that ubuntu is read before the others. What I do is create a copy of os-prober with a number smaller than 10, and make the original non executable:

sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober
sudo chmod -x /etc/grub.d/30_os-prober

That makes windows first in the menu so you can leave the default value at 0 in /etc/default/grub.

After the above command to recreate a new grub.cfg run:
sudo update-grub

Now you should have different layout in the boot menu and windows should be default that will boot if you don't touch anything.

PS. If you would like to get rid of the memtest entries in the menu so it looks more organized, you can make that file non executable too:
sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

If you ever want to make it executable again, just run the same chmod command but with +x.

---

### Post by Frogs Hair on 2012-01-08
You may want to check the link. I am not sure why Startup Manager is still  the software center because as the thread title indicates it is ineffective . [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by sks24 on 2012-01-08
Well Darkod's commands worked like a charm and in any case I prefer the cleaner GBUB.  
I installed 11.10 on the machine with updates enabled during the installation.  So maybe that has something to do with the Startup Manager still being in the software center.  But it is there, Frogs Hair, and I downloaded the ISO from the Ubuntu.com slash Canonical site (Here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download))  

Thank you both very much!

---

