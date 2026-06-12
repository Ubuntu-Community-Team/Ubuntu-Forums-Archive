---
title: "ATI - some issues of curiosity"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by barisurum on 2009-09-15
Are the TTM memory manager, radeon kernel modesetting and dri2 active in karmic by default? Which 2d accelerator is default XAA or EXA and how can I change if it is XAA? (I couldn't find the xorg.conf file) And finaly will there be a tool for us open source ati users like catalyst control center to change 3d settings, set fan speeds and perhaps overclock our GPUs? Thanks.

---

### Post by barisurum on 2009-09-17
noone to enlighten me a bit???

---

### Post by JCoster on 2009-09-17
I think I've misunderstood you and that you already know this but the xorg.conf is located at /etc/X11/xorg.conf and from here you set XAA etc. through the options under the driver information.

But I think you probably know this and that I've just totally misunderstood..

---

### Post by Seren on 2009-09-17
> **barisurum said:**
> Are the TTM memory manager, radeon kernel modesetting and dri2 active in karmic by default?


It is not activated by default. I don't know if it will be enable for the final release or not.

> 
 Which 2d accelerator is default XAA or EXA and how can I change if it is XAA? (I couldn't find the xorg.conf file)


IIRC  it is EXA.

You must add

> 
        Option          "AccelMethod"   "xaa"


in the device section of xorg.conf related to the video driver.

> 
 And finaly will there be a tool for us open source ati users like catalyst control center to change 3d settings, set fan speeds and perhaps overclock our GPUs? Thanks.

I haven't heard anything about such a kind of tool for the open source driver.

---

### Post by barisurum on 2009-09-17
JCoster: xorg.conf is built-in in Karmic now and doesn't come up in /etc/X11, I know of that change but is there a way to recreate it or do I need to recreate (is EXA default)?

/etc/X11$ ls
app-defaults  ja_JP.eucJP  xinit       Xsession.d
cursors       ja_JP.UTF-8  xkb         Xsession.options
fonts         rgb.txt      Xresources  XvMCConfig
fs            X            Xsession    Xwrapper.config
baris@barubuntu:/etc/X11$

---

### Post by barisurum on 2009-09-17
Thanks seren for your perfect explanation, sa&#287;ol :)

> 
And finaly will there be a tool for us open source ati users like catalyst control center to change 3d settings, set fan speeds and perhaps overclock our GPUs? Thanks.
I found this:

[http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

will try it...

edit: tested it, promising project, no overclocking and fan speed hacks though

---

### Post by Wise Ferret on 2009-09-17
With the open source ati drivers, the default 2d acceleration is exa.
For information about development of features and controls for the both the open source and proprietary driver try the phoronix forums. They have ati employees posting there.

---

### Post by JCoster on 2009-09-17
> **barisurum said:**
> JCoster: xorg.conf is built-in in Karmic now and doesn't come up in /etc/X11

Oh right thanks for this, I was unaware of that and thought it was a simple question from someone with so many beans!  When you say it is built-in what do you mean by that?  How would you go about editing it?

---

### Post by Eestlane on 2009-09-17
This should show, what's currently used (should check myself, though it's probably EXA already).
> /var/log/Xorg.0.log

You can search for EXA and XAA in it.

grep XAA /var/log/Xorg.0.log

and then:

grep EXA /var/log/Xorg.0.log

This will show the lines in the log containing the word "XAA" and "EXA". For me, it returns this:

"(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)"
[http://www.phoronix.com/forums/showpost.php?p=71968&postcount=5](http://www.phoronix.com/forums/showpost.php?p=71968&postcount=5)

EDIT: Note to myself: should test "MigrationHeuristic" "greedy".

---

### Post by barisurum on 2009-09-17
> When you say it is built-in what do you mean by that? How would you go about editing it?

people say that it generates the file on the fly (like virtual files, device files on ram I suppose), but I'm neither sure nor expert enough about it no matter how high my beans are :)

---

### Post by barisurum on 2009-09-17
Eestlane: It seems EXA is active in open sourced radeon:

> (II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 4
(II) EXA(0): Offscreen pixmap area of 122347520 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video

edit: some opengl extensions like gl framebuffer object still sucks though, lazy reflective water puff :(

---

### Post by Eestlane on 2009-09-17
Ah great. Thanks for checking that out.

Also, I see the Offscreen pixmap area seems to be quite big, so I should definitely test out the greedy mode, though I've no idea actually what it actually does. Actually really.

---

