---
title: "Burn effect missing in compiz"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by slymi2005 on 2009-03-22
I've been googling in search for a solution but nothing has solved my problem. It just is not there and I do not know how to find it. Has it been abandoned perhaps. I'm on ubuntu 9.04 alpha 6.

---

### Post by slymi2005 on 2009-03-22
Thought I should provide more information.

```
compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8500 GT (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

Here is an image of my compiz settings manager, the animations section does not give me the option to enable the burn effect. If I'm not mistaken it was available before I upgraded to 9.04.

[[IMG]http://img53.imageshack.us/img53/7060/screenshotb.th.png[/IMG]](http://img53.imageshack.us/my.php?image=screenshotb.png)

---

### Post by ninjapirate89 on 2009-03-22
In order for burn to show up under Animations, you must also enable Animations Add-On.

---

### Post by slymi2005 on 2009-03-23
It does not appear to be on my list on my eee pc install of ubuntu 9.04 but it was on my desktop install. I am currently installing updates on my eee pc so we'll see if that helps.

[[IMG]http://img8.imageshack.us/img8/3255/screenshot1hfn.th.png[/IMG]](http://img8.imageshack.us/my.php?image=screenshot1hfn.png)

---

### Post by ninjapirate89 on 2009-03-23
Ah 9.04. Sorry can't help as I am using Intrepid.

---

### Post by slymi2005 on 2009-03-23
Maybe I'll get an answer in a month when 9.04 is released.

---

### Post by Inane_Asylum on 2009-03-24
> **ninjapirate89 said:**
> In order for burn to show up under Animations, you must also enable Animations Add-On.

**Thank** you! I couldn't figure it out for the life of me.

If the "thanks" feature still existed, you'd get one...

---

### Post by scaine on 2009-03-24
> **slymi2005 said:**
> Maybe I'll get an answer in a month when 9.04 is released.

As ninjapirate89 notes, "Burn" is one of the animations listed in "AnimationAddOn".  But if I can ask, why are you manually sorting your plug-ins from the preferences screen?  It's easier just to tick them from the main screen, I think.

As for animations themselves, they're easiest to control form simple-ccsm - although you have to manually add that from synaptic.

---

### Post by slymi2005 on 2009-03-25
Yes, I am aware that Burn is an animation listed in animation addon but my problem is that I cannot find "animation addon." It is not on the main screen in CompizConfig Settings Manager

[[IMG]http://img150.imageshack.us/img150/4397/screenshot3y.th.png[/IMG]](http://img150.imageshack.us/my.php?image=screenshot3y.png)

In Simple CompizConfig Settings Manager the option to enable extra animations is greyed out.

[[IMG]http://img150.imageshack.us/img150/7138/screenshot2d.th.png[/IMG]](http://img150.imageshack.us/my.php?image=screenshot2d.png)

The reason I was using the plugins screen was because on my desktop that was how I was able to get the extra animations, by moving "animation addons" to the enabled section. Here on my eee pc though I'm still struggling. I wonder if I am missing a compiz package or something.

---

### Post by Bakon Jarser on 2009-03-25
Do you have compiz-fusion-plugins-extra installed?

---

### Post by slymi2005 on 2009-03-25
Yes I do, version 0.8.2-0ubuntu1.2. There is a package called compiz-fusion-plugins-unsupported but it is version 0.7.8.

I may just try reinstalling compiz see what happens.

---

### Post by Bakon Jarser on 2009-03-26
In case it helps here is all the compiz packages I have installed.

---

### Post by matmat07 on 2009-03-26
I ave the same problem here

---

### Post by slymi2005 on 2009-03-29
Well nice to see I am not the only one with the problem. Did you previously have the burn effect? What version of ubuntu are you on?

---

### Post by philinux on 2009-03-29
Just double checked this and burn is working fine here.

Jaunty beta 64bit clean default install.

Maybe delete your .compiz folder.

---

### Post by slymi2005 on 2009-03-31
I tried that and nothing changed, may I ask why you suggested doing that? I have jaunty 64 bit installed on my desktop and the burn effect is also working fine there, maybe a 32 bit problem? I'm out of ideas.

 I will be reinstalling it when the official release comes out so maybe things will be different then.

---

### Post by synflex on 2009-04-12
Try download compiz-fusion-plugins-extra_0.8.2-0ubuntu1_amd64.deb from intrepid and install with dpkg...

That might bring back animation-addon till jaunty's compiz-plugin package is released.

---

### Post by thethimble on 2009-04-21
Having the same problem on Jaunty x64

---

