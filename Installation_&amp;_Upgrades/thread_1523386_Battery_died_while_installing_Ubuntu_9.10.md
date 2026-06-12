---
title: "Battery died while installing Ubuntu 9.10"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by ZPfunk on 2010-07-03
Firstly, im a new user of Ubuntu (yeah, im a newb *blush* so bring on the hating). This is my first post so excuse me if somewhere in the threads this question has been asked and or answered, but I couldnt find it anywhere, so here goes,

I was in the process of updating my Ubuntu to 9.10 but I left my laptop unattended and forgot to plug it in, so when i came back it had died at an unknown point in the updating process. So upon booting it up i was presented with this. 

usplash: Setting mode 1152x864 failede-4bdf-ac2c-9d1a3d96f30c
usplash: Using mode 1024x768

Ubuntu 9.10 computer-laptop tty1

computer-laptop login:

I entered my login info and this is what followed

computer-laptop login: <login>
Password: <password>
Last login: Sat Jul   3 11:05:18 MST 2010 on tty1
Linux computer-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

computer@computer-laptop:~$

From this point, i have no clue whats going on, or what im supposed to do to get into the desktop environment, any help would be greatly appreciated, if anymore info is needed to help, i have no problems providing it. 

Thanks,
ZPFunk

---

### Post by warfacegod on 2010-07-03
Once you enter your credentials and they are accepted type: startx then hit Enter.

---

### Post by ZPfunk on 2010-07-03
Thanks! It worked. Now I have a blank(black) screen with the mouse on it?? Could this be due to an incomplete installation?

---

### Post by mickie.kext on 2010-07-03
> **ZPfunk said:**
> Thanks! It worked. Now I have a blank(black) screen with the mouse on it?? Could this be due to an incomplete installation?

Most likely. I think you should reboot computer and instead of "startx" you type "sudo apt-get update". Without quotes of course. That should re-do update.

---

### Post by ZPfunk on 2010-07-03
Ok, i tried to do a repair(which its in the process of doing, but if that doesn't work, i'll try to update with sudo. Thanks

---

### Post by warfacegod on 2010-07-03
Yep, that would be my guess. Does hitting Alt+F2 do anything? If so type gnome-terminal into it.

And in there try:

```
sudo apt-get update
```

Then:

```
sudo apt-get upgrade
```

---

### Post by ZPfunk on 2010-07-03
Ok, after doing a Repair, it works, thanks to everyone for all of your help, Much appreciated. Im a happy muffkin camper. :)

---

### Post by warfacegod on 2010-07-03
If that doesn't work, try:

```
sudo dpkg --configure -a
```

and post back any errors it spits out.

---

