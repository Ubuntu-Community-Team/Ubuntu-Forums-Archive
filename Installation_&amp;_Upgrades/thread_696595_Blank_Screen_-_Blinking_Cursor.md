---
title: "Blank Screen - Blinking Cursor"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by BrainDamage on 2008-02-14
Hi,

I installed Ubuntu Ultimate 1.5 from a desktop DVD. I have Vista installed in two of its partitions, and in the third I installed Ubuntu, choosing the resizing option while installation. 

The partitions are as follows:
/dev/sda1   Vista (C: )
/dev/sda2   Vista (D: )
/dev/sda6   /
/dev/sda7   /swap

In the 'Advanced' options, I passed (hd0,5) as a parameter to grub-install.

Everything seemed to go on fine, but when I am restarting my system (Compaq Presario laptop), I just get a blinking cursor... not even the GRUB prompt. 

Can anyone please help?
Thanks!

---

### Post by EXCiD3 on 2008-02-14
You chose to install Grub to the ubuntu partition instead of the MBR. You need to install grub to the MBR instead so that you can use grub to choose which OS to run. Follow this guide to install grub to your MBR and this should fix your problem: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by BrainDamage on 2008-02-14
Thanks! The other OS that I have is Vista and (as I read in some forum/post) that Vista overwrites the MBR at restart. The way to get across this is to use EasyBCD. If I install GRUB in MBR, can I use EasyBCD to configure so as to it's not overwritten by Vista at restart?

---

### Post by EXCiD3 on 2008-02-14
Vista only writes its boot loader to the MBR upon installation. If you use the live cd to install grub then that will fix your problem for good. If your ubuntu installation didnt detect and add options for you Vista installs then you will need to add these to your /boot/grub/menu.lst file.

Here is an example of a Windows grub option in case you dont have one already detected. You just add this to the end of the file and modify it to make sure it goes to the correct partition:

```
title        Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Remember Grub starts counting at 0 instead of 1!

---

