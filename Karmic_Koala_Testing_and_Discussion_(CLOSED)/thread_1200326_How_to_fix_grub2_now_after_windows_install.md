---
title: "How to fix grub2 now after windows install?"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Castlef on 2009-06-29
Hey all I installed windows 7 on another partition and now my master boot record is screwed... I can only boot up windows 7 now

I am currently on the live CD for karmic

When I try to do the usual sudo grub.... it does not even recognize the command.

When I type gru(Tab) here are the options I have:grub-dumpbios     grub-mkconfig     grub-mkimage      grub-setup
grub-editenv      grub-mkdevicemap  grub-mkrescue     
grub-emu          grub-mkelfimage   grub-probe        
grub-install      grub-mkfont       grub-set-default 

I have no idea which one to use. I tried doing 

sudo grub-install /dev/sda5 (my ubuntu partition)

and it says grub-probe: error: cannot find a device for /boot/grub

I tried doing

sudo grub-setup /dev/sda5

and it says (segmentation fault)

Any ideas?

Additionally .... I would like to see an option to restore grub on the main list when you boot from a live CD

---

### Post by budluva04 on 2009-06-29
give this a try

```
$ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub
```

if not i can help you alot easier and quicker on the irc channels 

#ubuntu+1 irc.freenode.net

---

### Post by Castlef on 2009-06-30
Hi

I tried

sudo apt-get install --reinstall libdebian-installer4

it ran into a problem with not finding it but sudo apt-get update fixed that.

When I ran

ubuntu@ubuntu:~$ sudo os-prober
ls: cannot access /media/System040Reserved: No such file or directory
ls: cannot access /media/System040Reserved: No such file or directory
ls: cannot access /media/System040Reserved: No such file or directory
ls: cannot access /media/System040Reserved: No such file or directory
/dev/sda5:Ubuntu karmic (development branch) (9.10):Ubuntu:linux

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by nhasian on 2009-06-30
here are step by step instructions:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

