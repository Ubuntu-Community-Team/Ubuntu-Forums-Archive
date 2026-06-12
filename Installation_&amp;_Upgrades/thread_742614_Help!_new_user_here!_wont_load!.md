---
title: "Help! new user here! wont load!"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by oncomingstormx on 2008-04-01
i get passed the GRUB part then i get a black screen. nothing happens. im not exactly computer smart just tired of windows soo bare with me


can anyone help me?

---

### Post by Pumalite on 2008-04-01
Try:
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg
Get back with results

---

### Post by oncomingstormx on 2008-04-01
yeah once i brought up the command line it loaded up everything. id tried to read what it said for more reference but it loaded too fast

---

### Post by Pumalite on 2008-04-01
This is new.

---

### Post by retrow on 2008-04-01
It could be the case that your hard drive is not being read correctly. I had a similar problem once, though I can't be sure that its the same.

When you get GRUB screen, hit Esc (which will take you to grub options for your default loading option).

Then at the end of the line which goes:
```
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c1c00bd0-c548-4a69-b96f-0e3c98b9f8e8 ro splash
``` add [color=red]irqpoll[/color]

```
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=c1c00bd0-c548-4a69-b96f-0e3c98b9f8e8 ro splash [color=red]irqpoll[/color]
``` Then press **b** so that it boots.

If everything goes well, you will need to edit the line permanently by editing menu.lst

---

### Post by r1reddog on 2008-04-02
I am having the same problem and none of these options work. I suspect its a graphics display issue as i have a wide screen laptop but ubuntu install and runs fine on a normal monitor size.  I have no access to any sort of command line by pressing ctrl + alt +f1.  does anybody have an idea how to get ubuntu to run. I really want to get it working on my laptop!!

---

### Post by ichi@YUKI on 2008-04-03
We're having trouble booting Ubuntu in one of our lab's dektops. It freezes in the splash screen. So I edited the line:

from:
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb8ab05a-fe8e-415a-bb7a-feff350ad753 ro quiet splash
to:
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cb8ab05a-fe8e-415a-bb7a-feff350ad753 ro splash

Apparently, the splash screen freezes when it loads hardware drivers. Can anyone help?

---

### Post by Pumalite on 2008-04-03
Try: nosplash

---

### Post by ichi@YUKI on 2008-04-04
still doesn't work. I'm sure there was an error after the *Loading Hardware Drivers part, but it showed up so fast I wasn't able to take note of the error output. We tried reinstalling Ubuntu three times already, and the disc doesn't seem to have any problems when we check it.

Oh yeah, if this helps, the PC uses an Intel P4 2.40GHz and has 256mb of RAM. We used the alternative to install Ubuntu.

---

### Post by Pumalite on 2008-04-04
Try Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

