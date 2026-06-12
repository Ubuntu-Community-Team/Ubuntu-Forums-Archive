---
title: "firefox has ugly fonts"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hourna on 2010-04-01
as compared with windows version of firefox and other browsers i have tried in lucid (epiphany, google chrome, opera 10.10), firefox shows really ugly fonts. i have sub-pixel smoothing enabled. i will upload screenshots to help comparing. i would like to see your screenshots, if you care.

from a turkish website ( [http://www.eksisozluk.com/](http://www.eksisozluk.com/) ):

firefox:

[IMG]http://i40.tinypic.com/2daxh13.png[/IMG]

chrome:

[IMG]http://i43.tinypic.com/2ntvho9.png[/IMG]

from facebook:

firefox:

[IMG]http://i44.tinypic.com/v5wklu.png[/IMG]

chrome:

[IMG]http://i39.tinypic.com/fuz5e1.png[/IMG]

from ubuntu home page:

firefox:

[IMG]http://i39.tinypic.com/mj88m.png[/IMG]

chrome:

[IMG]http://i39.tinypic.com/2lbnps5.png[/IMG]

from a blogspot post:

firefox:

[IMG]http://i41.tinypic.com/34ex5i1.png[/IMG]

chrome:

[IMG]http://i40.tinypic.com/14ugvol.png[/IMG]



i think the difference is quite obvious. is there any way to fix it?

---

### Post by MCVenom on 2010-04-01
Have you downloaded the MS fonts from the multiverse repository?

If not type this in the terminal and see if the fonts look any better:

```
sudo apt-get install msttcorefonts
```

---

### Post by hourna on 2010-04-01
it says they are already installed.

---

### Post by MCVenom on 2010-04-01
Well then, that can't be it... :|

---

### Post by psyke83 on 2010-04-01
Please use the "search this forum" feature... This topic has at least half a dozen duplicates.

[http://ubuntuforums.org/showpost.php?p=9010164&postcount=10](http://ubuntuforums.org/showpost.php?p=9010164&postcount=10)

---

### Post by Didius Falco on 2010-04-01
Have you tried changing to a different font in Firefox?** Tools>Preferences>Content>Fonts & Colors **

For even finer-grained control, go one more step to **advanced**. I always set it so that websites use my choice of fonts instead of their own...

---

### Post by hourna on 2010-04-01
> **Didius Falco said:**
> Have you tried changing to a different font in Firefox?** Tools>Preferences>Content>Fonts & Colors **

For even finer-grained control, go one more step to **advanced**. I always set it so that websites use my choice of fonts instead of their own...

yes i have set and tried both options. but still they are ugly.

---

### Post by dcstar on 2010-04-01
> **hourna said:**
> yes i have set and tried both options. but still they are ugly.

This PPA has a version of Firefox with the anti-alised fonts option turned on:

[https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)

I found it made a difference on my install.

---

### Post by jaco223 on 2010-04-01
Originally Posted by **lovinglinux**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8704533#post8704533")                 
                 [I]Try this:

     Code:
     gedit ~/.fonts.conf 

then replace the content of that file with this:

     Code:
     <?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig> 

Save it and restart Firefox.[/I]

---

### Post by Kow on 2010-04-02
I believe this a bug milestoned for Beta 2? It's a problem with firefox and cairo and seems to recur almost every dev cycle.

[https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615)
Yep, definitely not a new problem.

---

### Post by jaco223 on 2010-04-02
> **Kow said:**
> I believe this a bug milestoned for Beta 2? It's a problem with firefox and cairo and seems to recur almost every dev cycle.

[https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615](https://bugs.launchpad.net/ubuntu/lucid/+source/firefox/+bug/512615)
Yep, definitely not a new problem.

The problem persists with the chromium browser as well.

---

### Post by Seventh Reign on 2010-04-02
There is absolutely no difference at all between the fonts.  They are 100% identical.

---

### Post by dcstar on 2010-04-02
> **dcstar said:**
> This PPA has a version of Firefox with the anti-alised fonts option turned on:

[https://launchpad.net/~portis25/+archive/test](https://launchpad.net/~portis25/+archive/test)

I found it made a difference on my install.

The "new" official Firefox update is installed on my system today and the fonts revert to the crappy look, so then the new rebuilt package from the PPA above is installed and the fonts are back to normal again.

Learn the lesson people.

---

### Post by jaco223 on 2010-04-04
@Seventh Reign: I beg to differ, but i clearly see blue hinting in chromium. In the screen shot chromium is on the left and firefox on the right. 

Jaco

---

### Post by Kyril on 2010-04-04
Firefox 3.6.3 in Lucid has finally fixed the ugly font issue:

```
* Add a cairo LCD filter to use Freetype LCD colour filtering features,
    based on the same patch applied to our system cairo package. Thanks to
    Marc Deslauriers for helping to make this work. (LP: #512615)
```

---

### Post by tunin on 2010-04-04
> **jaco223 said:**
> @Seventh Reign: I beg to differ, but i clearly see blue hinting in chromium. In the screen shot chromium is on the left and firefox on the right. 

Jaco

You can beg to differ all you want.  I'm with Seventh in seeing no difference at all.

---

### Post by Uncle Spellbinder on 2010-04-04
> **tunin said:**
> You can beg to differ all you want.  I'm with Seventh in seeing no difference at all.
+1

I fail to see any difference whatsoever.

---

### Post by jaco223 on 2010-04-04
> **tunin said:**
> You can beg to differ all you want.  I'm with Seventh in seeing no difference at all.

Perhaps it is my computer. the monitor TFT Active Matrix LCD (1680x1050 native) display.
ATI Radeon HD 2400 XT graphics acceleration with 128 MB of GDDR3 memory.

or maybe I'm just a stickler for font rendering. 

Jaco

---

### Post by Longinus00 on 2010-04-04
> **jaco223 said:**
> Perhaps it is my computer. the monitor TFT Active Matrix LCD (1680x1050 native) display.
ATI Radeon HD 2400 XT graphics acceleration with 128 MB of GDDR3 memory.

or maybe I'm just a stickler for font rendering. 

Jaco

First of all, you shouldn't use a lossy image format to show little details. Second, unless you took that picture with a camera we have no idea how it looks on your lcd screen.

---

### Post by jaco223 on 2010-04-04
> **Longinus00 said:**
> First of all, you shouldn't use a lossy image format to show little details. Second, unless you took that picture with a camera we have no idea how it looks on your lcd screen.

By "lossy" I guess you mean "glossy"? what kind of image should I use?

---

### Post by Rob2687 on 2010-04-04
[Lossy compression]("http://en.wikipedia.org/wiki/Lossy_compression")

---

### Post by jaco223 on 2010-04-04
> **Rob2687 said:**
> [Lossy compression]("http://en.wikipedia.org/wiki/Lossy_compression")

Got it, thanks for the clarification. I learned something.

Jaco

---

### Post by jaco223 on 2010-04-05
Do these fonts look ok?

---

### Post by Longinus00 on 2010-04-05
> **jaco223 said:**
> Do these fonts look ok?

Did you take that picture with a camera?

---

### Post by jaco223 on 2010-04-05
> **Longinus00 said:**
> Did you take that picture with a camera?

Longinus, No I took it with the screen shot tool in ubuntu, but saved it as a .png file
instead of .jpg format. It looks clearer than my originally posted screen shot.

Jaco

---

### Post by Longinus00 on 2010-04-05
> **jaco223 said:**
> Longinus, No I took it with the screen shot tool in ubuntu, but saved it as a .png file
instead of .jpg format. It looks clearer than my originally posted screen shot.

Jaco

Then it's useless because other people won't see what your eyes are seeing, only what's in your framebuffer.

---

### Post by Kyril on 2010-04-05
> **jaco223 said:**
> Do these fonts look ok?

I  like the font. What´s the name of it?

---

### Post by jaco223 on 2010-04-05
> **Longinus00 said:**
> Then it's useless because other people won't see what your eyes are seeing, only what's in your framebuffer.

I give up.

---

### Post by Dougie187 on 2010-04-05
I think it looks good as well. When I compare the fonts in Ubuntu with Windows (In a virtual machine) I think the Ubuntu ones look better. But I guess that's all opinion.

---

### Post by jaco223 on 2010-04-05
Just not worth the effort here.

---

### Post by Dougie187 on 2010-04-07
> **Longinus00 said:**
> Then it's useless because other people won't see what your eyes are seeing, only what's in your framebuffer.

I would think this would be the best determination if the fonts in ubuntu were actually ugly. If he were to post the picture and the fonts were ugly, everyone would be flipping out over how terrible they look. But if he posts a picture claiming that they look ugly, but everyone thinks they look awesome, then he probably has a crappy monitor.

It doesn't matter what his eyes see, it matters what his computer is trying to show.

---

### Post by jaco223 on 2010-04-07
[QUOTE=Dougie187;9087908]I would think this would be the best determination if the fonts in ubuntu were actually ugly. If he were to post the picture and the fonts were ugly, everyone would be flipping out over how terrible they look. But if he posts a picture claiming that they look ugly, but everyone thinks they look awesome, then he probably has a crappy monitor.

It doesn't matter what his eyes see, it matters what his computer is trying to show.[/QUOTE

My monitor is ok, as there is nothing wrong on the OSX side when it comes to the display.

---

### Post by volanin on 2010-04-07
Try this and see if it works for you.
Open a terminal and type:

```

$ cd /etc/fonts/conf.d
$ sudo rm 10-hinting-slight.conf
$ sudo ln -s ../conf.avail/10-hinting-full.conf .
$ sudo ln -s ../conf.avail/10-sub-pixel-rgb.conf .

```

Then restart firefox (or better yet, restart your computer).
Please, post the results here.

P.S.: Pay attention, do not forget the dots (.) at the end of the last two lines!

---

### Post by psyke83 on 2010-04-07
> **volanin said:**
> Try this and see if it works for you.
Open a terminal and type:

```

$ cd /etc/fonts/conf.d
$ sudo rm 10-hinting-slight.conf
$ sudo ln -s ../conf.avail/10-hinting-full.conf .
$ sudo ln -s ../conf.avail/10-sub-pixel-rgb.conf .

```Then restart firefox (or better yet, restart your computer).
Please, post the results here.

P.S.: Pay attention, do not forget the dots (.) at the end of the last two lines!

What is the point of this, especially considering that GNOME Appearance Properties is specifically designed to provide a user interface for changing the font rendering setting?

---

### Post by volanin on 2010-04-07
> **psyke83 said:**
> What is the point of this, especially considering that GNOME Appearance Properties is specifically designed to provide a user interface for changing the font rendering setting?

For some reason, after version 3.5, Firefox takes its font rendering settings from
Fontconfig instead of GNOME's Appearance Properties, so changing the font
settings in GNOME Appearance has no effect.

Source:
[http://www.ubuntu-inside.me/2009/07/howto-fix-firefox-35s-font-hinting.html]("http://www.ubuntu-inside.me/2009/07/howto-fix-firefox-35s-font-hinting.html")

---

### Post by splicerr on 2010-04-07
For me Firefox only seems to work well with Microsoft fonts :confused:  Has been that way for ages. Other apps work fine though with the default fonts, it's just Firefox...

Anyway, you may want to give them a try:

```

sudo apt-get install ttf-mscorefonts-installer

```

---

### Post by psyke83 on 2010-04-07
> **volanin said:**
> For some reason, after version 3.5, Firefox takes its font rendering settings from
Fontconfig instead of GNOME's Appearance Properties, so changing the font
settings in GNOME Appearance has no effect.

Source:
[http://www.ubuntu-inside.me/2009/07/howto-fix-firefox-35s-font-hinting.html](http://www.ubuntu-inside.me/2009/07/howto-fix-firefox-35s-font-hinting.html)

The problem we've been seeing on Lucid is not the same. Ubuntu uses a patched version of cairo which adds the LCD filtering algorithm (originally written by David Turner). The issue is that Firefox itself shipped with an internal build of cairo without the patches to add the new algorithm, causing Firefox to revert to the older LCD filtering method. This was resolved in the last upload (bug report commented by myself and others many times, across several threads).

The instructions you linked are problematic because they will force a certain font setting, and will make the user interface which is supposed to control these settings (i.e. GNOME Appearance Properties, or KDE's Control Center font section), ineffective.

---

### Post by psyke83 on 2010-04-07
> **jaco223 said:**
> Do these fonts look ok?

I think I can see some colour fringing that's not present in Firefox on my system. Question: is this screenshot actually Firefox (and the latest updated version with the included fix for font rendering issues)? I suspect you posted a Chrome screenshot.

---

### Post by jaco223 on 2010-04-07
[QUOTE=psyke83;9089807]I think I can see some colour fringing that's not present in Firefox on my system. Question: is this screenshot actually Firefox (and the latest updated version with the included fix for font rendering issues)? I suspect you posted a Chrome screenshot.[/QUOTE

Pyske88, yes it was a screenshot from Chromium, as this is the browser I have a problem with. I fixed Firefox by changing  the .fontconfig file that I posted early on in this thread, as well as taking your suggestion from awhile back and installing libciaro2 and the LCD patch which you directed me to. All is well with Firefox, as I originally stated "the problem persists with Chromium browser." It's weird because Chromium was ok a few builds back, but then the "hinting" issue resurfaced with later builds. It may have been stated in an older thread. I know also from googling "font rendering chrome" there had been an issue as far back as last year that was reported on launchpad. I know the png. image I posted was not the greatest image, but it was the best I could manage, and to me at least, I can see red and blue hinting that apparently is not seen by some of the other respondents. One of the respondents said my image was "useless" because what you guys are seeing from my image is what's in the frame buffer. Please forgive my lack of knowledge as I'm not sure about the frame buffer, I got some understanding of it from wikipedia.

So I've just reverted to using Firefox, until I can find a solution for Chrome.

Thanks,

Jaco

---

