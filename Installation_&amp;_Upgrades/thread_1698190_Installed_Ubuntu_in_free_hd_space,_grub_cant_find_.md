---
title: "Installed Ubuntu in free hd space, grub cant find windows"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by Canime on 2011-03-01
Does anyone know the solution to this problem? I have windows on my primary partition, I installed Ubuntu on some free space in the hard disk, now when the boot loader loads it, it has only the choice for Ubuntu, the choice for windows, but alas when I select windows nothing happens, it returns to the grub boot loader list! 

All my files are recognized and haven't been deleted and I have run the windows recovery (start up repair in English) but of course nothing happened to change the situation for the better. Can someone offer some advice?

---

### Post by tommcd on 2011-03-01
Try just opening a terminal in Ubuntu and running ```
sudo update-grub
```
Hopefully this will add Windows to your grub list properly so you can boot it.
If this does not solve the problem, then post the output of this from the terminal:
```
sudo fdisk -l
```
This will list all of the partitions that Ubuntu sees.
Also download and run the bootinfo script, which you can get here:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Post the output of the bootinfo script here as well.
I am not the best at reading that booinfo script. But there are many people around here who are quite knowledgeable about it; and this is the info that is need to properly diagnose the problem.

And welcome to the Ubuntu forums!

---

### Post by Canime on 2011-03-02
I partially solved the problem, but now things have changed. I managed to insert the right CD (it was a vista CD I was using and not a windows7 CD), then I repaired the windows 7 image to a previous time. Of course this wrecked the boot options for Linux.
:(

---

### Post by tommcd on 2011-03-02
> **Canime said:**
> I partially solved the problem ... I repaired the windows 7 image to a previous time. Of course this wrecked the boot options for Linux.
After fixing the Windows master boot record (MBR) you will then have to reinstall grub2 to the MBR so that you can boot both Ubuntu and Windows.
What version of Ubuntu are you using?
I assume that you are using either Ubuntu 10.04 LTS (long term support) or Ubuntu 10.10 (the latest version).
To reinstall grub2 to the MBR from the Ubuntu live CD see this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Note: The first method listed there should work just fine.
Then when you reboot into your Ubuntu install, be sure to open a terminal and run:
```
sudo update-grub
```
This should *hopefully* update your /boot/grub/grub.cfg file so that you have the option to boot either Ubuntu or Windows when you boot your computer.

Write back if you need more help.

---

