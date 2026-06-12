---
title: "gdm don't recognize .svg in human theme - upgr. to 7.10"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by totmaga on 2007-10-27
Hello!

Ubuntu doesn't show me the login(splash?) screen. It shows instead:

"There was an error loading the theme Human
Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/bottom_bar.svg"

(I can only see the half of the background)
If I click Ok, it shows up again and I can't go further. 


I tried the followings, none of them worked:
- Reinstalled the libsvg1 package with apt-get.
- Installed instead of that the debian package (libsvg1 0.1.4-2)
- Compiled the source.

Thanks - M

---

### Post by supremum on 2007-12-09
i have the same problem
"There was an error loading the theme Human
Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/bottom_bar.svg"
i try to open then an svg file with image viewer and says "Unrecognized image file format"

---

### Post by dgm on 2007-12-30
bumpity bump!

I have this problem as well... anyone have any advice?

---

### Post by dgm on 2007-12-30
Hm. I'm beginning to think that this is because a bunch of packages were removed when I upgraded from Feisty to Gutsy.

During the upgrade, there was a little window that popped up, I can't remember what it said, but it told me to click "OK" and remove a bunch of packages. So I did. A bunch of them were image libraries.

Anyone know how to try and get them back, and see if this resolves the problem?

---

### Post by snblitz on 2008-03-16
I installed from the 7.10 CD and everything was fine for about a month.

Now I am running into this exact problem.

I re-installed everything even remotely associated with gdm, svg, and themes,
and I still get the problem in the login screen.

I switched login themes and the problem in gdm remains.

Another oddity is that System->Preferences->Appearances only displays a single 
theme called 'Custom' no matter how much installation of additional themes I do.

---

### Post by jvanvolk on 2008-03-20
I am having this problem too.  I did not upgrade to 7.10. I installed it from scratch.  However I was trying to install twitux (a gnome twitter application)  It required glib 2.15 and 2.14 is what was installed on my system.  It also required that I upgrade to gtk+-2.12 (gtk+2.12.9) It seemed after I upgraded  to the latest glib when things started to go wrong.  I have the same problem as everyone else in this thread.  I get the same error on boot.  The ubuntu log in screen doesn't show.  Once I am logged in, all of my windows have that default gnome gray look with blue title bars, rather then the nice soothing ubuntu orange.  :)   I only have the Custom theme available in the 'Appearance ' theme manager and I am unable to change any of its setting and have them stick.  I am not even able to modify the colors at all.  I tried to navigate to the Human Theme and install it, but I get the message "The file format is invalid."

Like the other people in this thread, i tired uninstalling and reinstalling everything.  I took all the themes, graphics, libraries, down to the bare bones, and reinstalled everything, but no luck.

Anyone know how to fix this?  

Thanks,
Jared

---

### Post by andrevanzuydam on 2008-04-17
Hi Everyone

The default packages of librsvg didn't seem to work for me after I compiled a new version of GTK into my system.

I think this relates to a problem with the version of the gnome library that reads the svg files. 

**Solution:** compile and install the **latest** librsvg library.  

[URL="http://ftp.gnome.org/pub/GNOME/sources/librsvg"]
http://ftp.gnome.org/pub/GNOME/sources/librsvg[/URL]

Get the latest version of librsvg from the link above and default .configure, make & make install.

After make install - press Ctrl+Alt+Backspace to restart X and you should have no errors!

---

### Post by amdturion on 2008-07-13
Hello, I am an openSUSE user, running version 10.3, by the way I suffered the same problem here.

After many attempts I found a simple workaround by modifying the file:
/usr/share/gdm/themes/GDM-SuSE/suse.xml, replacing the images extensions *.svg with *.jpeg and *.png, in this order:

original file:
[COLOR="DimGray"]<normal file="Background.svg" alpha="1"/>
<normal file="suse.svg" alpha="1"/>[/COLOR]

modified file:
[COLOR="Blue"]<normal file="Background.jpeg" alpha="1"/>
<normal file="suse.png" alpha="1"/>[/COLOR]
By the way, I would like to understand where exactly the problem causing this issue is hidden.

Regards,
amdturion

---

