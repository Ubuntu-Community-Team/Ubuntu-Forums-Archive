---
title: "Ran command and cannot boot"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-04-18
Stupid me ran "sudo dexconf" and rebooted and now after progress bar I get black screen then goes to dark gray and back to black then dark gray and stays that way. 
First, what is that command? I was trying to fix my ATI Radeon HD 3200 and saw the command in thread. When I ran the command it said 'killed' and that was it. What did it kill and how can I 'bring it alive' again'
Please help me get boot login.

---

### Post by Torgas Prim on 2009-04-18
All I can think of boot to a live cd and change the xorg.conf file.
The limit of my experience...sorry

---

### Post by drs305 on 2009-04-18
The recovery mode has an option to try to fix the X server. You might be lucky!

---

### Post by DougieFresh4U on 2009-04-18
> **Torgas Prim said:**
> All I can think of boot to a live cd and change the xorg.conf file.
The limit of my experience...sorry

Using live-cd now but do not know how or what to do (I'm no guru)

> **drs305 said:**
> The recovery mode has an option to try to fix the X server. You might be lucky!
I am NEVER lucky! Tried that and all the other options and still the same result

Thanks for replies.

---

### Post by drs305 on 2009-04-18
I don't know much about dexconf. It appears it presents an alternative to xorg.conf  

Perhaps you can restore /etc/X11/xorg.conf from a backup or see if there is an overriding file in /etc/X11/XF86Config-4  You might be able to use dpkg-configure to restore things. Take a look at the man page.

To look at those files, you will need to make a mount point from the LiveCD and then mount your actual Jaunty system partition. Otherwise you would just be looking at the LiveCD's files.

[http://www.penguin-soft.com/penguin/man/1/dexconf.html]("http://www.penguin-soft.com/penguin/man/1/dexconf.html")

Wish I knew more about dexconf to help out. Best of luck.

---

### Post by DougieFresh4U on 2009-04-18
> **drs305 said:**
> I don't know much about dexconf. It appears it presents an alternative to xorg.conf  

Perhaps you can restore /etc/X11/xorg.conf from a backup or see if there is an overriding file in /etc/X11/XF86Config-4  You might be able to use dpkg-configure to restore things. Take a look at the man page.

To look at those files, you will need to make a mount point from the LiveCD and then mount your actual Jaunty system partition. Otherwise you would just be looking at the LiveCD's files.

[http://www.penguin-soft.com/penguin/man/1/dexconf.html]("http://www.penguin-soft.com/penguin/man/1/dexconf.html")

Wish I knew more about dexconf to help out. Best of luck.

Thanks for your input. If some one could provide codes for me to get at my files via live cd - in simple dummy terms and guide me on editing x file, I would be so happy

---

### Post by adult swim on 2009-04-19
maybe you could try to chroot into your jaunty install from the livecd and reconfigure xserver
to do this boot the livecd, then go to a terminal and enter in ```
sudo mount /dev/sdXY /mnt
``` changing X and Y to the disk and partition number of your jaunty install respectively.  so if it was on the second partition of your first hard drive it would likely be /dev/sda2.  then run these commands to reconfigure your xorg.conf ```
sudo chroot /mnt

dpkg-reconfigure -phigh xserver-xorg

```  while you are chrooted into your jaunty install, you may as well inspect the xorg.conf to see that all looks well.  run ```
nano /etc/X11/xorg.conf
``` and take out anything that you may have added previously.  the dpkg-reconfigure should have done this for you already but it doesnt hurt to check.  to get out of nano hit ctrl+x and then hit y to save.  then enter in ```
exit

sudo umount /mnt

sudo shutdown -r now
``` and cross your fingers!

---

### Post by DougieFresh4U on 2009-04-19
> **adult swim said:**
> maybe you could try to chroot into your jaunty install from the livecd and reconfigure xserver
to do this boot the livecd, then go to a terminal and enter in ```
sudo mount /dev/sdXY /mnt
``` changing X and Y to the disk and partition number of your jaunty install respectively.  so if it was on the second partition of your first hard drive it would likely be /dev/sda2.  then run these commands to reconfigure your xorg.conf ```
sudo chroot /mnt

dpkg-reconfigure -phigh xserver-xorg

```  while you are chrooted into your jaunty install, you may as well inspect the xorg.conf to see that all looks well.  run ```
nano /etc/X11/xorg.conf
``` and take out anything that you may have added previously.  the dpkg-reconfigure should have done this for you already but it doesnt hurt to check.  to get out of nano hit ctrl+x and then hit y to save.  then enter in ```
exit

sudo umount /mnt

sudo shutdown -r now
``` and cross your fingers!

Thanks for reply.
This is what came out of commands. Don't know if all is good yet:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# 
root@ubuntu:/# dpkg-reconfigure -phigh xserver-xorg
grep: /proc/cmdline: No such file or directory
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090419003715
grep: /proc/cpuinfo: No such file or directory
grep: /proc/modules: No such file or directory
root@ubuntu:/# nano /etc/X11/xorg.conf
root@ubuntu:/# 
```

---

### Post by taavikko on 2009-04-19
```
dexconf - generate Xorg X server configuration file from debconf data
```

So basically you have just generated new xorg.conf file.

Just reboot and select recovery option in grub, then fix xorg.
It should then clear itself up.

Just a reminder, never do commands blindly when you see them.
Look for it's "man command" to see what it does.
This is equivalent for window users clicking and installing blindly software, and then wondering why they have malicious sw on their systems...

---

