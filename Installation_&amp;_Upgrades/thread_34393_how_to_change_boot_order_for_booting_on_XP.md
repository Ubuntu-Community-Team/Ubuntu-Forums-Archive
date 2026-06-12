---
title: "how to change boot order for booting on XP?"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by cacabuda on 2005-05-14
Hello,

I've installed ubuntu and now i have some kind of boot manager at each start.
By default, the system choose to launch ubuntu (Windows XP is at the end of the list). I would like to put Windows XP at the begining of the list, so that the system launches Windows.
How to do that?

Thanks,

---

### Post by Xian on 2005-05-14
Just edit your /boot/grub/menu.lst file and either change the default entry number or arrange the bootable partitions that are listed to however you desire.

---

### Post by monchichi on 2005-05-14
I can't imagine *why *you'd ever want to do such a thing, but if you must, edit the file /boot/grub/menu.lst:```
 sudo gedit /boot/grub/menu.lst
``` and change the order of the entries at the bottom of the file. The topmost entry is the default boot.

---

### Post by arctic on 2005-05-14
open a terminal (right-click on your desktop and select the terminal menu-entry). now  type the following:
sudo gedit /boot/grub/menu.lst
it will ask you for the superuser password. once entered, an editor should show up with the bootloader entry. there should be something like this at the end of the list:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
simply move this selection before the first ubuntu entry, so your menu.lst looks similar to this:
```
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
..... 
```
in order to change the default selection (=not use the first boot-selection by default), change the following entry:
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```
replace the default number "0" with the selection number you want to boot by default. and change the timeout seconds to what you want them to be.

good luck. :)

---

### Post by bored2k on 2005-05-14
Wait wait these methods are all sort of delicate , aren't they ?
I suggest you get grubconf , wich is a graphical manager for this on 
[http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/) . It will really help you avoid problems..

[img]http://img25.echo.cx/img25/7489/screenshotgrubconf6gc.png[/img]

---

### Post by arctic on 2005-05-14
nope, they are not delicate. getting the hands a bit dirty is a good learning experience.
also... is grub-conf finally bug-free? i (and others) had some rather annoying problems with it in warty.

---

### Post by bored2k on 2005-05-14
[QUOTE=arctic]nope, they are not delicate. getting the hands a bit dirty is a good learning experience.
also... is grub-conf finally bug-free? i (and others) had some rather annoying problems with it in warty.[/QUOTE]
 I heard it was crappy on Warty, but I've been using ever since Hoary's Release Candidate, and I have had no problems with it. The menu list item doesn't open because it requires root privileges, but it works through konsole/gnome-term.

---

### Post by cacabuda on 2005-05-14
Hello Twice,

Thanks everyboy for your answers.  :grin: 
In fact my question has already been posted and answered (you can see it if you have the will to go to the page 11 and read the latest post  \\:D/ ).
I've edit the menu file, but i think the graphical manager solution is interresting too. :wink: 


So once more thanks a lot.

---

### Post by orangeacid on 2005-06-14
Hey, cheers for the posts.  I was dreading having to sign up and wait for a reply but this is great.  Looks like I'll be coming here more often  :)

---

### Post by bored2k on 2005-06-14
[QUOTE=orangeacid]Hey, cheers for the posts.  I was dreading having to sign up and wait for a reply but this is great.  Looks like I'll be coming here more often  :)[/QUOTE]
 [img]http://www.drycreekrun.com/WELCOME%20FISHERMAN.jpg[/img]

---

### Post by ~Maxx on 2008-01-16
Great answers - worked for me too.  Thanks!

---

### Post by cotamayor on 2008-01-31
Great answers. They worked great.

This is my case:

Once upon a time there was a Lunux enthusiast that decided to install Ubuntu on his laptop. unfortunately his wireless network decided not to work even with Ndiswrapper, so he decided to let Ubuntu sit on his computer for some time. 

One day Gutsy was released and he decided to give a second chance to Ubuntu, after downloading the new version, he burned it in a CD and Installed Ubuntu 7.10 with Windows Vista and Ubuntu 7.04.

All the OSes were living happy together until he needed to unstall Solaris in his laptop. He decided it was the momento to erase one of the Ubuntu releases and dedicate that space to Solaris. He formatted his partition and suddenly neither Ubuntu Windows or Solaris were present, after two days of researching the net he found that GRUB was installed in the partition he deleted and ERROR 22 was all the time on the screen. 

He decided to run the live CD and Install GRUB, but his efforts were futiles, then after struggling for hours he decided to re-install Ubuntu 7.10 instead of 7.04 Finally that solved the problem and the OSes were happy together again, but there was a catch, the new Ubuntu was very slow to start, and it wasn't personalized as the user wanted, so he decide to do some research on changing the booting order and Voila, Here I am... and it worked

The score is 
OSes = 1
User  = 1

Only one more thing I need to get rid of one of my ubuntus but I don't want to mess again with the frightening GRUB can somebody point me in wich direction I have to go? 

Thanks in advance.

---

### Post by imtheguru on 2008-01-31
> **monchichi said:**
> I can't imagine *why *you'd ever want to do such a thing, but if you must, edit the file /boot/grub/menu.lst:```
 sudo gedit /boot/grub/menu.lst
``` and change the order of the entries at the bottom of the file. The topmost entry is the default boot.Poor choice of command.

Use gksu with graphical applications; sudo can seriously break your .ICEauthority

Cheers.

---

