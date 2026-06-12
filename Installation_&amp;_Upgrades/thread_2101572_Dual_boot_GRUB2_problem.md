---
title: "Dual boot GRUB2 problem"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by lkz6998 on 2013-01-05
I have a Win7 laptop and I installed Kubuntu 12.04 on it a few months ago and it was dual booting using GRUB2 and everything was working fine.  
What I didn't like was on power-on it would default to Kubuntu after 10 seconds.  I want it to wait forever for me to choose the operating system.  
I downloaded the GRUB Customizer GUI program and did 2 things; moved Win7 to the default boot position instead of Kubuntu and I changed the TIMEOUT to -1.  I thought -1 meant that the boot menu would wait forever until I chose the operating system.
However after making the changes, when I power on the laptop there is no GRUB2 boot menu anymore and it immediately boots to Win7 and doesn't give me the chance to load Kubuntu.
I can't figure out how to get back into Kubuntu.
Does anyone know what I did wrong, and how I can fix this?

---

### Post by highrun on 2013-01-05
Download a program called easyBCD. When it installs, select the add new entry option. Go to the linux tab and select the appropriate settings. Make sure to save. Then go to the edit boot menu. There is where you will select teh default OS, the timeout options, and etc. Again, make sure to save

---

### Post by darkod on 2013-01-05
> **highrun said:**
> Download a program called easyBCD. When it installs, select the add new entry option. Go to the linux tab and select the appropriate settings. Make sure to save. Then go to the edit boot menu. There is where you will select teh default OS, the timeout options, and etc. Again, make sure to save

That's a windows program and works only with windows bootloader, not grub.

You can use the kubuntu cd to load the live session, then open the kubuntu partition on the hdd and find the file /etc/default/grub.

In there there will be a line like GRUB_TIMEOUT=-1. Make the value 30 for example. That means 30 seconds.

I really can't imagine why you want it to wait indefinitely. Not sure if putting 0 means indefinitely. I think 30 seconds are more than plenty. But putting it at 30 will at least allow you to see the grub menu to boot kubuntu.

Later you can investigate how to make grub2 wait indefinitely, and if it's possible at all.

---

### Post by darkod on 2013-01-05
Sorry, I got slightly confused. Cahnging the value only in /etc/default/grub will not help immediately even though that is where you need to change it.

You will also have to update the /boot/grub/grub.cfg but it might be better to temporarily change it from the live session. In there should be the GRUB_TIMEOUT value too. Set it at 30 so that it allows you to boot to kubuntu once, and then adjust the value either directly in /etc/default/grub or using Grub Customizer again.

After you adjust it, make sure you run:
sudo update-grub

to recreate new grub.cfg.

---

### Post by lkz6998 on 2013-01-05
After I make changes in GRUB Customizer I have to type "sudo update-grub"?
I didn't do that last time, maybe that has something to do with the problem I'm having now...

---

### Post by darkod on 2013-01-05
Not sure, I change it directly in the config files. It's more clean that way.

I would expect Grub Customizer to save the changes but I'm not sure. Anyway it doesn't hurt running update-grub.

---

### Post by Hakunka-Matata on 2013-01-05
Yes, you want to run ```
sudo update-grub
```after changing grub parameters.  Running it will generate a new "grub.cfg" file which is the file read @ startup.  Watching it generate the file can also be a learning experience, as you see it finding all bootable partitions and creating a menu line for each,

good luck

Example:

das@acer-netbook:~$ sudo update-grub
[sudo] password for das: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
das@acer-netbook:~$

---

