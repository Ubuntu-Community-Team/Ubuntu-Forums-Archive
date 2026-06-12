---
title: "Dual-boot, Two hard drives (xp-ubuntu)"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by harsh2209 on 2007-11-30
Friends,

I want to install windows xp pro on the larger hdd (320 GB) and Ubuntu 7.10 on the second (80 GB). I didn't get enough help from the previous similar threads.

I have two IDE hard drives (320GB and 80 GB) for my desktop

I tried unsuccessfully: -

Connected both hard drives as Master -> Slave.
Installed Win Xp Pro on the 320 GB hdd.
Then, Installed Ubuntu 7.10 on second i.e. 80GB hdd.
When reboot the system, Grub Error 21 and neither of the two OS came up.

So, please suggest a working procedure to go ahead with this task.

---

### Post by Pumalite on 2007-11-30
I assume 320 GB is Mater and 80 GB is slave?

---

### Post by harsh2209 on 2007-11-30
Yes. 320Gb is Master and 80 GB as Salve.

---

### Post by Pumalite on 2007-11-30
Have to install with both hard drives connected and install Grub to the MBR
We assume Master is sda. Get Gpated Live CD and make a large partition of your whole sda drive, formatting it ntfs. Install XP. Get back to me when you have done that.

---

### Post by jimbogy on 2007-11-30
another method (that I've used successfully since being unable to dual boot Ubuntu (on one HD) or Vista (on a separate HD)_is to simply restart and  then hit F2 during restart and turn off HD 0 (where Vista is) so that Grub on HD 1 boots up Ubuntu.

inelegant but workable

---

### Post by harsh2209 on 2007-11-30
Ok, there's an issue. The current scenario is:-

On the 320 GB HDD Xp is already installed WHICH I CANNOT FORMAT. In other words DON'T WANT TO as I'm too lazy.
Another thing is that I have installed Ubuntu on the other HDD i.e. 80 GB. 
I did that separately i.e. by installing drives individually.

Now, what can I do to make them Master Slave  in order to have a regular dual boot?

---

### Post by Pumalite on 2007-11-30
Then you can boot either one by switching the boot order in BIOS.

---

### Post by meierfra on 2007-11-30
You probably just have the reinstall grub and edit /boot/grub/menu.lst.

Please boot from the Live CD, open a terminal (Application->Accessories->Terminal)

and post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

Also go to Places->Computer and see whether you can find your ubuntu partition. If yes navigate to /boot/grub, open the file menu.lst and post the content.

---

### Post by louieb on 2007-11-30
Not a problem. Pretty common setup. Use it myself. 
A great place to search is the how to section of the forum.
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

1st time I set up a PC to dual boot - I unplugged the drive that XP was installed on. Paranoid something bad might happen.  
Then to dual boot had to add XP to the GRUB menu.
[Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

