---
title: "Text screen"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by COLiNx86 on 2007-11-08
Ok so i just upgraded to Ubuntu 7.10 from 7.04 but now when i turn it on instead of going to a login screen. where i type my password and username it goes to like a text mode screen kind of like a terminal. what happened? how can i fix this?

---

### Post by taurus on 2007-11-08
After log in with your username and password, what happens if you run this command from a prompt?

```
startx
```

---

### Post by COLiNx86 on 2007-11-08
Sorry it took so long to reply (school) but when i do that it says a bunch of stuff and then says fatal error.
I also tryed the gdm restart thing but it didn't work either.

---

### Post by reckless2k2 on 2007-11-08
did you by chance use a proprietary video driver in 7.04? if so, you've got to edit xorg.conf back to standard then reinstall the driver back in.

---

### Post by COLiNx86 on 2007-11-08
Well being the noob i am i don't know for sure what a proprietary video driver is, but i have an idea.
I used Envy to install my NVIDIA driver in 7.04. so do i still need to edit xorg.conf? and if so how?

---

### Post by bulldog on 2007-11-08
You can try to login in text mode and type sudo envy
With a little luck you can start envy and remove the driver.

---

### Post by COLiNx86 on 2007-11-08
nope still not working, oh well i'll just go back to feisty

---

### Post by bulldog on 2007-11-08
If you have a nvidia card you have to enable the nv driver.
try in the console ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by taurus on 2007-11-08
Edit /etc/X11/xorg.conf

```
sudo nano -Bw /etc/X11/xorg.conf
```
and change the Driver from "**nvidia**" back to "**nv**".  Save it with <Ctrl>o and exit with <Ctrl>o.  Now, see if X starts.

```
startx
```

---

