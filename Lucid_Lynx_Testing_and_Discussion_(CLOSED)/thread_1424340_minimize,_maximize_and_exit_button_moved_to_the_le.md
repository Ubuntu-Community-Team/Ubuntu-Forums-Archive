---
title: "minimize, maximize and exit button moved to the left hand side?"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by a8jr on 2010-03-07
hi guys im using ubuntu lucid lynx x86 32bit, and i was wondering why  the minimize, maximize and exit button moved to the left hand side? 
I mean:

[[IMG]http://img62.imageshack.us/img62/5606/screenshotibj.png[/IMG]]("http://img62.imageshack.us/i/screenshotibj.png/")

This does not depend on the theme im using, every theme just changed  into this way. it was on the right hand side when i was using  karmic but after i upgraded to lucid (and did not make any change to any  settings at all), it suddenly changed this way.

Is there any setting to change this? I feel awkward having it on the  left hand side.

---

### Post by overdrank on 2010-03-07
Moved to Lucid Lynx Testing and Discussion

---

### Post by Merk42 on 2010-03-07
[It's part of the new theme](http://ubuntuforums.org/showthread.php?t=1422422)

---

### Post by autocrosser on 2010-03-07
Yea---really more Mac OSX-ish....   Don't know if I like more Mac OSX-ish, but it's different.....I'm sure that the guys that try to make things look like Mac OS will have a field-day.....

---

### Post by dagrump on 2010-03-07
Do I see a merge here? Yes they did, & I changed it back, But I'm not cool, happening, or with it... What ever thats worth.
Some one was inspired. So they changed something to prove they could.
You can change it back, if you would like to.

---

### Post by hikaricore on 2010-03-07
I'm also not a fan of the new Human Dyslexic theme.  Luckly I rarely use gnome so it's a non-issue.

---

### Post by uRock on 2010-03-07
This caused me to reinstall Karmic on my Netbook. I tried the simple fix found in the forum and they didn't work.

---

### Post by Regenweald on 2010-03-07
It's already grown on me. All in all, no big difference to me.

---

### Post by zykotick9 on 2010-03-08
To move them back to the old layout.

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

---

### Post by blakamin on 2010-03-08
And so it begins...





[http://ubuntuforums.org/showthread.php?t=1422422](http://ubuntuforums.org/showthread.php?t=1422422)



[COLOR="White"][SIZE="1"]Is this really a new forum member or somebody taking the mickey?[/SIZE][/COLOR]
rofl

---

### Post by a8jr on 2010-03-08
@admins: sorry for the wrong thread placement. i dont know if there is special place for discussing lucid lynx

so is there any way to change this now? it feels like having spoon on your left hand while you are right handed...

---

### Post by philinux on 2010-03-08
> **a8jr said:**
> @admins: sorry for the wrong thread placement. i dont know if there is special place for discussing lucid lynx

so is there any way to change this now? it feels like having spoon on your left hand while you are right handed...

Read post #9 of this thread ;)

And this thread in the forum. [http://ubuntuforums.org/showthread.php?t=1422422](http://ubuntuforums.org/showthread.php?t=1422422)

---

### Post by slymi2005 on 2010-03-08
Yeah I've gotten used to the new placement already, not a big deal, but is anyone else having issues with the whole window bar disappearing. I have to go to file close because the max, min, close disappear. Any help?

---

### Post by Luke has no name on 2010-03-08
Thank the LORD for this fix. Moving the buttons to the left is unequivocally a poor shift in usability. No longer can you simply wave your mouse button over to close a window. Now, the left side of the window is too busy, while the right side is blank. And yes, it is a shift from two decades of a subtle yet important set of buttons being in one specific location.

STICKY THIS THREAD.

Edit:
The one thing I've seen that logically justifies this move is that in Netbooks and smaller screens, there is less mouse movement which makes for easier use. Still, This should be something adjustable in the theme advanced settings, or something similar.

I just wish the design team justified their decision. Shuttleworth did a great job explaining the other branding changes and their rationale in the weekly newsletter.

---

