---
title: "Fonts - changed with Edgy?  Old ones back?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by tinker123 on 2006-10-30
Hi;

I recently upgraded to edgy from dapper.  It seems everywhere I go in my desktop now I have ttf fonts.  This usually looks lousy in linux, but I have to admit it looks good.

My problem is their one place where it does not look good and that is in my editor ( commercial linux app ) Visual Slick Edit.

I'm guessing there is a default font directory that was changed in the upgrade process.  

Does anyone know what that directory is so I can find some way to point my app to it?

Thanks

---

### Post by dr.drake on 2006-10-31
ehrm, there are a couple of threads about fonts in edgy firefox, but I just downgraded firefox to version 1.5 and the fonts are still acting weird, so I guess it must be edgy related, not with firefox2.0, that's why I add to this thread..

sometimes while browsing fonts show up as **transparant with a white outline**. it is easiest to reproduce when I google (this forum) and then select the "in cache" option. when I then click "show current page without highlights, it becomes normal again..
but it also sometimes happens in normal webpages, some fonts look like that, some look normal.

what could be the cause of this, might it be related to the oOo problem?

*edit: I just checked, but open office seems to be working fine on my side..

---

### Post by Footer on 2006-11-01
I'd like to add my .02 to this thread.  The fonts in OO look absolutely horrible and I can't figure out how to fix.  And from the searching I've done on this forum and elsewhere, there currently isn't a fix.  Here's a couple of threads with more details:

[http://www.ubuntuforums.org/showthread.php?t=286178](http://www.ubuntuforums.org/showthread.php?t=286178)

[http://kubuntuforums.net/forums/index.php?topic=10385.0](http://kubuntuforums.net/forums/index.php?topic=10385.0)

The second link has some good screen shots.

Thanks!

---

### Post by bluenova on 2006-11-01
And have the fonts changed for CLI (i.e CNTL + ALT + F1) or is it just me?

---

### Post by Footer on 2006-11-01
And it seems that font issues run far deeper than just OO, CLI, FF, etc. in Edgy.  Look at this thread:

[http://www.ubuntuforums.org/showthread.php?t=286361](http://www.ubuntuforums.org/showthread.php?t=286361)

Yet another problem associated with Edgy fonts???

We need some **ANSWERS**!

:evil:

---

### Post by dr.drake on 2006-11-01
could it have something to do with the xorg.conf ???

in dapper I had more lines about fonts then in edgy:

[QUOTE=xorg_Dapper]

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection[/QUOTE]

[QUOTE=xorg_Edgy]

Section "Files"
	# path to defoma fonts
    FontPath 	"/usr/share/fonts/X11/misc"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/usr/local/share/fonts"
EndSection[/QUOTE]

---

### Post by Footer on 2006-11-01
I wish I could say the same for my xorg.conf.  Mine look nearly identical.

Dapper:

```
Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

Edgy:

```
Section "Files"

  # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

I wonder what else it could be?

---

### Post by Footer on 2006-11-01
Hey, hey, whaddya know ... You were definitely on the right track dr.drake.  Although my xorg.conf files were nearly the same between the versions, something changed ... and I got clued in to it when I saw this line in the Edgy xorg.conf:

```
FontPath        "/usr/share/fonts/X11/misc"
```

Notice how the fonts/X11 are reversed in all the other lines?  Well, I just made all the other lines fonts/X11, like this:

```
Section "Files"

  # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

and WALA! vncviewer now works!!!

I'M SO HAPPY!!!  Thanks a bunch dr.drake!!!

:D :D :D

---

### Post by bluenova on 2006-11-02
Oh I'll try changing mine tonight, as I'm using the same xorg.conf that I had with Dapper due to extra setting such as twinview.

---

### Post by dr.drake on 2006-11-02
oh no!!!!!!

so I thought we really had it nailed there, but it doesn't work for me.. :(

it must be something with that font path in xorg.conf though...

tomorow I'll have some time to dig a little deeper

---

### Post by Footer on 2006-11-02
It didn't work for you???  What the??????

Are you sure you switched those two around (X11/fonts to fonts/X11)?  And you did restart your xserver right???

It worked like a charm for me ... Hope you get it figured out!!!

:)

---

### Post by dr.drake on 2006-11-02
yes I did..

I also did a search for folders named "fonts", and I found a fonts folder within the firefox folder with a dozen config files in them.
I'm going to try and read through them tomorrow, maybe that there's something there?

---

### Post by tinker123 on 2006-11-03
Yep, switching the font paths to be /fonts/X11 rather than /X11/fonts in worked for me too!

For the sake of archive searchers you can find xorg.conf in Ubuntu at
/etc/X11

You can edit it by become root, which you can do with:
sudo bash

Good Luck!

---

### Post by rjz35 on 2006-11-15
worked for me thanks

---

