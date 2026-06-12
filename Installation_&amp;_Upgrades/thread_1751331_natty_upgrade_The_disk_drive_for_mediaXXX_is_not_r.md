---
title: "natty upgrade The disk drive for /media/XXX is not ready yet or not present"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by PablolyonsD on 2011-05-06
I have read several threads about this, however I am either too noobish to understand instructions or they dont work -.-

First off:

[http://ubuntuforums.org/showthread.php?t=1466555&page=3](http://ubuntuforums.org/showthread.php?t=1466555&page=3)

I've tried to use that thread to help but to no avail, i tried to use this:

[http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/](http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/)

BUT I CAN'T OPEN A TERMINAL!!! as i am at a point where the screen says:

***Continue to wait, press S to skip or M for manual recovery.***

so if i run this command : [B]gksudo gedit /etc/fstab  my computer whines about there being no way to show this on the screen,

I have tried this:

[/B]Use a non-graphical editor, like emacs or vi.  Try Ctl+Alt+F3 -- you  should get a login prompt.  Login to an account with admin privileges  (like, the first account you created, for example), and then type 'sudo  vi /etc/fstab'; that will open /etc/fstab in the vi editor.  Make your  changes, save them, exit the editor, reboot...

... but if you're not used to working with a non-graphics-based editor,  you'll have a bit of research to do.  It's not hard, though, just  tedious.


however i have not managed to make it work :(

any help would be appreciated as i need ubuntu for matlab to hand in a coursework in 2 days, so basically, im ******.

Thanks anyways

---

### Post by Dutch70 on 2011-05-06
Hi and welcome to UF

Maybe I'm missing something, but why don't you press S to skip & then edit fstab?

---

### Post by PablolyonsD on 2011-05-06
I could do that but I don't know how to, also I can't use gedit as explained before.....

---

### Post by Dutch70 on 2011-05-06
Yeah, I'm definitely missing something here.

You're saying you don't know how to press the "S" key?

That should get you into the gui so you can use gedit.

---

### Post by PablolyonsD on 2011-05-07
> **Dutch70 said:**
> Yeah, I'm definitely missing something here.

You're saying you don't know how to press the "S" key?

That should get you into the gui so you can use gedit.

Ive tried that before, takes me to a black screen that freezes and remains black....

---

### Post by Dutch70 on 2011-05-07
Do you have a wubi install? Is Ubuntu installed inside of windows programs?

I don't want to lead you down the wrong path, but that sounds like it may be a different problem. 
Try monodeset or other boot options from here...
[[COLOR="Red"]How to set NOMODESET and other kernel boot options in grub2[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=1613132")
Also, there are 2 sticky threads at the top of the "installation & upgrades" forum that may be of some help to you.

---

### Post by PablolyonsD on 2011-05-07
> **Dutch70 said:**
> Do you have a wubi install? Is Ubuntu installed inside of windows programs?

I don't want to lead you down the wrong path, but that sounds like it may be a different problem. 
Try monodeset or other boot options from here...
[[COLOR=Red]How to set NOMODESET and other kernel boot options in grub2[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=1613132")
Also, there are 2 sticky threads at the top of the "installation & upgrades" forum that may be of some help to you.


I don't have wubi, I have ubuntu 10.04 which i just upgraded as mentioned, this error has NEVER happened to me before and im 100% sure its due to the natty upgrade, some time ago dell software messed up my grub2 but i managed to fix it and get it working, this error i have read in a couple of forums and as i mentioned its simply solved by editing that file with jedit etc but i cant even open jedit, thanks for your help anyways, will post some screenshots later

---

### Post by PablolyonsD on 2011-05-07
Maybe this is more clear, I boot up my laptop:

First image on the left, then the second image appears, if i do nothing the third image appears: mountall: Plymouth command failed, disconnected from plymouth,

If i enter s all the time, to skip, the screen turns black with a flashing white _ and does NOTHING.

....

ideas?

when i need ubuntu to hand in frikin courseworks it fails, anyways.

---

### Post by Dutch70 on 2011-05-07
Well, that explains why pressing "S" to skip wouldn't work. 
Unfortunately I don't know what to tell you about that. You can try to boot into an older kernel if you want. 
Maybe someone else will have some more input.

ps. You can use nano instead of gedit by typing...
```
sudo nano /etc/fstab
```
I'm not very good with nano though so you may want to read up on it a little bit. Can't be very difficult.

---

### Post by PablolyonsD on 2011-05-07
> **Dutch70 said:**
> Well, that explains why pressing "S" to skip wouldn't work. 
Unfortunately I don't know what to tell you about that. You can try to boot into an older kernel if you want. 
Maybe someone else will have some more input.

ps. You can use nano instead of gedit by typing...
```
sudo nano /etc/fstab
```I'm not very good with nano though so you may want to read up on it a little bit. Can't be very difficult.

Success with nano, can edit the fstab, however, i can't save!!! It says read only when i try to save, wtf O_o

---

### Post by PablolyonsD on 2011-05-07
ideas??

---

### Post by txapelgorri on 2011-05-11
Hi:

In my case the problem was that I had my upgrade broked, so:
1) Pulse M to get the console
2) Remount / as RW: mount -n -o remount,rw /
3) Finish the upgrade: dpkg --configure -a

Enjoy :)

---

### Post by PablolyonsD on 2011-06-21
I get an error message saying "processing was halted beacuse ,there were too many errors" i have googled but found no solutions, :s

---

### Post by PablolyonsD on 2011-06-21
[http://ubuntuforums.org/archive/index.php/t-954623.html](http://ubuntuforums.org/archive/index.php/t-954623.html) ive run this and failed to fetch numerous webs, could not resolve gb.archive.ubuntu.com

Some index files failed to download. They have been ignored, or old ones used instead.

Ideas??

---

