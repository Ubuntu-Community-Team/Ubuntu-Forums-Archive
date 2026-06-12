---
title: "How to re-install Hoary?"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by joplass on 2005-05-22
I got this message after I installed "xcompmgr transset":
"I cannot start the X server"
With a blue screen in the background.

I think I have to re-install Hoary.  I tried what I did the first time I installed Hoary but the system does not pick up the cdrom.  It goes to the blue screen right away.  What do I have to do to re-install Hoary???
Thanks in advance.

---

### Post by tmowerman on 2005-05-22
If all you have done is install xcompmgr, try removing the changes made to your X server configuration

```
sudo dpkg-reconfigure xserver-xorg
```

Should do this automatically.  

When this is done, 

```
sudo /etc/init.d/gdm restart
```

Should bring you back to the login screen.  

It is also possible you simply typed something wrong whilst trying to install xcompmgr.

```
nano /etc/X11/Xorg.conf
``` 

Will let you edit the file again

---

### Post by joplass on 2005-05-22
worked!!!
Thanks

---

