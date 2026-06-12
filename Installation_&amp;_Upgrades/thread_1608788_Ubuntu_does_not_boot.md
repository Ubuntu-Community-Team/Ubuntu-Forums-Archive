---
title: "Ubuntu does not boot"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by JTU50 on 2010-10-29
I am totally new to Ubuntu.  I am trying to install Ubuntu Server 10.10 on an old Compaq 700mHz with a 30GB HD, and at least 1MB RAM (dopn't remember exact amount). Downloaded iso file, extracted, burned to CD and installed from CD.  All seemed to go well. When machine went to reboot after installation all I get is a flashing cursor " _ ". Tried repair broken install from CD - doesn't find anything wrong. Add'l info, computer has IDE drive, yet when I try to list files (ls) after booting from CD all that is listed are sda drives. Only thing I couldn't do was set up network - need to get a new NIC.
 
Suggestions please.
 
Jeff

---

### Post by peyre on 2010-10-29
First thought, why not try a desktop version of Ubuntu?  You could even try a lightweight version like Xubuntu or even Lubuntu (though Lubuntu 10.10 makes Wine crash on my system).  If you're new to Ubuntu, a GUI might help lower the learning curve--but more importantly, you might have success with a desktop version if the server version is choking on you.

---

### Post by avtolle on 2010-10-29
> **JTU50 said:**
> I am totally new to Ubuntu.  I am trying to install Ubuntu Server 10.10 on an old Compaq 700mHz with a 30GB HD, and at least 1MB RAM (dopn't remember exact amount). Downloaded iso file, extracted, burned to CD and installed from CD.  All seemed to go well. When machine went to reboot after installation all I get is a flashing cursor " _ ". Tried repair broken install from CD - doesn't find anything wrong. Add'l info, computer has IDE drive, yet when I try to list files (ls) after booting from CD all that is listed are sda drives. Only thing I couldn't do was set up network - need to get a new NIC.
 
Suggestions please.
 
Jeff
Well, if you indeed extracted from the iso then that is likely part of the problem. Just burn as an image without extraction, and give it another try.

---

### Post by JTU50 on 2010-10-29
Thanks for the responses. Perhaps I used the wrong terminology re extracting. After downloading the iso, I used program called ImageBurn to burn image to disk and used that to install - which did seem to go as it was supposed to - it booted, from cd, gave messages as installation proceded, etc.

---

### Post by Old_Grey_Wolf on 2010-10-29
Are you expecting a GUI interface? You can install a GUI interface on the Server with one of the following commands. With a 700mHz processor, I would recommend XFCE or LXDE.

For Gnome use
```
sudo apt-get install ubuntu-desktop
```

For KDE use
```
sudo apt-get install kubuntu-desktop
```

For LXDE use
```
sudo apt-get install lxde
```

For XFCE use
```
sudo apt-get install xubuntu-desktop
```

---

### Post by peyre on 2010-10-29
> **Old_Gray_Wolf said:**
> Are you expecting a GUI interface?

A "GUI interface"?  Isn't that redundant? :D

---

### Post by Old_Grey_Wolf on 2010-10-29
> **peyre said:**
> A "GUI interface"?  Isn't that redundant? :D

Yes, it is.

---

### Post by JTU50 on 2010-10-30
No, I'm not expecting a GUI. But I get no response from trying any command. In fact, I don't even get a login prompt on boot, just a blinking line as noted in prior post.

---

