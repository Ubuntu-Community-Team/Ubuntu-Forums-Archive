---
title: "Solid purple background - where does it live?"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-03-17
I installed the beta1 test ISO and included in the wallpaper in System>Preferences>Appearance is the same background as the default plymouth.  It is not in /usr/share/backgrounds.

It is not in my other installs so it must be a new thing but I can't find it.  It looks better than the default grape juice and cottage cheese vomit default wallpaper.

I would also like to know if anyone has been able to replace it in plymouth.

---

### Post by jesterthejedi on 2010-03-17
Its called warty-final-ubuntu.png, and its located in /usr/share/backgrounds/

---

### Post by ranch hand on 2010-03-17
> **jesterthejedi said:**
> Its called warty-final-ubuntu.png, and its located in /usr/share/backgrounds/
Nope, that is the ghastly purple one that the gdm uses and the default wallpaper.  This is the solid purple used by plymouth.

It really is a lot nicer, in my eyes anyway than the one you are referring to.

In most of my installs I have the grub menu background, the gdm and the waooper matching.

I used to be able to do the same with plymouth but it is not working well with the newer versions because of the animated dots (I think).

I was assuming that the solid purple was generated in the plymouth theme script but it must also exist somewhere else if it is available in for wallpaper too.

Where in flideration is it?  Or is it generated somehow from the plymouth script?  It seems there would have to be another script in /usr/share/backgrounds (like the one for cosmos) to generate the wallpaper.

This is a silly thing to do for a wallpaper so I figure it is somewhere else.

I looked in /usr/share/images where the old xslpash folder still is (gdm used the bg_2560x1600.jpg file from there for a long time).  In that same directory is desktop-base which is thee default for the grub background image.  I thought maybe there.  Nope it is empty (currently).

The bugger has to be somewhere.

---

### Post by psyke83 on 2010-03-17
(Note: I haven't tried the beta testing ISOs)
Go to System -> Preferences -> Appearance, Background tab.

I bet that you're looking for the first item called "No Desktop Background", which instead lets you specify a colour (default is probably #2C001E) and fill type (default is solid, can also fill as a horizontal or vertical gradient).

If you really want it as a wallpaper, create it to the desired specifications in GIMP ;).

---

### Post by ranch hand on 2010-03-17
> **psyke83 said:**
> (Note: I haven't tried the beta testing ISOs)
Go to System -> Preferences -> Appearance, Background tab.

I bet that you're looking for the first item called "No Desktop Background", which instead lets you specify a colour (default is probably #2C001E) and fill type (default is solid, can also fill as a horizontal or vertical gradient).

If you really want it as a wallpaper, create it to the desired specifications in GIMP ;).
I will admit that in my other installs there is, what I thought was, a plain black background.  In this beta1 it is solid purple.

I am not over in testing land right now, on 9.04 and headed to bed, but how do you do this?  I did change to the solid black on one of the other installs.  I did not see a way to change it (I wasn't looking for one either).  I just assumed it was black as a holding device for the purple one.

That purple or black or changable one has to live somewhere too.  It is not in /usr/share/backgrounds.  Just bugging me to death.

Says a lot for the stability of 10.04 that we are worrying about this kind of thing instead of "how the devil do I get this to boot, haven't had it up for 10 days" like last time around now.

Edit
It really is purple in the beta.  It is as you say the first one in the wallpaper offerings, as is the black one.  I will look at it again in the morning.

---

### Post by MacUntu on 2010-03-17
_deleted_

---

### Post by elespejo on 2010-03-20
Bump.

I managed to customize everything including login screen to my taste  (don't really like the new purplish/reddish default theme) but ain't got a clue how to change the purple background.

---

### Post by ranch hand on 2010-03-20
Thank you elespejo.  I thought maybe i was just being stupid.

The grape juice and cottage cheese vomit login screen is pretty bad.  It is nice to get rid of.  Feels better.

---

### Post by ankspo71 on 2010-03-20
I think I might have found it. It looks like the background in plymouth is a script.
Look in /lib/plymouth/themes/script/script.script .

It looks like there are other themes to choose from too.
 /lib/plymouth/themes


```
sudo updatedb
locate plymouth
```found these files too.
/usr/bin/plymouth-log-viewer
/usr/sbin/plymouth-set-default-theme
/var/lib/plymouth/boot-duration

---

### Post by MacUntu on 2010-03-20
If you mean plymouth's text plugin (**text logo** "Ubuntu 10.04" plus dots), you need to recompile plymouth (change 'PLY_TERMINAL_COLOR_BLACK' from '0x2c001e' to '0x000000' in 'src/plugins/splash/text/plugin.c') and replace '/lib/plymouth/text.so' with the one from your build ('debian/plymouth/lib/plymouth/text.so').

---

### Post by elespejo on 2010-03-20
Nope - I want to change the _solid_purple_background_ into another solid color. No clue about how it's generated - my guess is it's somehow automagically generated by a single command, not by using a jpg or something.

---

### Post by MacUntu on 2010-03-20
So you mean the graphical boot theme? Then it's most likely in '/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script'

```
...
Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom
...

```
0.16*256, 0, 0.12*256 (RGB) equals purple.

Don't forget to 'sudo update-initramfs -c -k `uname -r`' after changing the color.

---

### Post by ronacc on 2010-03-20
I just booted the current daily )AMD64 , and it shows a solid purple in appearances , see SS  , or for your DT just use Gimp and make one . I also show a slightly lighter solid purple in my install .

---

### Post by MacUntu on 2010-03-20
Hm, rsyncing the latest i386 daily. *curious*

---

### Post by elespejo on 2010-03-20
Thanks a lot MacUntu! That's what I was looking for - I just couldn't make heads or tails of the numbers. I managed to change the background and seems changing the dots should be easy now.

---

### Post by MacUntu on 2010-03-20
Correcting myself: for RGB component values from 0-255 it's actually /25**5** (*255 respectively) to get the new (old) value. So if you have some blue color like

(60, 123, 234)

the new one is

(60/255, 123/255, 234/255) -> (0.235, 0.482, 0.918****) :D

---

