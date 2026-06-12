---
title: "Problem with urxvt(borderless) with fluxbox"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by cos4 on 2006-12-07
After upgrading to Ubuntu 6.10 I've got a problem with urxvt. It is displayed  on all workspaces and I can't change it's position(using alt+left mouse). This problem didn't occure before the upgrade to Edgy, in which fluxbox was upgraded to version 1.0 RC2.

Any idea?

ps:This is what my Xdefaults look like
> urxvt*scrollTtyOutput:  false
urxvt*scrollTtyKeypress:false
urxvt*loginShell:       true
urxvt*font:             xft:Bitstream Vera Sans mono:size=9
urxvt*scrollBar:        false
urxvt*foreground:       #cccccc
urxvt*background:       #000000
urxvt*saveLines:        10000
urxvt*inheritPixmap:    true
urxvt*tintColor:        #ffffff
urxvt*shading:          100
urxvt*geometry:         84x26
urxvt*borderLess:	true
urxvt*shading:		10

(hope thats the right forum)

---

### Post by fly5 on 2006-12-07
I just had same problem, came with latest updates. everything seem to work when you change on the line "URxvt*borderLess: true" true > false.

then run "xrdb -merge ~/.Xresources" or if that doesn't help then "xrdb ~/.Xresources" might do it.

works but then it's not borderless anymore..

---

### Post by po0f on 2006-12-07
cos4,

I use Edgy's rxvt-unicode and all my settings work the way they are supposed to.  The only difference between your's and my settings are the way resources are defined in ~/.Xresources:
```
[FONT="Courier New"]urxvt.resource: value  # what I have (a dot)
urxvt*resource: value  # what you have (an asterisk)[/FONT]
```
Between 7.0 and 7.7-9, rxvt-unicode changed the way resources were defined in .Xresources/.Xdefaults.  You may want to change this and see if it works for you.

---

### Post by cos4 on 2006-12-09
Using a dot doesn't help, with borderless false its ok, but of course not borderless anymore. Seems like there is no solution apart from configuring the borderstyle so that it lookes nice, something I wanted to do anyway.

---

### Post by fly5 on 2006-12-19
Hey I found one solution to get it borderless. Add to ~/.fluxbox/apps following:
```
[app] (urxvt)
[Deco] {NONE}
[end]
```

then reconfigure and try to start urxvt ;)

---

### Post by cos4 on 2006-12-19
Yeah that works, great!
Thanks!

---

