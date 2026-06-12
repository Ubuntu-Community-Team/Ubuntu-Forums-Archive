---
title: "Xvnc 'Could not open default font 'fixed'' problem..."
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by scho on 2006-12-07
I upgraded my OS to Edgy. But I could make the vncserver working. When I excuted vnc4server, I had 'Could not open default font 'fixed'' error message in the log file.

So I tried one following way which is suggested somewhere around,

Xvnc4 :1 -fp /usr/share/X11/fonts/misc/

But I got still same error message so I checked the font directory and I could see 'fixed' font list in the fonts.alis
file.

What should I do to solve this problem....

---

### Post by rappazzo on 2006-12-09
I also have a similar problem.  I was running xrdp (xrdp.sourceforge.net), which uses Xvnc, in dapper.  When I upgraded (foolishly, I guess), I get the font issues.  I am not sure where Xvnc is looking for fonts, I have tried various ways to fix it, with configs and making links, but none of those methods have worked.

So, if anyone else can fix this problem, I would appreciate it too.

---

### Post by gr3p on 2006-12-24
me too having a similar problem in starting vncserver on edgy.

this worked fine for me:

[http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)

---

### Post by nameuser909 on 2007-06-19
(this post got a bit long but i've tried to keep it simple and not complicated)

i tried installing vnc4server on kubutun 6.10 but I was having the same fonts problem, if i ran 
vnc4server :1

if you look in your 

home folder/.vnc/*.log 

you see the line with the default font fixed not found.

well i had a look at the vnc4server script by running:
less `which vnc4server`
and you see the lines (a couple of pages down):

# Add font path and color database stuff here, e.g.:
#
#$cmd .= " -fp /usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/75dpi/";
# $cmd .= " -co /usr/lib/X11/rgb";
#

so i changed it to the lines below (using vim but you could use Kate or something as well):
# Add font path and color database stuff here, e.g.:
#
$cmd .= " -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/100dpi/";
#$cmd .= " -fp /usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/75dpi/";
# $cmd .= " -co /usr/lib/X11/rgb";
#


so now the error is gone and vnc starts up! I made one other change. I don't think twm was installed on the system so I installed the wm2 package, and changed the file

home folder/.vnc/xstartup

and commented out the xsetroot line (which is why you get a gray screen if thats whats happening to you)
and change the line that says twm with wm2

jobs a good'n

the next problem i had was the iptables firewall! i installed the firestarter package and ran it from a terminal  (the run dialog would do as well i think) using 
gksu firestarter &
then i tried to connect from my host, which brought up an event in the firestarter interface saying that i was trying to hack in, so i right clicked on that event, and asked it to allow the service for that host, sorted!

i'm not running it from xinetd yet so i still need to run the vnc4server command on the computer (i do it over ssh when i need it ) but i might try that next

have fun!

---

### Post by fatmano on 2007-11-06
I just upgraded to Kubuntu Gutsy and had this problem.  All I did was create some 
symlinks.  It seems that vncserver wants to find the fonts in /usr/X11R6/lib/fonts but they now live in /usr/share/fonts/X11.  So simply :

cd /usr/X11R6/lib/X11/fonts
ls /usr/share/fonts/X11
and link all the directories there that are not listed in /usr/X11R6/lib/X11/fonts.  For me that was:

sudo ln -s /usr/share/fonts/X11/100dpi 100dpi
sudo ln -s /usr/share/fonts/X11/75dpi 75dpi
sudo ln -s /usr/share/fonts/X11/misc misc
sudo ln -s /usr/share/fonts/X11/Type1 Type1
sudo ln -s /usr/share/fonts/X11/util


Fired up vncserver :1 and all was well w/ the world :D

HTH

---

### Post by Chuk on 2007-12-19
> **fatmano said:**
> I just upgraded to Kubuntu Gutsy and had this problem.  All I did was create some 
symlinks.  It seems that vncserver wants to find the fonts in /usr/X11R6/lib/fonts but they now live in /usr/share/fonts/X11.  So simply :

Fired up vncserver :1 and all was well w/ the world :D

HTH

Thanks, I had a similar problem and thanks to you, fixed it.

---

### Post by rshields on 2008-02-01
I can confirm that this is still a problem on Gutsy when installing the vncserver package.

> **fatmano said:**
> I just upgraded to Kubuntu Gutsy and had this problem.  All I did was create some 
symlinks.  It seems that vncserver wants to find the fonts in /usr/X11R6/lib/fonts but they now live in /usr/share/fonts/X11.  So simply :


That didn't work for me. I fixed it by editing /usr/bin/vncserver and changing

```

if (!$fontPath) {
  $fontPath = "/usr/X11R6/lib/X11/fonts/Type1/,".
              "/usr/X11R6/lib/X11/fonts/Speedo/,".
              "/usr/X11R6/lib/X11/fonts/misc/,".
              "/usr/X11R6/lib/X11/fonts/75dpi/,".
              "/usr/X11R6/lib/X11/fonts/100dpi/,".
              "/usr/share/X11/fonts/misc/,".
             "/usr/share/X11/fonts/Type1/,".
              "/usr/share/X11/fonts/75dpi/,".
              "/usr/share/X11/fonts/100dpi/".
              "/usr/share/fonts/X11/misc/,".
             "/usr/share/fonts/X11/Type1/,".
              "/usr/share/fonts/X11/75dpi/,".
              "/usr/share/fonts/X11/100dpi/"
}

```

to

```

if (!$fontPath) {
  $fontPath = "/usr/share/fonts/X11/misc/,".
              "/usr/share/fonts/X11/Type1/,".
              "/usr/share/fonts/X11/75dpi/,".
              "/usr/share/fonts/X11/100dpi/"
}

```

[quote=http://www.fifi.org/doc/vnc-common/faq.html]
The VNC server can also get upset if you have directories on your font path which don't actually exist on your system.
[/quote]

:)

Hope this helps.

---

### Post by rshields on 2008-04-19
I found that it stopped working with the same error, possibly following an update (am using Gutsy), and I also had to comment out the following code:

```

if (!$fontPath) {
  &ReadXFConfigFont;
}

```

---

### Post by bigdawgte on 2008-07-09
rshields:

I have this problem as well and the earlier fix didn't work (Gutsy).  But you say "I fixed it by editing /usr/bin/vncserver..."  Are you sure you mean vncserver?  I don't have that file in that location.  I think I have a symlink to an executable called "vncviewer."

---

