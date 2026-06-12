---
title: "Hanso theme gnome-terminal menu bar transparent"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-08-27
Messing around with some of the new themes, I noticed applying the Hanso theme in Karmic results in the gnome-terminal menu bar displaying with transparency. The title bar and window are both opaque, making this visually distracting and unappealing.

Changing line 108 in /usr/share/themes/Hanso/gtk-2.0/gtkrc:
```

- rgba = TRUE
+ rgba = FALSE

```
 fixes this issue.

Filed: [https://bugs.launchpad.net/ubuntu/+source/community-themes/+bug/420074](https://bugs.launchpad.net/ubuntu/+source/community-themes/+bug/420074)

---

### Post by tekstr1der on 2009-08-28
This is fixed upstream now
> From: Andrew Starr-Bochicchio <a.starr.b@gmail.com>
Reply-to: Bug 420074 <420074@bugs.launchpad.net>
To: [email]jws141@comcast.net[/email]
Subject: [Bug 420074] Re: Hanso theme gnome-terminal menu bar
transparent
Date: Fri, 28 Aug 2009 03:31:27 -0000

This was a personal preference that was inadvertently added and not
reverted. The default should be FALSE. I pushed the changes upstream
(rev. 21) along with minor enhancements (highlights) to the metacity.

Regards,

dashua

---

### Post by tekstr1der on 2009-09-10
Fix has landed in Karmic:

```
community-themes (0.17) karmic; urgency=low

  * Second artwork drop.
  * Hanso, v0.4:
   - Disable rgba transparency (LP: #420074).
   - Fix fg[INSENSITIVE] text dark and light toolbar (LP: #424807).
   - Add new metacity icons by mac_v which are larger and more distinct
     (LP: #424025).
   - Fix blue color nautilus-location (LP: #424014).
  * Add Night Impression, build 90904-1.


```

---

