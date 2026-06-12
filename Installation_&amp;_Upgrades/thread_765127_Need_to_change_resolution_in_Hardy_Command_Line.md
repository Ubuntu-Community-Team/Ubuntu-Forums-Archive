---
title: "Need to change resolution in Hardy Command Line"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Afkpuz on 2008-04-24
Hello, I just downloaded Hardy and it seems that the installation process has changed.  I have a large CRT monitor with a resolution of 800x600.  In the past, I used an alternate install CD and selected that resolution in the text installer.  Now, Hardy doesn't present me with that option and it tries to run my resolution at something way too high to see anything.  So, how do I change the resolution and refresh rate through the command line recovery console?  Oh, and I've installed hardy, I just cannot boot it up.  The screen turns to fast moving lines that make no sense.

I check xorg.conf and it looks really different than previous versions.

Here are the specs I Need

Res: 800x600
Vert Ref: 60
Horiz ref: 31

Can anyone help?

---

### Post by Peter09 on 2008-04-24
Boot into safe mode, that will give you a text based prompt.

What graphics card have you got?

PC

---

### Post by Afkpuz on 2008-04-24
Nvidia geforce 8600 GT I think.  I know how to get to the command line, I just don't know what to edit anymore.  Hardy is so different! My xorg.conf file looks nothing like what it used to after fresh install.  I just need to know where I can configure my resolution and refresh rate in the command line and the syntax to do it.

---

### Post by Peter09 on 2008-04-24
Try typing 

```
envyng -t
```

at the command prompt. It will do a good job of installing the nvidia drivers.  you can the use

```
nvidia-settings
```

to setup the screen


PC

---

### Post by Afkpuz on 2008-04-24
says there's no such command as 
```
envyng
```

and I double checked my spelling too.  Does anyone know which text file I can edit to change my resolution?

---

### Post by eriqjaffe on 2008-04-24
You need to download envyng...

```
sudo apt-get install envyng-gtk
```

You might also need to grab envyng-core, I can't remember if apt will download that automatically or not.  Once that's installed, you can run envyng from a terminal.

---

### Post by howlingmadhowie on 2008-04-25
i wouldn't worry about envy unless you're using an nvidia of an amd card. 

does ```
dpkg-reconfigure xserver-xorg
``` still work?

don't worry. i've just tried it. it doesn't.

---

