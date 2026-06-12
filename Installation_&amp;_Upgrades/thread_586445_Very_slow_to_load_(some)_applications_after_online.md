---
title: "Very slow to load (some) applications after online upgrading to Gusty"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by moairmoair on 2007-10-22
Hi,

The applications still load, but very slowly after about 20-30 seconds of delay. Once running they seem working fine. And its only happening to some of the applications. 

Fast as before the update:
Calculator, Folders on the Desktop (Nautilus), Geany editor, MySQL Query Browser, flpsed, Gimp.

Noticeably slower than before update to 7.10:
Home Folder, Accessories/Dictionary, Default Terminal, Google Earth, Evolution, Opera, Tomboy, OpenOffice Word, gedit ...

Double clicking on folders (on the Desktop) loads Nautilus immediately. But choosing Places/Home Folder or clicking on the Trash icon takes a long time to launch Nautilus.

The slowing down does not increase CPU  consumption. It seems the slowed programs are just waiting for a while (without hard disk accessing) for something before they show up.

The following packages are removed at the end of the update.

binfmt-support
feisty-session-splashes
gcj-4.1-base
gij-4.1
gnome-cups-manager
libgda2-3
libgda2-common
libgnomecupsui1.0-1c2a
liblzo1
libportaudio0
libslab0
libstlport5.1
openoffice.org-filter-mobiledev
ttf-baekmuk
vnc-common
xvncviewer

Any ideas what's going wrong? 

Thanks
Moair

---

### Post by chek2fire on 2007-10-22
Are you running and compiz-fusion?

---

### Post by upboardin on 2007-10-22
I am having this exact same problem on 2 of my computers. One is a Thinkpad T42p with 2gb of ram, 128m ATI Radeon. The second is a P4 2.4 Ghz with 1.5m ram and a Nvidia fx 5500. 

Its exactly like moairmoair states. I try to open terminal, no hard disk access, no noticeable CPU usage. It just waits. it take 20-30 seconds to load the terminal as well with other software.

The t42p was an upgrade from Feisty.  The desktop was a clean install.

And no Compiz is not running on either computer


Thanks

---

### Post by moairmoair on 2007-10-22
> **chek2fire said:**
> Are you running and compiz-fusion?


I enabled extra effects (only shadows and wobbly no 3D)  through System/Appearance right after the upgrade. It looked fine on the first try. But I wobbled the window so hard it moved between workspaces and crashed the user interface (Ctrl+Alt+arrows to switch workspaces still worked but non of the opened  windows, desktop icons or the task bars showed up, only the background image was displayed). After a power-off restart i disabled the effect. 

Now I'm getting the 'Desktop effect couldnot be enabled' message testing to enable the effects. 

My machine is a Dell Inspiron 600m (1.5GH, 512M, 40G, ATI Radeon 32M). More specifications at [http://reviews.cnet.com/laptops/dell-inspiron-600m/4507-3121_7-20906173.html](http://reviews.cnet.com/laptops/dell-inspiron-600m/4507-3121_7-20906173.html) 

Thanks

---

### Post by moairmoair on 2007-10-22
[QUOTE=upboardin;3602565.  The desktop was a clean install.[/QUOTE]

Thanks Upboardin. Otherwise I might be doing a clean install now :)

---

### Post by ThUnD3rM0rPh on 2007-10-22
have the same problem but only on the home folder and another shortcut i have made.no compiz fusion on a acer 1694wlmi

---

### Post by ThUnD3rM0rPh on 2007-10-22
installing compiz following this guide somehow fixed it.
[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)

can't figure out why, but i don't care right now. hehe

---

### Post by avsa242 on 2007-12-18
I would like to know if any of you ever figured this out? My mother's laptop (Presario C552US, Celeron 1.6) exhibits this behaviour and I haven't been able to figure it out. It seems like it's inter-process-communication related (i.e., dbus, etc) but I'm not experienced with it enough to know for certain.

Cheers,
Jesse

---

