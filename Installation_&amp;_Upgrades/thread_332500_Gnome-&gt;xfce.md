---
title: "Gnome-&gt;xfce"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by muxecoid on 2007-01-06
Hey. I've installed xubuntu-desktop under ubuntu. I'm logging in to xubuntu, but GNOME still occasionally takes over the desktop even if I set "Allow Xfce to manage desktop" in Xfce desktop settings.

---

### Post by orb9220 on 2007-01-06
Are you launching any gnome apps when in xfce?

---

### Post by muxecoid on 2007-01-06
> **orb9220 said:**
> Are you launching any gnome apps when in xfce?

Indeed. Lots of GTK apps. Some of them are GNOMEish, I guess.

---

### Post by Pobega on 2007-01-06
If you launch Nautilus Gnome will take over the Xfce desktop. Avoid Nautilus and use Thunar/MC instead, that should work fine.

---

### Post by muxecoid on 2007-01-07
> **Pobega said:**
> If you launch Nautilus Gnome will take over the Xfce desktop. Avoid Nautilus and use Thunar/MC instead, that should work fine.

OK, but GNOME still takes over the desktop at startup. And fxburn does not know to handle DVDs.:( Is there any way to configure GNOME to not manage the desktop?

---

### Post by Edowardo on 2007-01-15
Bump? Having same issue here....

---

### Post by total wormage on 2007-01-15
> **muxecoid said:**
> OK, but GNOME still takes over the desktop at startup. And fxburn does not know to handle DVDs.:( Is there any way to configure GNOME to not manage the desktop?

i'm having the same 'problem', but only when launching nautilus (which is logical..), if you go to your settings manager, then sessions, you should be able to automatically save the session
(i'm not at home now, so i'm only guessing..)
if you exit ubuntu with xfce managing the desktop, it should now also boot with xfce managing :]

(if not i'm guessing that there is a nautilus under your startup programs, of which i do not know the location atm, will be back!)
good luck

---

### Post by muxecoid on 2007-01-15
> **total wormage said:**
> i'm having the same 'problem', but only when launching nautilus (which is logical..), if you go to your settings manager, then sessions, you should be able to automatically save the session
(i'm not at home now, so i'm only guessing..)
if you exit ubuntu with xfce managing the desktop, it should now also boot with xfce managing :]

(if not i'm guessing that there is a nautilus under your startup programs, of which i do not know the location atm, will be back!)
good luck
Did not work. GNOME takes over the desktop at startup too.

---

### Post by ultranoize on 2007-02-14
Hi, I have the same problem. GNOME taking over the desktop. I do not use nautilus (not that I know.). Its really strange  because I change the settings to allow xfce to manage the desktop and in the middle of the session GNOME takes over for no apparent reason.  ??? Have you guys found the solution??  By the way I'm running Xfce 4 Desktop Environment
version 4.4.0 (Xfce 4.4).

thanks ...

---

### Post by spooner on 2007-02-27
I'm having the very same problem. When, I click on the "Allow XFCE to manage the desktop" check button I get a pop-up help message saying...
"To ensure XFCE doesn't manage your desktop when you next start XFCE, please save your session. If you are not using the XFCE session manager you'll need to edit your ~/.config/xfce4/xinitrc file."
Saving the session doesn't seem to work and I looked for this file and I can't find it. I'm getting quite annoyed as the only option that I have come across is a complete re-install of Xubuntu instead of the XFCE over Ubuntu that I have now even thou I have all my programs and apps just the way I like them. I'm going to keep looking for a quick fix untill Fiesty Xubuntu is released.

Compaq Evo N400c laptop, 850Mhz, 256Mb Ram, 120GB HD, Ubuntu 6.10 via XFCE.

---

### Post by orb9220 on 2007-02-27
Look into your system monitor to see what apps are starting on startup. 

If there are gnome specific apps starting like network-manger,beagle,gdesklets?,etc... you need to verify if indeed these apps are indirectlly starting gnome services.

Sorry that is all I can come up with. I had the same problem with xfce awhile back and just about any gnome type app can call up a slew of gnome stuff.

---

### Post by spooner on 2007-02-27
Ok, have solved my problem. I looked in system monitor and indeed I had a few gnome services running. Also, nautilus had started up (not that I've ever asked it to) so I open synaptic searched for Nautilus and completely removed it. Some burning software that I had installed was dependent so I removed that as well.
Problem solved.

---

