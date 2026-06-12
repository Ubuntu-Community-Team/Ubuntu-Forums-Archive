---
title: "dual screen on intel 965 - xrandr"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by WardLoockx on 2008-01-07
I'm trying to install my dual screen using xrandr but each time it fails. No changes. Framebuffer ? don't know ?

Here is some more info
[PHP]
xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA disconnected (normal left inverted right)
LVDS connected 1680x1050+0+0 (normal left inverted right) 331mm x 207mm
   1680x1050      60.0*+
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TMDS-1 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9
   1152x864       74.8
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
TV disconnected (normal left inverted right)
ward@ward-laptop:~$ xrandr --output LVDS --left-of TMDS-1
xrandr: screen cannot be larger than 1680x1680 (desired size 2960x1050)
[/PHP]

But no dual screen :( only clone. 

Thanks !
Ward

---

### Post by WardLoockx on 2008-01-07
Looks like I had to adjust my buffer using this in my xorg.conf

Virtual 2624 1200

found the info @ [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

---

### Post by amaragon on 2008-01-09
I believe you cannot have the OpenGL functionality with a virtual desktop of that size. The maximum allowed for the virtual desktop to have OpenGL is 2048x2048.

I have that problem now, I have two screens, the VGA to the right of my laptop. The laptop runs at 1280x768 and the VGA at 1440x900. Now, when you sum up both in the x direction, the sum is above 2048. Therefore, even though I modified the xorg.conf file to have the entire space that I need, the compiz functionality is lost.

Did you solve this issue?

a²

---

### Post by srankin1826 on 2008-02-07
You can till use compiz.  Sort of.  What you need to do is edit /usr/bin/compiz to get rid of the startup check that the screen size is less than 2048x2048.  Compiz may not reliably render stuff outside of 2048x2048, but at least you can start it up and play around.  It didn't look to bad for me with a 1280x1024 on top of 1400x1050 (2680x2074).

In the section:  

check_texture_size()

change:                
                verbose "Failed.\n"
                return 1;

to:

                verbose "Failed.\n"
                return 0;

cheers,

Sam

btw:  extreme newbie here, your mileage may vary.

---

### Post by ullix on 2008-02-12
It does seem to me that the 2048x2048 limit for the virtual screens was overcome with the Intel 965 chipsets ([http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2"))

If someone has evidence that this is still a limit, please provide data or post a reference

I am running Kubuntu Gutsy on an Acer Extensa 5220 laptop (using Intel 965GM chipset) and dual screens work, but need a lot of manual fiddling with xrandr. I need advice how to get TV working from the S-video connector. Anyone has experience?

---

### Post by john.ennew on 2008-04-13
I've been struggling with xrandr and TV out on an Intel GM965 chipset system.

On boot the TV out sometimes works and sometimes doesn't. Xrandr always reports that it is working though.  I was wondering if anyone has had any better experiences?

Interestingly, if I suspend the system to S3 when the TV out is not working then wake it up again, the TV out always works on resume.  However, because of a separate bug with the Intel HD audio driver, the sound then stops working.

I've posted a bug report to this bug:
[https://bugs.launchpad.net/bugs/6270](https://bugs.launchpad.net/bugs/6270)

---

