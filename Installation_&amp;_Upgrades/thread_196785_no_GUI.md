---
title: "no GUI"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Uta on 2006-06-14
I just installed Xubuntu and I see the Ubuntu splash at startup,it loads and then it goes into terminal mode (tty1)? How do I start XFCE? Thanks!
Also at start up it says "unable to locate RSDP" ?

---

### Post by loell on 2006-06-14
try startx

---

### Post by Uta on 2006-06-14
I think something went very wrong with my install. "startx" does not work.
I installed the OEM version, alternative. I thought I would greeted with a xubuntu  screen but it's ubuntu? Doesn't seem right.

---

### Post by loell on 2006-06-14
ah yes, the alternate version.. 
i haven't tried that installer.

btw, how much is your ram? 
can you install via xubuntu livecd instead?

---

### Post by Uta on 2006-06-14
128mb, that's it.
I have several computers running Linux but I just thought I would put some new life into this old laptop. Can you install with only 128mb of ram? Thank you--

---

### Post by scott9027 on 2006-06-14
I don't know about the Xubuntu LiveCD, but the Ubuntu/Kubuntu LiveCD's need 192MB of RAM unfortunately.  You should look for instructions for the alternate installer, because you may have to do some more work yourself, as it's designed for experienced users and developers etc.

---

### Post by laodan on 2006-06-14
I had the same problem yesterday (xserver crash) and solved it following the "how to" in [steliot's sticky post]("http://www.ubuntuforums.org/showthread.php?t=187177")
Good luck.

---

### Post by Uta on 2006-06-14
my xserver did not crash I have no GUI  installed,I need to install that.
I have the alternate CD which I thought would have installed somekind of GUI, but no. So I would like some help installing a GUI from the CD.
Thanks.

---

### Post by sefs on 2006-06-14
I installed (Xubuntu 6.06 Dapper) it on a computer (from 2000) using the text mode installation on the alternate CD, and every thing went rather well as expected.  This seems to be the better way as it requires much less memory than using the desktop CD.  Instead of OEM mode ... try using the Text mode. That mode seems similar to the default mode that was from breezy, Until they switched the names around and called the regular install CD an alternate CD and the LiveCD the Desktop CD.

A pleasent surprise is that the modem even works using gnome-ppp.  of course dial up sucks in this day an age though.

---

### Post by Sutekh on 2006-06-14
[quote=Uta]my xserver did not crash I have no GUI  installed,I need to install that.
I have the alternate CD which I thought would have installed somekind of GUI, but no. So I would like some help installing a GUI from the CD.
Thanks.[/quote]The Alternate CD *will* install the GUI, except you chose an OEM install, which may be the problem.

You can install the Xubuntu dekstop environment using these commands
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
``` Use you login password when prompted.

---

### Post by Uta on 2006-06-15
Thank you for the information, currently it is installing the xubuntu desktop environment. 
I am wondering why though it is installing a lot of fonts, like tamil, punjabi,oriya,malayalam, etc? It is taking forever to "regenerate fonts cache? I only have a 4 GIG HD on this very old laptop and I thought that Xubuntu was suppose to be for small/old laptops, not installing a lot of bloat? Could you help me understand this part of the install process? Again thanks.
OK, I now have a GUI, and my wirelesscard working but the "fonts" don't look right. Do I need to reconfigure xorg?
If so, how do I do that?

---

### Post by Uta on 2006-06-15
OK, lots of things to fix but can't start fix anything because my username is not in the sudoers file? How do I login as root in Xubuntu, my regular password does not work and when I try to sudo passwd root, nothing happens because I don't have sudo for my username. How do I get out of this 'loop'?

Thanks.

---

### Post by loell on 2006-06-15
I still think, that you would be better installing via live cd since 128 mb ram will suffice
and  basing from your last problem of not able to login, reinstalling from scratch will be your best option... thats just my opinion though :)

and oh don't give up on Xubuntu.. its worth it..
nah.. i know you won't ;)

---

### Post by Uta on 2006-06-15
Ok I have fixed the sudo users issue by booting from the live cd, mounting the HD and editing the file "sudoers" and I now can use sudo. My visuals are not right, fonts are not displayed correctly, which I have tried to correct by reconfiguring xserver but my changes having no affect on the font issue. I guess I need to manually edit xorg.conf.
Could someone share their font settings from xorg.conf with me?
My fonts are jagged. Could it be because I selected "bitmap" as one of the display options?
Thanks!

---

### Post by mulperi on 2006-06-15
Here is the fonts part of xorg.conf:
[FONT="Courier New"]	FontPath     "/usr/lib/X11/fonts/misc"
	FontPath     "/usr/lib/X11/fonts/cyrillic"
	FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/Type1"
	FontPath     "/usr/lib/X11/fonts/CID"
	FontPath     "/usr/lib/X11/fonts/100dpi"
	FontPath     "/usr/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"[/FONT]

My X crashed after Dapper upgrade so I had to boot into rescue mode and overwrite xorg.conf file with the original one. Then I downloaded ATI proprietary drivers and reinstalled it. 

Anyway, perhaps these links will help you in your font-problems:
[http://gentoo-wiki.com/index.php?title=HOWTO_Xorg_and_Fonts&printable=yes](http://gentoo-wiki.com/index.php?title=HOWTO_Xorg_and_Fonts&printable=yes)
[http://www.ubuntuforums.org/showthread.php?t=20976](http://www.ubuntuforums.org/showthread.php?t=20976)

Rgds,

---

