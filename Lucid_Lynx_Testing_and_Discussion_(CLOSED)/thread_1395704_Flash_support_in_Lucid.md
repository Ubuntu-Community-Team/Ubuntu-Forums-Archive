---
title: "Flash support in Lucid"
date: 2010-02-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by haydoni on 2010-02-01
Are there plans to improve flash working on websites, such as bbc iplayer and 4od, in Lucid? I'm not expecting it to work out of the box, but being able to pause (iplayer) etc., without having to terminal bash* would be useful.

Is this on the cards? (I really hope so:) )



*I can't remember where I got the method I did to fix it, but it was similar but even longer than this one:
[http://ubuntuforums.org/archive/index.php/t-1298378.html](http://ubuntuforums.org/archive/index.php/t-1298378.html)
This enabled me to pause, skip and fullscreen, whereas none of the three flash options in Software Centre worked!

---

### Post by philinux on 2010-02-01
> **haydoni said:**
> Are there plans to improve flash working on websites, such as bbc iplayer and 4od, in Lucid? I'm not expecting it to work out of the box, but being able to pause (iplayer) etc., without having to terminal bash* would be useful.

Is this on the cards? (I really hope so:) )



*I can't remember where I got the method I did to fix it, but it was similar but even longer than this one:
[http://ubuntuforums.org/archive/index.php/t-1298378.html](http://ubuntuforums.org/archive/index.php/t-1298378.html)
This enabled me to pause, skip and fullscreen, whereas none of the three flash options in Software Centre worked!

Works out the box here. 64 bit flash plugin from adobe. nVidia 8600gt

---

### Post by haydoni on 2010-02-01
So BBC iplayer works perfectly for you? I thought it also needed Adobe AIR plug-in...

Anyway, I hope you're right, I'll check BBC iplayer on a fresh install. It could be that my terminal fiddling has prevented automatic updates from fixing the issue (I made the "fix" over a month ago).

This will make converting people much much easier.

---

### Post by philinux on 2010-02-01
> **haydoni said:**
> So BBC iplayer works perfectly for you? I thought it also needed Adobe AIR plug-in...

Anyway, I hope you're right, I'll check BBC iplayer on a fresh install. It could be that my terminal fiddling has prevented automatic updates from fixing the issue (I made the "fix" over a month ago).

This will make converting people much much easier.

If I use iplayer I only use the flash version within firefox. Adobe air is only needed for the iplayer download version. This episode is a 651meg download.

---

### Post by xebian on 2010-02-01
> **haydoni said:**
> Are there plans to improve flash working on websites, such as bbc iplayer and 4od, in Lucid? I'm not expecting it to work out of the box, but being able to pause (iplayer) etc., without having to terminal bash* would be useful.

Is this on the cards? (I really hope so:) )



*I can't remember where I got the method I did to fix it, but it was similar but even longer than this one:
[http://ubuntuforums.org/archive/index.php/t-1298378.html](http://ubuntuforums.org/archive/index.php/t-1298378.html)
This enabled me to pause, skip and fullscreen, whereas none of the three flash options in Software Centre worked!

The title is very misleading.  

Flash is NOT BBC iplayer.

---

### Post by Digikid on 2010-02-01
I agree that SOMETHING needs to be done about flash in Ubuntu.  Extremely buggy and works only half of the time.

Hopefully they will get it working right in Lucid.

---

### Post by Merk42 on 2010-02-01
> **Digikid said:**
> I agree that SOMETHING needs to be done about flash in Ubuntu.  Extremely buggy and works only half of the time.

Hopefully they will get it working right in Lucid.

Isn't that really up to Adobe?

---

### Post by Longinus00 on 2010-02-01
> **Digikid said:**
> I agree that SOMETHING needs to be done about flash in Ubuntu.  Extremely buggy and works only half of the time.

Hopefully they will get it working right in Lucid.

There is literally nothing canonical can do about this.

---

### Post by Roasted on 2010-02-02
> **Merk42 said:**
> Isn't that really up to Adobe?

That's what's so scary.

The one thing Steve Jobs did right was calling Adobe lazy...

---

### Post by HomoGleek on 2010-02-02
> **Merk42 said:**
> Isn't that really up to Adobe?
> **Longinus00 said:**
> There is literally nothing canonical can do about this.


I need not use my own words.

---

### Post by HomoGleek on 2010-02-02
P.S iPlayer, 4OD, ITV Player, five OD all work fine for me, just the evil SkyPlayer using the evil silverlight that I have issues with.... moonlight my bum!

---

### Post by blazemore on 2010-02-15
I'm having a problem with flash player where it won't recognize my mouse input. If I click Play for example on Youtube, it ignores me.

---

### Post by HomoGleek on 2010-02-15
What Flash Plugin are you using?

---

### Post by blazemore on 2010-02-15
> **HomoGleek said:**
> What Flash Plugin are you using?

Adobe one from the Firefox wizard.
Package name is flashplugin-installer and I think it's the same as flashplugin-nonfree.

---

### Post by dudude on 2010-02-15
> **blazemore said:**
> I'm having a problem with flash player where it won't recognize my mouse input. If I click Play for example on Youtube, it ignores me.

I found a fix for this problem with 64 bit Karmic (probably works for Lucid too, but I haven't tried it yet).

The fix was to add "export GDK_NATIVE_WINDOWS=1" to the /usr/lib/nspluginwrapper/i386/linux/npviewer file.

My npviewer file:
```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

This allows clicking in flash players on Youtube and Hulu and such, with Compiz active.

As always, YMMV.

If anyone cares, [HERE]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407") is the bug report for the clicks-not-working problem.

---

### Post by emarkay on 2010-02-16
Oh how I have hated Flash - from websites that require it to do simple page selection to all the annoying adverts - and who decided it and its FLV format was the best choice for multimedia?

But, like Windows itself, we have stuck ourselves into a downward compatibility quagmire of patches and kludges on top of an already poorly engineered application to make it the universally accepted monstrosity it is today.

I thought there was HTML5 or some other multimedia transport out there - but then again, will the masses of U-Tube wannabeez migrate to it?  

It's the author (Adobe)  of the software's priority to get it right before the application (Mozilla Firefox) it is used in is adjusted, then if the OS (Ubuntu Linux) needs any modifications, they are made; in that oder.

Go post something about this on Adobe's board - and listen to the silence...

---

### Post by Merk42 on 2010-02-16
> **emarkay said:**
> 
I thought there was HTML5 or some other multimedia transport out there - but then again, will the masses of U-Tube wannabeez migrate to it?  


Too much fighting between the more adopted and technically superior h.264 versus the FOSS theora.

---

### Post by chippy99 on 2010-04-14
Thanks Dudude for the tip about npviewer file settings, that fixed BBC Iplayer for me

---

### Post by hanzomon4 on 2010-04-17
> **dudude said:**
> I found a fix for this problem with 64 bit Karmic (probably works for Lucid too, but I haven't tried it yet).

The fix was to add "export GDK_NATIVE_WINDOWS=1" to the /usr/lib/nspluginwrapper/i386/linux/npviewer file.

My npviewer file:
```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

This allows clicking in flash players on Youtube and Hulu and such, with Compiz active.

As always, YMMV.

If anyone cares, [HERE]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407") is the bug report for the clicks-not-working problem.

Thank You!

---

### Post by nux on 2010-04-24
dedude

That fix sorted things for me.
Muchly appreciated.

The lack of control in embedded media apps was the only thing stopping 10.4 from being just about perfect.

---

### Post by Sashin on 2010-04-24
> **Merk42 said:**
> Too much fighting between the more adopted and technically superior h.264 versus the FOSS theora.

It's not more adopted, both Firefox and Opera don't support it but support Ogg theora.

---

### Post by Miguel on 2010-04-24
h.264 is much more CPU intensive than Theora, and recently it has been proven that one can adapt h.264 specific chips to accelerate some key theora ingredients, allowing theora in portable devices.

---

