---
title: "How do you exit X? or reboot without lauching X"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by CrazyTn on 2007-03-02
I am trying to install my video card driver, but need to exit X first.
Don't think Ubuntu has an /etc/inittab file

So How do I do it in Ubuntu?

Thanks in advance

---

### Post by Kateikyoushi on 2007-03-02
Select recovery mode in grub that will boot you to terminal. If it ins't called recovery mode please let me know, I forgot the name.

---

### Post by mikewhatever on 2007-03-02
Alt+Ctrl+F1 to exit X.
Alt+Ctrl+F7 to get back.

---

### Post by CrazyTn on 2007-03-02
> **mikewhatever said:**
> Alt+Ctrl+F1 to exit X.
Alt+Ctrl+F7 to get back.

I have done some reading, and Ctrl+Alt+F1 doesn't exit X. X will so run in the backgroud

---

### Post by CrazyTn on 2007-03-02
> **Kateikyoushi said:**
> Select recovery mode in grub that will boot you to terminal. If it ins't called recovery mode please let me know, I forgot the name.

Ok thanks, 

THink itis called something like Ubuntu 6.10 (recovery mode)

---

### Post by CrazyTn on 2007-03-02
Recovery Mode is at runlevel 1, and I want runlevel 3
is there another way?

When I ran in recovery mode, the root user is automatically logged in. Is there a way for it to ask the id and password first?

---

### Post by zba78 on 2007-03-13
> **CrazyTn said:**
> I have done some reading, and Ctrl+Alt+F1 doesn't exit X. X will so run in the backgroud

Ctrl+Alt+F1 will get you to the terminal. make whatever changes you need, then press  Ctrl+Alt+F7 to return to your old X. Then press  Ctrl+Alt+Backspace to restart X which will load with your new settings

---

### Post by TheMono on 2007-03-13
I haven't tried this, so don't quote me, but I don't see why it wouldn't work, if you actually wanted to EXIT X, to do :

Ctrl+alt+F1
Login
killall X

---

### Post by Rui Pais on 2007-03-13
Kill X is drastic! (sounds like a mystery plot :lol:)

A simple:

Alt+Ctrl+F1
login
sudo /etc/init.d/gdm stop
Install what you want
sudo /etc/init.d/gdm start

this last one will restart x server and gdm

---

### Post by dams on 2007-03-13
Try using telinit it changes the run level.

---

### Post by Rui Pais on 2007-03-13
> **dams said:**
> Try using telinit it changes the run level.

The OP  don't want to change run level. 
He/she just wants to stop X server to install a video driver that requires that X would not be running at all (nvidia, at least, requires that)

---

### Post by augur80 on 2007-03-13
> **Rui Pais said:**
> Kill X is drastic! (sounds like a mystery plot :lol:)

A simple:
Ctrl+F1
login
sudo /etc/init.d/gdm stop
Install what you want
sudo /etc/init.d/gdm start

this last one will restart x server and gdm

This is the most effective method suggested.  However, you may need to change the first key sequence above to:

```
Ctrl+Alt+F1
```

After you finish with these commands, you may need to switch back to the gdm tty7 by issuing the key sequence:

```
Ctrl+Alt+F7
```

After changes, the proper sequence of commands should be:

```
Ctrl+Alt+F1
login
sudo /etc/init.d/gdm stop
Install what you want
sudo /etc/init.d/gdm start
Ctrl+Alt+F7
```

(Note:  gdm is for stopping gnome, make sure you change this to the proper command to stop KDE if you are using kubuntu)

If you are installing proprietary video drivers, make sure you remember this sequence of commands, since it will need to be done every time the kernel image is updated.

Have fun, just did it myself after a new kernel update.

---

### Post by Rui Pais on 2007-03-13
yes of course Ctrl+Alt+F1 or other way you wont leave the graphical console. 
Thanks for the correction, i'll just didn't give much attention on that cause that part the OP have already done and know how to switch consoles :)

i'll change my posts, anyway, to avoid misleading anyone in error.

---

### Post by Orinoco on 2007-03-22
Like the OP, I am trying to install NVDIA drivers on my laptop to match the wide screen.  
When I type Ctrl+Alt+F1 as recommended, my screen goes blank and nothing happens.  This behavior occurs whether or not I've opened a terminal first.  

I have installed edgy from a CD and have done nothing else to the system.  The application programs that come with the install (OpenOffice.org, Gimp, Totem) all seem to be working.  

What should I do?  The VLC player needs a proper screen resolution to show videos correctly, and Blender, while working, stretches everything out across the screen because the default resolution isn't quite wide enough.

---

