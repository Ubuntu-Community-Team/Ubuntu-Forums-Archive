---
title: "Emacs font problem after dist-upgrade to edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Dybber on 2006-10-26
Hi

I just upgraded to Edgy (using [this guide]("https://help.ubuntu.com/community/EdgyUpgrades")). That caused several problems. The biggest is that the default font in Emacs isn't working any more. It displays a square instead of all characters.

Another problem (which I have solved) was that I couldn't chose other window managers than Gnome, from the login screen. (I just needed to create new /usr/share/xsession/xxxxxx.desktop files for the other window managers)

---

### Post by youbaji on 2006-10-26
Probaly that's because of missing fonts.  Nearly all of the fonts files had been move from "/usr/share/X11/fonts/..." to "/usr/share/fonts/X11/..."

Check your directories to see if fonts files really located there.  You may need to update your xorg.conf file.  Then, restart X.

---

### Post by Dybber on 2006-10-26
I just tried that, but it didnt help, but it looks like it works for other people: [https://launchpad.net/distros/ubuntu/+source/xfontsel/+bug/57803](https://launchpad.net/distros/ubuntu/+source/xfontsel/+bug/57803)

---

### Post by Dybber on 2006-10-26
The font i want to use is -urw-nimbus mono l-regular-r-normal--17-120-100-100-p-0-iso8859-15 and bitstream vera fonts isn't available either. (but they are installed)

---

### Post by kroenecker on 2006-11-01
Editing xorg.conf fixed it for me :)

---

### Post by ulugeyik on 2006-11-06
editing xorg.conf and restarting X worked for me too.

Indeed this is bit annoying that the upgrade did not take care of that.

---

### Post by smuglr on 2006-11-16
I had similar problem from clean install, solved by installing xfs and xfstt.

Dougie

---

### Post by flemmingbjerke on 2006-11-18
Neither fixing xorg nor installing xfs and xfstt helped for me.

---

### Post by melgrim on 2006-11-19
It seams that I'm with the same problem...

None of the solution suggested worked for me.

---

### Post by bhaskar on 2006-12-02
Same problem after dapper to edgy upgrade.  xorg.conf points correctly, made sure xfs and xfstt were installed, but emacs has ugly fonts and xemacs crashes without leaving a core file.

---

### Post by izm81 on 2006-12-04
updating xorg.conf and restarting X worked for me.  yay!  :)

---

### Post by theccr2 on 2006-12-05
May I ask what people edited in their xorg files to get it to work?

---

### Post by izm81 on 2006-12-05
Youbaji mentioned it in the second comment.

In the Files section, you'll be changing the FontPath values.  For example, for me, one was

```
  FontPath "/usr/share/fonts/X11/misc"
```

and now it's
  
```
  FontPath "/usr/share/X11/fonts/misc"
```

basically, just switch the "X11" and "fonts".

Then restart X.  Logging out should do this.  ctrl+alt+backspace will do it immediately (save ur work!).

HTH

---

### Post by mtierney on 2007-01-14
It seems that I am in the same boat as a lot of people: neither fixing the xorg.conf file or installing xfs* packages helps me. If it helps at all, I'm using a ThinkPad T60 with ATI x1400. 

Thanks for any advice you might have :-)

---

### Post by TheClayman on 2007-02-18
Hi !


I was facing the same problem and solved it now. Even after fixing my xorg.conf emacs still displayed rectangles instead of characters. After doing a
   ```
sudo aptitude install xfonts-100dpi
```

and restarting the X-Server via Strg-Alt-Del emacs displayed the fonts correctly.

By the way: after installing the fonts, xmms' playlist was not legible anymore. Via Preferences->Font I selected a new font. Typing
  ```
xlsfonts | less
```
at the shell gives a list of possible entries (e.g. -adobe-helvetica-medium-r-normal--14-120-100-100-p-88-iso8859-1)

HTH
  TheClayman

---

### Post by benny_blanco on 2007-02-21
Hi,

I have the same problem (emacs has ugly font, but not rectangles) after upgrade to edgy. 
Editing xorg.conf didn't solve the problem (I had a black screen after gdm restart)
I checked the paths /usr/share/X11/fonts/ and /usr/share/fonts/X11/. They both exist on my machine and they both contain fonts:

vincent@whereismymind:~$ ls /usr/share/X11/fonts/
100dpi  75dpi  fonts.cache-1  misc  Type1
vincent@whereismymind:~$ ls /usr/share/fonts/X11/
100dpi  75dpi  encodings  fonts.cache-1  misc  Type1  util

If I go a bit deeper: 

vincent@whereismymind:~$ ls /usr/share/X11/fonts/Type1/
encodings.dir  fonts.alias  fonts.cache-1  fonts.dir  fonts.scale
vincent@whereismymind:~$ ls /usr/share/fonts/X11/Type1/
a010013l.pfb  c0583bt_.afm  c0648bt_.afm   n019023l.pfb  n022023l.pfb
a010015l.pfb  c0583bt_.pfb  c0648bt_.pfb   n019024l.pfb  n022024l.pfb
a010033l.pfb  c059013l.pfb  c0649bt_.afm   n019043l.pfb  p052003l.pfb
a010035l.pfb  c059016l.pfb  c0649bt_.pfb   n019044l.pfb  p052004l.pfb
b018012l.pfb  c059033l.pfb  d050000l.pfb   n019063l.pfb  p052023l.pfb
b018015l.pfb  c059036l.pfb  encodings.dir  n019064l.pfb  p052024l.pfb
b018032l.pfb  c0611bt_.afm  fonts.alias    n021003l.pfb  s050000l.pfb
b018035l.pfb  c0611bt_.pfb  fonts.cache-1  n021004l.pfb  z003034l.pfb
c0419bt_.afm  c0632bt_.afm  fonts.dir      n021023l.pfb
c0419bt_.pfb  c0632bt_.pfb  fonts.scale    n021024l.pfb
c0582bt_.afm  c0633bt_.afm  n019003l.pfb   n022003l.pfb
c0582bt_.pfb  c0633bt_.pfb  n019004l.pfb   n022004l.pfb


Indeed there seems to be more information in /usr/share/X11/fonts/ than in /usr/share/fonts/X11/ but changing this in xorg.conf does not solve my problem. 
Someone has an idea ?

Thanks !

---

### Post by benny_blanco on 2007-02-21
ok, I just solved the problem, using the previous trick of changing "X11/fonts" into "fonts/X11" in xorg.conf
I must have done a mistake the first time. (the only difference this time is that I used ctrl+alt+backspace instead of gdm restart, but I don't think that makes a difference)

---

### Post by gcordoba on 2007-02-23
I got the same problem. However after the edgy update I found to xorg.conf files:
/etc/X11/xorg.conf and /usr/share/xresprobe/xorg.conf
Please, on which one I need to do the change?
Best regards,
Gustavo

---

### Post by gcordoba on 2007-02-23
Bad news for me...
         FontPath        "/usr/share/X11/fonts/misc"
is ok in both the files.

Any other option to fix the problem?
Gustavo

---

### Post by gcordoba on 2007-02-23
Maybe this output could help:
:
 gcordoba@xterm2:~$ xemacs
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font

Fatal error (11).
...
Segmentation fault (core dumped)
gcordoba@xterm2:~$

no core found by 
gcordoba@xterm2:~$ gdb /usr/bin/xemacs core
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

/home/gcordoba/core: No such file or directory.
(gdb) quit
gcordoba@xterm2:~$

---

### Post by Anicka on 2007-02-27
Please, read the previous posts again.

In your "/etc/X11/xorg.conf" it should say: FontPath "/usr/share/fonts/X11/misc"

Change it for all fonts and it should work.

---

### Post by gcordoba on 2007-02-27
Fixed!, 
however as a price I got a very ugly pink frame for the terminals and any window.
To fix this maybe a little change should be done. Any idea?
Gustavo

---

