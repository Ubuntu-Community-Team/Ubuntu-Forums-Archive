---
title: "Uh-oh, wha-di-do!?"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2007-09-20
Keep in mind this worked perfectly when I installed it on my system it booted straight to the desktop faster than you can say ... . So I was getting to know Ubuntu and how it works and what possible things I could accomplish so my dumbarse didn't know that not only konquerer was a web browser it was also the browser and helper for the file system, so what did I do? "Hm, wonder what happens if I remove this" hah little did I know I just screwed myself over. So when I tried to reinstall it through the add/remove program on there it lead to some other known error, so I said screw it, I'm gonna wipe my system and start over. Boy this just gets better and better, so after wiping the system I run into a slower boot process when loading the kernel from the LiveCD, so 5min waiting for it to leave the Ubuntu splash screen I finally get to where it starts loading the processes. and this is what I get for the pending 20min of getting nowhere: 

Link to image: [http://img451.imageshack.us/img451/6903/im000379hx6.jpg](http://img451.imageshack.us/img451/6903/im000379hx6.jpg)

So now as you can see I have my leg stuck in a bear trap and obviously cant get away from it. Please help, I really like Ubuntu and wish to experiment with it and get to know how Linux works. Thank you in advance. :)

---

### Post by Pumalite on 2007-09-20
You have trash left in your hard drive or partition. You might have to DBan.
Post:
sudo fdisk -lu

---

### Post by cowboy.bebop on 2007-09-20
I googled DBan, is it something that comes on a live CD or is it built into the cd itself? Also I noticed below what you typed "sudo fdisk -lu" is that LU or IU?

---

### Post by Pumalite on 2007-09-20
Small L

---

### Post by cowboy.bebop on 2007-09-21
So itried dban and it sorta worked. it did in fact wipe my hd cause xp wont boot. but im still getting the same errors. I tyred sudo -lu and then returns no sign that something may have formatted it or casued any changes. any other ideas that may help?

---

### Post by Pumalite on 2007-09-21
If you now want dual boot XP-Ubuntu. do the following:
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Burn the iso to CD, boot from it and make one large partition of your hard drive formatted ntfs. Install XP. Defrag Xp several time, Boot Gparted again, right click on XP and from the menu, choose 'resize partition'. Then install Ubuntu, install Grub to MBR (by default) and you are done. You will be presented with a menu to boot either OS.

---

### Post by maybeway36 on 2007-09-21
If you have a Knoppix disc you can boot GParted from that.
1. At the "boot: " prompt, type ```
knoppix noswap desktop=fluxbox
```
2. When Fluxbox starts up, right-click on the desktop, go to XShells>XTerm
3. Type ```
sudo gparted
```
4. After you close GParted, type ```
sudo shutdown -hP now
``` to turn off your computer.

---

