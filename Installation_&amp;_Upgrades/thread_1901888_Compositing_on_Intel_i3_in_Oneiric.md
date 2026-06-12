---
title: "Compositing on Intel i3 in Oneiric"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by jandac2011 on 2011-12-29
Desktop effects worked without problem in natty. When I upgraded to oneiric, one of many problems in that worst of upgrades so far is that they stopped working. I verified that this is not a problem with my personal settings: desktop effects still work flawlessly in live kubuntu 11.04, and they do not in live 11.10. I get a message that effects: Blur, Box Switch, Cover Switch, Desktop Cube, Dashboard, Desktop Grid, Dialog Parent, Fade, Highlight Window, Login, Logout, Minimize Animation, Outline, Present Windows, Screenshot, Slide, Sliding Popups, Starting Feedback, Taskbar Thumbnails, Translucency and Zoom had to be turned off.

> ~ $ uname -a
Linux kizomba 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

I have an Intel Core i3 540 @ 3.07 GHz with an integrated graphics card and no additional graphics card. I have 16GB of RAM.

Is it possible to use an older version of xserver or kwin so that I can use desktop effects? I am not fan of compositing, but since compositing became standard, switching it off leaves an interface with an ugly look resembling pure Tcl/Tk.

This issue is just one of several I have with this worst version of Kubuntu ever:
[LIST=1]
[*]After some attempts to change the effects (perhaps), I can no longer log in immediately. The process plasma-desktop sleeps for almost exactly 5 minutes before I can see my desktop. This is something in my personal settings, as new test users don't have that effect, but I don't know which setting it is.
[*]New users have to change their password the first time they log in. However, they cannot do that the first time a popup window shows up - all keyboard input is blocked. The second time (I press Escape) entering the password is interrupted after a short delay - it looks like a very short timeout. This happens in kdm.
[*]I use kdm as I regard new gdm and lightdm (or so) insecure as they show the list of users. However, contrary to previous versions, there seems to be no way to specify KDE as the default window manager (not in e.g. .dmrc). This should be in the Control Center! It seems impossible to choose a session type with keyboard; I have to use mouse for that.
[*]Invoking Firefox sometimes crushes the window manager, and I'm returned to kdm.
[*]Miro and vlc often crash desktop-plasma.
[*]Konqueror very often freezes for about a minute, usually when opening a new tab with some flash content. Sometimes scrolling stops working - moving slidebars or pressing PgUp/PgDn only moves the bars, not the contents. BTW, an upgrade of adobe flash plugin installer some time ago (2 months ago?) made watching flash video impossible in konqueror. It was corrected in 11.10, but not in 10.04, which is supposed to be a stable version (I use it on a different computer).
[/LIST]

---

### Post by searchfgold6789 on 2011-12-29
Which graphics card do you have? P.S. you can find out by typing into the terminal ```
sudo lshw -c display
```It's possible that you need graphics card drivers. You can install them automatically using Jockey: K menu > Applications > System > Additional Drivers.
If Jockey doesn't display anything, or it displays that you already have a graphics driver activated, then tell us. In any case you'll need to find out what your GPU is.

I agree. Kubuntu 11.10 sucks. So I stuck with 11.04. Don't know what I'm going to do once it runs out of life.

---

### Post by jandac2011 on 2011-12-29
> **searchfgold6789 said:**
> Which graphics card do you have? P.S. you can find out by typing into the terminal ```
sudo lshw -c display
```It's possible that you need graphics card drivers. You can install them automatically using Jockey: K menu > Applications > System > Additional Drivers.
If Jockey doesn't display anything, or it displays that you already have a graphics driver activated, then tell us. In any case you'll need to find out what your GPU is.

I agree. Kubuntu 11.10 sucks. So I stuck with 11.04. Don't know what I'm going to do once it runs out of life.
It is the graphics card that is integrated with the Intel Core i3 processor (it is inside the processor):
```
$ sudo lshw -c display
[sudo] password for jandac: 
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fb800000-fbbfffff memory:e0000000-efffffff ioport:ff00(size=8)

```
As to K menu > Applications > System > Additional Drivers: it shows no drivers, and it says "No proprietary drivers are in use on this system".

The unity_support_test says the card is compatible, so it should run KDE as well. And it did in the previous Kubuntu version.

---

### Post by jandac2011 on 2012-01-03
Just an update, but only to the other errors. I would still like to know how I could get desktop effects like in natty.
> **jandac2011 said:**
> 
[LIST=3]
[*]I use kdm as I regard new gdm and lightdm (or so) insecure as they show the list of users. However, contrary to previous versions, there seems to be no way to specify KDE as the default window manager (not in e.g. .dmrc). This should be in the Control Center! It seems impossible to choose a session type with keyboard; I have to use mouse for that.
[/LIST]
New users log in to KDE directly. Calling Gnome (unity) instead of KDE seems to be related to that long sleep of plasma-desktop.

---

### Post by maverick555 on 2012-01-09
system settings--> check disable functionality check at startup.:popcorn:

---

### Post by jandac2011 on 2012-02-21
> **maverick555 said:**
> system settings--> check disable functionality check at startup.:popcorn:
It took me some time to find what system settings->disable functionality check at startup meant. It is at System settings->Desktop effects->Advanced tab.

Yes, it worked. I have also found why the display in KDE freezes for 5 minutes after login, but this should be a subject for a separate post. Thanks a lot!

---

### Post by jandac2011 on 2012-03-01
> **maverick555 said:**
> system settings--> check disable functionality check at startup.:popcorn:
This also solves (huge) problems with stability of Firefox and Miro. I suspect that there must be a similar switch somewhere in Ubuntu Unity that still always loads as default in kdm and remains crippled, i.e. the left bar does not show up, and using the trick with --replace and changing some options works only till the end of the session.

---

