---
title: "Compiz slow in Lucid kernel, run normail in karmic kernel"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by donnykurnia on 2010-07-30
First, if this question is in a wrong category, please edit and move it in the correct one.

When Lucid released, I upgrade the Karmic in my Thinkpad R61 using ```
apt-get dist-upgrade
```

The upgrade went smooth, with some minor problems like no sound, but I have fix it using this link: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

One things that remains until today is that when I'm using latest kernel (right now 2.6.32-24), the compiz run very slow, make the whole desktop unusable. When compiz is killed and using metacity, the desktop is running in normal speed.

Fortunately I still had the Karmic kernel (2.6.31-20) and booting using this kernel, everything run normally.

I just wonder what cause the latest kernel make compiz become slow. Is there any leftover application that I had to uninstall (maybe it's like pulseaudio's problem above), or any missing library/application that I need to install?

If this is a bug, is there any ticket for this and a fix?

TIA

---

### Post by ptn107 on 2010-07-30
Are you using Ubuntu's supplied open-source video drivers or ones you downloaded from the web?

---

### Post by donnykurnia on 2010-07-30
Hi ptn107,

I'm using intel driver from main repository:

$ dpkg -l|grep xserver|grep intel
ii  xserver-xorg-video-intel               2:2.9.1-3ubuntu5                       X.Org X server -- Intel i8xx, i9xx display driver

Is there any other information that I need to supply to help finding the solution?

---

### Post by donnykurnia on 2010-07-30
Hi ptn107,

I'm using intel driver from main repository:

```
$ dpkg -l|grep xserver|grep intel
ii  xserver-xorg-video-intel               2:2.9.1-3ubuntu5                       X.Org X server -- Intel i8xx, i9xx display driver
```

Is there any other information that I need to supply to help finding the solution?

---

### Post by ptn107 on 2010-07-31
> **donnykurnia said:**
> Is there any other information that I need to supply to help finding the solution?

lspci -nn
lspci -v

---

### Post by donnykurnia on 2010-07-31
> **ptn107 said:**
> lspci -nn
lspci -v

Here it is in the attachment. I'm also include ```
dpkg -l
``` result, so maybe there are missing essential Lucid package in my installation, or there are obsolete package that must be removed.

---

### Post by ptn107 on 2010-08-01
I too have integrated Intel video on my Dell laptop using the same [i915] driver.  I cannot figure out why yours would be slowing down.  Try searching launchpad.net/ubuntu for a bug related to your problem.  If none exist open one.  May I suggest a clean install also?  That may be a bit drastic?

---

### Post by davidmohammed on 2010-08-01
I also have an intel graphics (855GM).  Compiz also slowed down to make the desktop unusable.

I installed the compiz fusion icon

right clicking the icon displays a menu - make sure BOTH

loose binding and indirect rendering are both ticked

for some reason, indirect rendering was not ticked on my install and compiz made the desktop unusable.

---

### Post by donnykurnia on 2010-08-01
Yeah, clean install is an ultimate way. Unfortunately I still have projects near deadline. After that, I might have time to do clean install.

I just want to know if anyone had similar problems, or know something that might be the cause of this problems. Doing clean install every 6 month is quite wasting time. I prefer to do dist-upgrade to kept all my current application settings.

---

### Post by donnykurnia on 2010-08-01
@davidmohammed,

I had Compiz Fusion icon installed, and in my setting, only indirect rendering ticked, loose binding is not. Using old Karmic kernel, this setting is working well. I will try the Lucid kernel now, see if this is the main cause of the slowness in Lucid. Thank you for sharing the info.

---

### Post by donnykurnia on 2010-08-02
@davidmohammed,

I try to activate Loose Binding while using old kernel. It doesn't show any effect, since the compiz run normally here. I reboot my laptop and using latest kernel. Even with Loose Binding and Indirect Rendering ticked, it still slow.

However, when I un-tick both checkbox, then only activate Indirect Rendering option, the compiz now running normally, just like when I'm using old kernel.

I don't know if this related, but it seema that deactivate Indirect Rendering then reactivate it make the compiz now working well. I need to reconfirm this by rebooting. If it still working well, then it is the reason and solution for those who had similar problems with mine.

---

### Post by donnykurnia on 2010-08-02
I have reboot my laptop. Compiz slow again. Looks like I had to spend a few minute to disable then re-enable Indirect Rendering to make the desktop usable.

Is there any way to automate this process, instead of doing it manually? Via command line maybe, I can do a command to disable indirect rendering, pause, then re-enable it?

---

### Post by davidmohammed on 2010-08-02
compiz settings (I think) are stored in ~/.gconf/apps/compiz

suggest rename and folder to something else - it should get recreated when you switch from "no effects" to "normal effects" in the visual effects tab.

---

### Post by donnykurnia on 2010-08-02
~/.gconf/apps/compiz folder mostly have empty %gconf.xml file. I cannot found Indirect Rendering and Loose Binding settings in there. It only store the effect that I have set.

The problems is not with the effects. When I deactivate then reactivate Indirect Rendering, compiz with my settings run normally. I just need to know a way to do deactivate-reactivate automatically when I start the laptop. I haven't try it after waking up from hibernate yet. I'll post my findings later.

---

