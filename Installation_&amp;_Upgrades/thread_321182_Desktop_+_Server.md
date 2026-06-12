---
title: "Desktop + Server"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Bruderhead on 2006-12-18
Hi,

Very new to Ubuntu and Linux, though I did admin a small Solaris system a decade ago (lots of familliar-looking stuff here). Recently built a new Win machine and am converting old machine to Ubuntu. Using it to (re)learn, and hope to eventually build my own email/web/FTP server.

Question is, I would like to use Ubuntu SERVER (LAMP), but am not ready to give up the desktop GUI (Gnome). The server install provides only the former; the desktop install only the latter. So, what is the easiest way to get both? Install server and add Gnome, or install desktop and add (L)AMP? 

Either way, where can I get the correct packages, and will the install be as simple as the overall Ubuntu install? I have the disks for both server and desktop, in both Dapper and Edgy.

Any guidance would be appreciated greatly.

Thanks!

---

### Post by tkjacobsen on 2006-12-18
I would go for an edgy desktop install, then add the lamp-server following this wiki: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)..

This will give you the easiest desktop installation. And you have to configure the server anyway.

If you really care for stabillity use Dapper instead of edgy, though edgy should do the job fine, it also has better/more apache2 modules.

---

### Post by NumberOne on 2006-12-18
I installed the LAMP server then installed the gnome desktop.  It is pretty easy.

After you install the LAMP server, from the command line type this.

sudo apt-get install ubuntu-desktop

You will need a high speed internet connection and you server install disk.  depending on the speed of you PC it should take about 20 mins.

---

### Post by Bruderhead on 2007-03-09
Holidays and work travel grossly delayed this project.

Thanks for the recommmendations ... it really was pretty easy!

Now for all the configuration ...

---

### Post by EvilMarshmallow on 2007-03-09
I just followed NumberOne's instructions and I have the "X server failed to load" message when I attempt to log in.

I tried to do dpkg-reconfigure but it says that xserver-xorg isn't installed?

Did I miss a step somewhere?  It tells me GDM is running but can't start X.  This is an old PC with a VGA connection on the motherboard.

---

### Post by zvacet on 2007-03-09
```
  sudo dpkg-reconfigure xserver-xorg
```
choose vesa driver

---

### Post by EvilMarshmallow on 2007-03-10
I discovered that xorg didn't install at all.

Now I'm getting errors because it's looking for a theme that doesn't exist.

---

### Post by cje on 2007-03-17
got the same problem ...

---

### Post by EvilMarshmallow on 2007-03-19
Try apt-get install ubuntu-desktop again.

I got it to work once, then I decided to go hardcore :lolflag: and reinstalled without a gui.

I think in the process of doing the ubuntu-desktop the first time, some of the installations failed and I didn't see it.

---

### Post by zvacet on 2007-03-20
```
sudo aptitude install ubuntu-desktop
```

---

