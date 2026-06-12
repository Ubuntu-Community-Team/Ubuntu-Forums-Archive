---
title: "bitstream vera sans mono gone in 9.10"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by clementmunns on 2010-02-02
Just went from 9.04 to 9.10 and did all the ttf bit, but alas my favorite font has been disappeared. Any help would be appreciated.

---

### Post by khughitt on 2010-02-15
*bump*

Anyone know what happened?

---

### Post by iKevin on 2010-02-20
I am also interested in this font.  Can I manually download it?

---

### Post by Jacob001 on 2010-02-21
I had the same problem, after upgrading to 9.10 Xubuntu this beautiful font was gone ... a real pain in the butt ! :cry:
Since this is my favourite XEmacs font.
 
It took me quite some time to fix it in xemacs, maybe it's useful for someone else, so here it goes :
 
download the Bitstream Vera Sans Mono from [www.gnome.org/fonts]("http://www.gnome.org/fonts")
put them in ~/.fonts
// scan the font directories on the system and build font cache files
fc-cache -f
// check if ok
fc-list | grep Bitstream
cd ~/.fonts
// for every font file found create X11 XLFD-name and add to fonts.scale
mkfontscale
// read the font files in the directory, convert names to lower case and add names to file
// "fonts.dir" in the directory
mkfontdir
// add this dir to the FONT path
xset fp+ ~/.fonts
// can check with
xset -q
 
// now to add dir to the fontpath permanently (e.g. after reboot) : add it
// to /etc/X11/xorg.conf as :
Section "Files"
FontPath "/home/???/.fonts"
EndSection

---

### Post by pebo on 2010-02-21
ttf-dejavu: font family based on the Bitstream Vera Fonts with a wider range of characters

dejavu-sans-mono is a drop-in replacement

---

