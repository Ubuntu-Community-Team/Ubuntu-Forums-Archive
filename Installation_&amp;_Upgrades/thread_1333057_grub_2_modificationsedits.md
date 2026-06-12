---
title: "grub 2 modifications/edits"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2009-11-21
i was able to make some customizations to grub 2 following the info in these links:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html](http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html)

i have so far added a splash screen image, changed the text colors and removed unneeded grub entries from the menu.

however, the screen resolution is a bit of a problem to configure for me. my laptop's native res is 1920x1200. i hit 'c' when at the grub menu and typed vbeinfo and got a listing of resolutions. the last ones listed were 1920x1200. when i change the config file entry 

```
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi
```  

to

```
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=1920x1200 ; fi

```

update grub, make sure the splash image i'm using is a 1920x1200 .tga and restart, i only see the upper left portion of the image in the grub screen.

when i did a vbeinfo i think the vbemode that was set was 0x101 (640x480), but the mode i want for 1920x1200 is 0x17c or 0x17d.

how do i change the vbemode ?

---

### Post by zero7404 on 2009-11-21
anyone ?

---

### Post by drs305 on 2009-11-21
It looks like you were trying to change the 00_header file. This graphic mode setting is normally used as a backup in case the setting in /etc/default/grub isn't specified.

Generally you just change the GRUB 2 resolution in the /etc/default/grub file by uncommenting the GFX line:
> 
#GRUB_GFXMODE=640x480


In your case, probably
> 
GRUB_GFXMODE=1920x1200


Don't forget to run "sudo update-grub" to activate the changes.

---

### Post by zero7404 on 2009-11-21
> **drs305 said:**
> It looks like you were trying to change the 00_header file. This graphic mode setting is normally used as a backup in case the setting in /etc/default/grub isn't specified.

Generally you just change the GRUB 2 resolution in the /etc/default/grub file by uncommenting the GFX line:


In your case, probably


Don't forget to run "sudo update-grub" to activate the changes.

hey drs305....

yeah, i made that change, after restarting i saw it didn't work, typed 'c' in grub, then vbeinfo showed that the mode was 0x101. so if vbeinfo lists a resolution that means it's supported, correct ? i will try it again, maybe i did something wrong.

---

### Post by drs305 on 2009-11-21
Yes, vbeinfo should show supported modes. 

You might try making the format:
1920x1200x16, 1920x1200x32, etc and see if that changes anything.

You might also try changing resolutions to/from Packed/Direct modes to see if that makes it work.

Are the fonts changing sizes? That would indicate the settings are taking effect, and perhaps the problem is with your splash image.

---

### Post by zero7404 on 2009-11-21
> **drs305 said:**
> Yes, vbeinfo should show supported modes. 

You might try making the format:
1920x1200x16, 1920x1200x32, etc and see if that changes anything.

You might also try changing resolutions to/from Packed/Direct modes to see if that makes it work.

Are the fonts changing sizes? That would indicate the settings are taking effect, and perhaps the problem is with your splash image.

i'll try this out and see. the fonts are not changing size...

how do i change from Packed to Direct ?

---

### Post by drs305 on 2009-11-21
> **zero7404 said:**
> How do i change from Packed to Direct ?

They are just listed in a column in the vbeinfo returns. IIRC when G2 was in the early beta testing I tried a few of the vbeinfo returns and they didn't work. There were several options for each resolution, including bit depth (the third number). Then I noticed the ones that weren't working on my computer were the 'Packed' entries, so I selected ones that weren't listed that way.

It's something to try.

Did you go back and change 00_header back to its defaults?

---

### Post by zero7404 on 2009-11-21
> **drs305 said:**
> They are just listed in a column in the vbeinfo returns. IIRC when G2 was in the early beta testing I tried a few of the vbeinfo returns and they didn't work. There were several options for each resolution, including bit depth (the third number). Then I noticed the ones that weren't working on my computer were the 'Packed' entries, so I selected ones that weren't listed that way.

It's something to try.

Did you go back and change 00_header back to its defaults?

i don't think i messed with this, don't know what you're referring to with regard to the 00_header....

i changed /etc/default/grub (the file that contains this resolution setting)

---

### Post by drs305 on 2009-11-21
> **zero7404 said:**
> i don't think i messed with this, don't know what you're referring to with regard to the 00_header....

I was referring to this line from the first post:
> 
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi
 

This is the same line found in /etc/grub.d/00_header. It is there in case GRUB_GFXMODE isn't defined in /etc/default/grub.

---

### Post by zero7404 on 2009-11-21
ok....yeah that is the line i made changes to. i updated the file once again to include the third x32 definition, restarted into grub, but it still displays 640x480 image as well as text.

the there appear to be more colors than the 8 or 16 color definition, and the image looks pretty good, considering it's grub and not a fully loaded OS.

i can settle with that for now, i'll mess with grub2 later on as it matures from 1.97 to 2.0.

thanks for the chime in drs305....

---

