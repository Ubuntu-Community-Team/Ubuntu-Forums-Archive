---
title: "Virtual console problem after upgrading to Gutsy"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by norferatu on 2007-10-30
I just upgraded to Gutsy and the transition was more or less smooth.. 

But now, my problem (#1) is: if i edit my /boot/grub/menu.lst and write "vga=795" in front of my new 2.6.22-14 kernel, when i access the virtual console (ctrl+alt+f1), i just cannot see anything beside a blinking cursor! Nothing happens, i can't login or do anything else! I had to remove the "vga=795" entry which makes me work with HUGE ugly letters in the console..

Plus, another problem (#2): if i try to go back to x (alt+f7) the system usually crashes, i get no x and have to reboot!

Can anybody help? Thanks.

---

### Post by dkkarthik on 2007-11-02
I have the same problem. Has anyone found a solution to this? I want to enable virtual console as my x doesnt seem to work (after my attempt to upgrade my ati 9700 pro card drivers). I dont have the virtual console and cant compile the ati drivers using knoppix - I am screwed.

---

### Post by mikro on 2008-02-15
Same problem here, Kubuntu fresh install.

---

### Post by geoffree on 2008-03-03
I have a slightly different problem with virtual consoles:  When I enter C-A-Fx all that I get is a totally blank screen PLUS after a few seconds, I notice that my monitor goes to sleep mode. From the blank screen I can get back to the GUI by entering C-A-F7 and it returns to a graphic mode.  I have looked at the /etc/profile files and other ~/.bash?? files and they seem to contain appropriate code.
I have been struggling with this for several weeks now, ever since installing Gutsy. Hopefully someone will have a fix for this.  What about the Ubuntu developers? What do they have to say?

Geoffrey

---

### Post by geoffree on 2008-03-03
More re: virtual console problem:

The run lines in my ../grub/menu.lst file read as follows:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=74851bee-4253-4a44-86c3-6177fb3e199a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


In my Dapper ../grub/menu.lst, the kernel line is simply:

kernel     /boot/vmlinuz...(ver #)   root=/dev/hda1  ro quiet splash

I frankly don't understand the great long line of numbers following UUID= but I am posting this with the hope that the Ubu people or some expert might find something of explanation in all this.

Geoffrey

---

