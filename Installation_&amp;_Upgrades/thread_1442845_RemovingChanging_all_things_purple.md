---
title: "Removing/Changing all things purple"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Slim Odds on 2010-03-30
Can someone please post directions on how to get completely rid of _everything purple in Lucid_?

The boot screen
The login screen
The default terminal background
The "Click here to hide all windows and show the desktop" button
Anything else that you can think of that's purple.
etc. etc. etc.

Please include a global fix for the WM button fiasco so that I don't have to modified the individual account of newly created users.

Many, many thanks in advance.

P.S. Message to Canonical: I love Ubuntu, but purple themes are for teenage girls.

P.P.S. Does anyone else find it humorous that the "***new***" default purple background file is named "***warty-final-ubuntu.png***"?

---

### Post by peakpc on 2010-04-04
I to think the purple must go: somethings can be accessed changed under system, preferences,appearance,backgrounds (I like the space slides)
system, preferences,appearance,themes (change theme completely or at least customize,icons to gnome)
I have not figure out the boot screens yet, it doesn't seem to be xsplash like in 9.10 (hated the brown stuff even more) but I'm working on it and will post when I find it.

---

### Post by peakpc on 2010-04-04
It would seem that 10.04 is using plymouth to boot I am looking into theming.

---

### Post by peakpc on 2010-04-18
reference this [http://ubuntuforums.org/showthread.php?t=1431739&highlight=purple]("http://ubuntuforums.org/showthread.php?t=1431739&highlight=purple")to change purple in plymouth

---

### Post by arrimapirate on 2010-04-18
I would like to know this as well. My main complain is the gdm screen. I miss the old one from 9.10 as well as the splash that played. The word Ubuntu with blinking lights just doesnt work for me.

---

### Post by peakpc on 2010-10-12
I had to find a way to change the purple and orange stuff at boot up, no offence but I just don't like the combo. Themes are easy enough after logging but, changing the Plymouth boot colors and GDM screens took a little more doing...

Here is what I ended up doing:

For Plymouth, I enter "gksu gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script" in terminal then drill down to "Window.SetBackgroundTopColor" and set all the numbers in that line to zeros like (0.00, 0.00, 0.00) then the next line "Window.SetBackgroundBottomColor" and do the same. save and exit. one the next boot the screen will remain black with the Ubuntu logo and orange dots (not sure yet how to change dot colour but It's not so bad on a black background.

Next is the GDM... I found this youtube video that explains it well.
It goes like this:
At login press control+alt+F1, log in, then type “export DISPLAY:0.0” enter then “sudo -u gdm gnome-control-center” enter then control+alt+F7. Edit as desired then control+alt+F8

I decided to change the background to match my regular one which is the space collection, this way it gives a seamless look. Also I changed the theme to match mine which is a mix of clearlooks and glossy-P.

I am all about choices, Ubuntu is great but it should not have to be so hard to change the look if you want (It use to be much easier before 9.04).

---

### Post by Maxei on 2010-11-09
hey peakpc,

Are you using Compiz and the cube? I have set one different background for each of the four sides of the cube. But always, immediately after login, there is that horrid, fatal, vomiting-inducing purple background, which stays as a layer behind the other images. 

The problem is with the upper and lower panels: if I decrease the opacity of the panels, the purple color layer will show up. This behaviour does not occur if I set only one identical image as background for the four sides of the cube, so making the panels translucent will show correctly the image behind, not that bad purple layer. 

But with 4 images set in the cube, the panels prefer to use the purple color instead of the corresponding background image in each side of the cube.

Can you help? maybe this is a clash between Compiz and the other, what would be, metacity or the gdm, or something else?

---

### Post by babur on 2010-11-09
You can use "Ubuntu Tweak" to custom things.... 
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Maxei on 2010-11-09
> You can use "Ubuntu Tweak" to custom things....
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Please, can you be more specific? the ubuntu tweak is well known, but doesn't do everything. But I could miss something and if so, please kindly indicate where I could get things fixed with ubuntu tweak. 

If you have experienced a similar problem as described and found a fixing, please share it. But if is not your case, it is better not to comment. thanks.

---

### Post by babur on 2010-11-09
Hey maxei,

May be I was not specific.

As you know not everything using Tweak, I was able to change the login screen and logo.  The default terminal background (am using transparent) using the prefrences of the terminal window.

---

### Post by slimteufel on 2011-08-31
> **Slim Odds said:**
> 
The login screen


anyone figure this out?

---

### Post by Slim Odds on 2011-08-31
> **slimteufel said:**
> anyone figure this out?

Try this:
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

Although, I want to find out where it stores the actual image filename.

---

### Post by slimteufel on 2011-09-01
> **Slim Odds said:**
> Try this:
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

Although, I want to find out where it stores the actual image filename.

Nope, still purple.  Probably just going to install debian.

---

### Post by Slim Odds on 2011-09-01
> **slimteufel said:**
> Nope, still purple.  Probably just going to install debian.

Then you didn't follow the instructions....

This alone is all you need:```
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow
```

---

### Post by slimteufel on 2011-09-02
> **Slim Odds said:**
> Then you didn't follow the instructions....


When you remove the background image default, there is a solid color background, which is purple.  These instructions have absolutely nothing to do with changing the color of the background.

---

### Post by Slim Odds on 2011-09-02
> **slimteufel said:**
> When you remove the background image default, there is a solid color background, which is purple.  These instructions have absolutely nothing to do with changing the color of the background.

OK, excuse me... I used a background image and it's much better. No more purple for me.

---

### Post by slimteufel on 2011-09-02
> **Slim Odds said:**
> OK, excuse me... I used a background image and it's much better. No more purple for me.

GAH, thanks anyway!

---

### Post by Slim Odds on 2011-09-02
> **slimteufel said:**
> GAH, thanks anyway!

You know that you could use a blank image of any color that you like, right?

---

### Post by slimteufel on 2011-09-03
> **Slim Odds said:**
> You know that you could use a blank image of any color that you like, right?

Yes, understood.  But I wouldn't learn anything that way.  ;)

---

### Post by slimteufel on 2011-09-03
I feel like I just gave birth... but it could be that I am half drunk.  Anyway, no more purple forcryingoutloud.

Edit the xml in: /var/lib/gconf/debian.defaults

find:  <entry name="primary_color" and change the string value to the color you want
do the same thing with <entry name="secondary_color" just in case ;)

Okay, now to get out of this half-drunk state and go full retard.

---

