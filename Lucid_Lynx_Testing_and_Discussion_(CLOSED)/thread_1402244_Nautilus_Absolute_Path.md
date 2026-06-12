---
title: "Nautilus Absolute Path"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-02-08
How do I get back the path display back in nautilus?

ie. /blahblah/somefolder/somefile

---

### Post by cariboo on 2010-02-08
Have you got the Location Bar enabled in the view menu?

---

### Post by ChadMMc on 2010-02-09
Just to the left of your location bar is a button (looks like a paper and pencil) which toggles between text and button based bar display.

---

### Post by kahumba on 2010-02-09
I know about that button, it works in Karmic but in Lucid it didn't work when I last checked several days ago.

---

### Post by francesco_m on 2010-02-09
> **kahumba said:**
> I know about that button, it works in Karmic but in Lucid it didn't work when I last checked several days ago.

Press Ctrl + L and the location bar changes.

---

### Post by mdurham on 2010-02-09
> **francesco_m said:**
> Press Ctrl + L and the location bar changes.
You also need ESC to return it back to buttons

---

### Post by kahumba on 2010-02-09
Thanks, but why is this?
Is it a bug or some weird usability improvement by making it less obvious?

---

### Post by tad1073 on 2010-02-09
> **cariboo907 said:**
> Have you got the Location Bar enabled in the view menu?

yes

> **francesco_m said:**
> Press Ctrl + L and the location bar changes.

Is there any way to make the change permanent?

---

### Post by Miaou86 on 2010-02-09
hello,
start :
```
gconf-editor
```locate and check :
```
apps ->nautilus -> preferences -> always_use_location_entry
```

---

### Post by MacUntu on 2010-02-09
That's what I've done too, but then you lose the ability to toggle between path and breadcrumb view.

I miss that useful button but it's Gnome, so I'm used to such changes...

---

### Post by tad1073 on 2010-02-09
I prefer the location bar myself, it is easier when working in the terminal, for me that is.

---

### Post by Sophont on 2010-03-06
Good thing I searched before posting a new topic for this. :-)

Thanks for the info about the gconf settings.

I rarely used the breadcrumb variant. But it was nice that I could toggle it with a button.

I'm ok with the default being the breadcrumbs - if some usability testing lead to that decision.
I'm ok with Gnomes tendency to keep options in the UI to a minimum - as long as I can fix things via gconf-editor and most settings are close enough to my preferences.

But not having an option to bring back the button that allows me to toggle that on the fly seems like a needless regression.

Or is there already an option in gconf-editor that I overlooked?

Regarding the default: What is the supposed advantage of the breadcrumbs?
I like the textual version (location_entry) because it allows easy copy/paste. Plus sometimes there are different versions of a path tree and in text it's easy to change the upper end.

I can see the breadcrumbs winning on devices where primary input is via touchpad etc... instead of keyboard - but otherwise?

My personal favourite would be to have the choice not in an extra button but in the context menu of the location field. The context menu is there anyway, it's not large and there would be no button talking space for a rarely used option.

---

### Post by shafin on 2010-03-06
> **Sophont said:**
> 
Regarding the default: What is the supposed advantage of the breadcrumbs?
I like the textual version (location_entry) because it allows easy copy/paste. Plus sometimes there are different versions of a path tree and in text it's easy to change the upper end.
I can see the breadcrumbs winning on devices where primary input is via touchpad etc... instead of keyboard - but otherwise?


On advantage of breadcrumbs is, with it, you can one click move to any of the parent directories and then move back again. Due to this, I only use the location bar in my nautilus and has disabled all the buttons, and I don't miss them.
However, having the toggle button would be the ideal scenario, as everyone is entitled to their tests.

---

### Post by Atermoon on 2010-03-06
I just discovered that if you type **/** in nautilus it switches from breadcrumbs to pathbar! I've no idea for how long it's been like this but I find it really awesome :)

---

### Post by VMC on 2010-03-06
> **Atermoon said:**
> I just discovered that if you type **/** in nautilus it switches from breadcrumbs to pathbar! I've no idea for how long it's been like this but I find it really awesome :)

Your right.Good find. Saves type Ctrl+l.

---

### Post by kahumba on 2010-03-06
> **Sophont said:**
> Good thing I searched before posting a new topic for this. :-)

Thanks for the info about the gconf settings.

I rarely used the breadcrumb variant. But it was nice that I could toggle it with a button.

I'm ok with the default being the breadcrumbs - if some usability testing lead to that decision.
I'm ok with Gnomes tendency to keep options in the UI to a minimum - as long as I can fix things via gconf-editor and most settings are close enough to my preferences.

But not having an option to bring back the button that allows me to toggle that on the fly seems like a needless regression.

Or is there already an option in gconf-editor that I overlooked?

Regarding the default: What is the supposed advantage of the breadcrumbs?
I like the textual version (location_entry) because it allows easy copy/paste. Plus sometimes there are different versions of a path tree and in text it's easy to change the upper end.

I can see the breadcrumbs winning on devices where primary input is via touchpad etc... instead of keyboard - but otherwise?

My personal favourite would be to have the choice not in an extra button but in the context menu of the location field. The context menu is there anyway, it's not large and there would be no button talking space for a rarely used option.
I agree with you.
Canonical lost its way a bit trying to oversimplify simple things (pun intended).
Using breadcrumbs basically means absolute newbies are given priority over medium and advanced users since such users usually prefer the text version.
Should breadcrumbs be set as default? Probably.
Should the text version be **that** hidden? I don't think so.

---

### Post by tad1073 on 2010-03-15
Thanks for the help everyone.

---

