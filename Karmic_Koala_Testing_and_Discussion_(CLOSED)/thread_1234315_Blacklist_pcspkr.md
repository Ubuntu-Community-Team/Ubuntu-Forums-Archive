---
title: "Blacklist pcspkr"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-07
Just done some updates and it asked whether to keep or update /etc/modprobe.d/blacklist.conf. Knowing I'd added a line to disable the pc speaker, I thought I'd check what would change:
```
--- /etc/modprobe.d/blacklist.conf	2009-08-02 19:48:06.228958103 +0100
+++ /etc/modprobe.d/blacklist.conf.dpkg-new	2009-08-07 17:26:27.000000000 +0100
@@ -44,12 +44,12 @@
 # hangs at desktop session start (Ubuntu: #246969)
 blacklist snd_pcsp
 
+# ugly and loud noise, getting on everyone's nerves; this should be done by a
+# nice pulseaudio bing (Ubuntu: #77010)
+blacklist pcspkr
+
 # EDAC driver for amd76x clashes with the agp driver preventing the aperture
 # from being initialised (Ubuntu: #297750). Blacklist so that the driver
 # continues to build and is installable for the few cases where its
 # really needed.
 blacklist amd76x_edac
-
-# PC speaker
-blacklist pcspkr
-

```
So, at last. The pc speaker is disabled by default. Woo hoo!:D

---

### Post by Eestlane on 2009-08-07
Right decision.

---

### Post by racmar on 2009-08-07
I know it's one of the first things I do...  Especially on my laptop, everytime I open the lid... BEEP.

+1 good decision devs.

---

### Post by Darkshade on 2009-08-08
Finally ^^

---

### Post by taavikko on 2009-08-08
Just for more info:
```
module-init-tools (3.10-2) karmic; urgency=low

  * blacklist.conf: Blacklist pcspkr. It produces an ugly and loud noise,
    getting on everyone's nerves. If still needed at all, this should be done
    by a nice pulseaudio bing. (LP: #77010)
```

---

### Post by rudenko_ruslan on 2009-08-08
Right decision.

---

### Post by OutOfReach on 2009-08-08
Ahh finally, it's really annoying and it turns into the very first thing I change about the install....even before the theme.

The thing I wonder is...why wasn't this done before?

---

### Post by phenest on 2009-08-08
> **taavikko said:**
> Just for more info:
```
module-init-tools (3.10-2) karmic; urgency=low

  * blacklist.conf: Blacklist pcspkr. It produces an ugly and loud noise,
    getting on everyone's nerves. If still needed at all, this should be done
    by a nice pulseaudio bing. (LP: #77010)
```

That's already in my post, albeit mine was taken from update manager.

I hope that, if they implement a "nice pulseaudio bing" that it'll be something we can disable easily. No point in replacing one annoying beep with another.

---

### Post by taavikko on 2009-08-08
> **phenest said:**
> That's already in my post, albeit mine was taken from update manager.

Yeah, it was, just put the added info so that people would see what package did the change,

> **phenest said:**
> I hope that, if they implement a "nice pulseaudio bing" that it'll be something we can disable easily. No point in replacing one annoying beep with another.

I agree on that. 
As a sidenote, things need to be more easily configurable in Gnome, without searching for hours what key to change in gconf :)

---

### Post by phenest on 2009-08-08
> **OutOfReach said:**
> The thing I wonder is...why wasn't this done before?

I think this is due to the new [Paper Cut]("https://wiki.ubuntu.com/PaperCut") definition.

---

