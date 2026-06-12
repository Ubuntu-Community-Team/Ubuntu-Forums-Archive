---
title: "GRUB really slow!"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by PhoenixP3K on 2005-03-31
I'm not sure on where to post that question, so I'll do it here.

I've searched a bit, and did find explicitly what I was looking for. GRUB is taking over 2 minutes to get to the OS selection screen. And from what I've read other users have much faster boot-time.

Some info on my computer
PIV - 2.6 Ghz
248MB RAM

Ubuntu is installed on a slave 3.2GB 3600 rpm HD 
(might it be the cause? I though GRUB was installed on the master drive where WinXP is installed... Anyway speculations.)

---

### Post by feneks on 2005-04-02
Normaly a counter counts 3 seconds before GRUB starts Ubuntu. Did you change anything at /boot/grub/menu.lst ? You'll find a line with 

timeout       [seconds]

--edit--
GRUB is installed at the masterbootrecord (mbr) of the first Harddisk.

---

### Post by PhoenixP3K on 2005-04-02
My counter is set to 10 seconds to let me choose from Ubuntu or Windows XP. The the problem comes before that. From the moment I push the power button to the moment I can select wich OS there is a 2 minutes wait. The time Ubuntu takes to load from there is normal and comparable to XP. But I just don't understand what GRUB is doing for 2 minutes in stage1.5 thing...

---

### Post by feneks on 2005-04-03
Stage 1 is installed at the mbr of the first disk and just boots stage 2 or stage 1.5. Stage 1.5 is neccessary if your boot (or root) partition is behind the first 1024 cylinders of the first disk. The job of stage 1.5 is to find and load stage 2. Stage 2 then searches for the kernel and boots the system. Stage 1.5 is either just at /boot or as a small part at mbr and the rest at /boot.

[http://www.bglug.ca/articles/linux_boot_process.html](http://www.bglug.ca/articles/linux_boot_process.html)

Have you set the bootflag at your /boot (or root) partition? 

The rpm shouldn't be a problem. GRUB is quite small I think. If you want to know the data-speed of your disk use
```
hdparm -tT /dev/hdb
```

---

### Post by Muhammad on 2005-09-05
So Ubuntu should be installed on the logical drive in order for GRUB to load faster?

---

### Post by quitlahok on 2005-09-24
do you have a floppy drive? if not, make sure that you have your bios configured to tell the os it's not there. I was having trouble with grub loading really slowly, checked my bios and noticed that it thought floppy drive A was a standard drive, i switched that to "none" and now grub loads up in about half an instant :P

---

### Post by pirast on 2005-10-23
If you still have this problem please help solving it:

[https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245](https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245)

---

