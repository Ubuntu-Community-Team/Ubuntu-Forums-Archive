---
title: "grub issue 10.10 -&gt; 11.04 on VMWare Server"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by rvince99 on 2011-10-05
I am using VMWare Workstation 6.0.1 and trying to upgrade my virtual Ubuntu 10.10 to 11.4. Evertyhing has installed correctly, and when it goes  to do the automatic reboot, I am getting a prompt of the following:

GNU GRUB version 1.98-1ubuntu3
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions

grub >


What should I do here to get my system to come up? Thanks rvince

---

### Post by rvince99 on 2011-10-05
Here is how I solved it:

grub>ls
(hd0) (hd0,0) (hd0,1)  (hd0,2)  (hd0,3)  (hd0,5)

then :

grub>ls -lh (hd0)

keep going through those until you find which is the drive with the system installed on it. In my case, it was (hd0,5) so I did :

grub> linux  (hd0,5)/vmlinuz root=/dev/sda1
grub> initrd  (hd0,5)/initrd.img
grub> boot

and voila!

---

### Post by rvince99 on 2011-10-05
The only problem is -- I have to repeat this process every time I reboot! I have run:

>sudo grub-mkconfig --output=/boot/grub/grub.cfg

Once I have successfully booted up, and it appears to recreate grub.cfg, but when I reboot, I keep getting the same thing.

Can someon please point me as to how I can make this work without taking me to the grub command line on each reboot? Thank you, rvince

---

