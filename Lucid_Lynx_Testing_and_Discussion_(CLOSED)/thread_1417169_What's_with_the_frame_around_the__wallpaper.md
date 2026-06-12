---
title: "What's with the frame around the  wallpaper?"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-02-27
Any image I choose has a thin white frame around it??

---

### Post by godhika on 2010-02-27
It is a nautilus bug. Type > nautilus -q to make it disappear. This has been discussed in several threads here.

---

### Post by Uncle Spellbinder on 2010-02-27
> **godhika said:**
> It is a nautilus bug. Type  to make it disappear. This has been discussed in several threads here.

Thanks. Should have searched before posting. I should know better. Sorry 'bout that. :oops:

---

### Post by andrewabc on 2010-02-27
There is already a bug with similar problem. No time to look tonight, but there was a thread about it past couple days.

EDIT:
too late

---

### Post by MacUntu on 2010-02-27
Visual Gnome annoyance - it's reported upstream, so don't expect it fixed anytime soon. :-# I recommend a light wallpaper.

---

### Post by VMC on 2010-02-27
Strange, I don't have that small white border around anything anymore. I use to. I'm using the default theme and screen and only use visual effects normal. But it use to be there.

---

### Post by exploder on 2010-02-27
I see the white edge around the wallpaper if I use the NVidea drivers, it is not there with the open source drivers.

---

### Post by Ichtyandr on 2010-02-27
i had it with nouveau driver as well. also reappears when changing themes or wallpapers

---

### Post by Uncle Spellbinder on 2010-02-27
> **Ichtyandr said:**
> ...also reappears when changing themes or wallpapers

Fonts, too. This is really ridiculous. I hope this gets addressed before final. Having to do ***nautilus -q*** each time I change something is *REALLY* irritating.

---

### Post by Atermoon on 2010-02-27
Try renaming any file on your desktop and it'll appear no matter what drivers you use ;)

---

### Post by Uncle Spellbinder on 2010-02-27
> **Atermoon said:**
> Try renaming any file on your desktop and it'll appear no matter what drivers you use ;)
Confirmed. I just renamed an avi and the damned frame showed up again.

---

### Post by VMC on 2010-02-27
Here's the [**_original_**]("http://ubuntuforums.org/showthread.php?t=1379469&highlight=nautilus+white") topic on the white frame.
And here is the bug report [**_#507263_**]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263"), and nothing has been reported since January. Go there and "me too" at least, maybe even a comment or two.

---

### Post by Uncle Spellbinder on 2010-02-27
@ VMC

Thanks for the bug link. Left a comment and did the whole "me too" thing.

---

### Post by haydoni on 2010-02-27
In some themes this is not present, for example "dark room".

EDIT: I'm wrong, it was just be a darker shade of grey which is was unnoticeable with my wallpaper.

---

### Post by forcecore on 2010-03-18
waking up topic, it is still on daily 17 for example if changing theme it appears or sometimes creating new files on desktop, i have intel graphics and effects disabled. Only cure is currently if white border appears: nautilus -q

---

### Post by kyleabaker on 2010-03-19
> **forcecore said:**
> waking up topic, it is still on daily 17 for example if changing theme it appears or sometimes creating new files on desktop, i have intel graphics and effects disabled. Only cure is currently if white border appears: nautilus -q

It looks like a fix was recently committed:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/507263)

---

### Post by andrewabc on 2010-03-20
Glad to see it fixed. Too bad it didn't make it in time for beta1 release.

/expect more complaints/bug reports.

---

