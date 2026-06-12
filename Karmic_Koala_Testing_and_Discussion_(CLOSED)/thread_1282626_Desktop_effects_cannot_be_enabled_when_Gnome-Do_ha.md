---
title: "Desktop effects cannot be enabled when Gnome-Do has started"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Maupertus on 2009-10-04
Hi Everyone,

I'm pretty sure that when I first installed Karmic on my EEEpc 904HA with integrated 945 GME graphics chip, Compiz worked just fine. 

However, I just installed Gnome-Do, and everything seemed to be working fine for a moment. But then ... I restared the computer.

Now I just came to the conclusion that Compiz apparently crashes with Gnome-Do. Is anybody else experiencing this problem?

How can I best determine this problem for a bug-report?

---

### Post by FatalChaos on 2009-10-04
I'm not sure it is related to gnome do. I'm having the same problem with the same card, but when I disable gnome do it still happens. Furthermore, everything is just slow right now.

---

### Post by wilee-nilee on 2009-10-04
On Karmic, Gnome-Do the PPA version comes up as a black square that is unreadable, and the auto-scroll icon in Firefox is just a black dot although it works. The graphics stuff is probably not set up yet.

---

### Post by Maupertus on 2009-10-05
I don't know what the problem is. I thought I had it, but I haven't experienced any problems since doing the following.

- Start up Karmic.
- Remove Gnome-Do from the Startup Applications list.
- Restart Karmic.
- Gnome-Do doesn't start, and now it is possible to enable (all) desktop effects.
- Put Gnome-Do back in the Startup Applications.
- After Reboot, I haven't encountered any problems.

(I have to admit I'm a little bit hesitant to recreate the problem ;)

---

### Post by Maupertus on 2009-10-05
> **Maupertus said:**
> I don't know what the problem is. I thought I had it, but I haven't experienced any problems since doing the following.

- Start up Karmic.
- Remove Gnome-Do from the Startup Applications list.
- Restart Karmic.
- Gnome-Do doesn't start, and now it is possible to enable (all) desktop effects.
- Put Gnome-Do back in the Startup Applications.
- After Reboot, I haven't encountered any problems.

(I have to admit I'm a little bit hesitant to recreate the problem ;)

And alas, this doesn't work every time.... grrr

---

### Post by Forlong on 2009-10-05
I don't use Gnome-Do but I reckon it uses some form of transparency. If Compiz isn't running it most probably enables Metacity's transparency, which isn't compatible with Compiz (Metacity is GNOME's default window manager).

Next time Compiz can't be enabled, use this to check why that is: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by rburkartjo on 2009-10-05
i have the same problem and all my updates are current

---

### Post by Bufke on 2009-10-05
This happened to me too.  I had to do a 
sudo dpkg-reconfigure -phigh xorg-server
and reboot. That made desktop effects work again and the desktop no longer very very slow.

---

### Post by Maupertus on 2009-10-11
Well, I have been playing around for the lesser part of a week and it's strange but I have to start compiz manually from terminal. After I've entered "compiz" without even closing Gnome-Do, everything works fine and fast.

If I want to enable compiz via the appearance menu, it only works after terminating gnome-do and metacity in the system manager.

Now, although this isn't a real deal breaker, it would be great if this wasn't necessary. So, how do I discover the reason of this strange bug?

---

### Post by sdowney717 on 2009-10-11
install and run 'fusion-icon'
this gives you a nice icon on the panel to control compiz emerald etc...
you can also set it up in the startup programs.

---

### Post by Maupertus on 2009-10-11
> **sdowney717 said:**
> install and run 'fusion-icon'
this gives you a nice icon on the panel to control compiz emerald etc...
you can also set it up in the startup programs.

It's a nice workaround, and I've thought about it, but come on...it should just work.

I wanted to post the outcome of starting Compiz from terminal, I hope someone can spot anything going wrong.

[QUOTE= Terminal -> Compiz]maupertus@myeepc:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

[/QUOTE]

---

