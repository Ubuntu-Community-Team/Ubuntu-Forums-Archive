---
title: "Fonts disappeared after upgrade"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by lupus7 on 2006-11-30
Hi!
I've upgraded dapper to edgy and had some errors durign upgrade, but there's last problem, that I can't resovle:
Fonts disappered in gnome-desktop, I have empty squares. GTK-fonts are OK, KDE-fonts are OK, and gnome - not.
I've reinstalled all x-fonts, and see that fonts directory is changed! In xorg.conf I has:
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

And my fonts was installed in /usr/lib/X11. I've copied all "fonts" directory to /usr/share/X11/, making mkfontdir and fc-cache. It doesn't help. I found fonts in /usr/share/fonts/X11/, and tried to write this path to xorg.conf..not seems very help
ful..
How can I find the right path for fonts and how can I "register" it with xorg?
I made "find / | grep 100dpi" and output is [here]("http://iminside.net/filez/output.txt"). Thanks.
p.s. maybe it's only gnome problem? cos in other managers i have all fonts visible, if so - where can I solve the problem in gnome?

---

### Post by spin2cool on 2006-11-30
You're on the right track.  Edgy changed the font directories, which b0rked up somethings upon upgrade.  (I had this problem too).  The main difference is that the "X11" and "fonts" directories are reversed.

So, you'll need to change:
**FontPath     "/usr/share/X11/fonts/misc"**

to:
**FontPath     "/usr/share/fonts/X11/misc"**

Repeat for all of the font paths, reboot, and see if that solves your problems.

---

### Post by lupus7 on 2006-12-06
It doesn't  help :(
Where the gnome saves his fonts config?

---

### Post by lupus7 on 2006-12-07
Anybody..?

---

### Post by lupus7 on 2006-12-08
Like I can see, something wrong with permissions to fonts. I see fonts with root only, not with others users (when I use Gnome). What are right permissions and owners should be to font files?

---

### Post by lupus7 on 2006-12-11
How can I competely remove gnome and install it again? But without remove KDE. Maybe it will help..

---

### Post by lupus7 on 2007-02-09
Up

---

