---
title: "Docky hangs on &quot;about do&quot;?"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Confuseling on 2009-04-13
Can someone confirm this as a bug?

Run Gnome Do in Docky mode.

Right click on Gnome Do icon on left.

Select "About Do".

About Do window opens correctly, but system soft-locks. Ctrl Alt Backspace works, as does switching to a virtual terminal to reset.

Thanks.

ETA: Interestingly it doesn't hang in non Docky mode...

ETA2: Another one: Two-finger tap (i.e. middle mouse) on Docky Firefox icon doesn't seem to open another window any more. Again, if someone can confirm I'll launch a bug. Thanks.

---

### Post by Confuseling on 2009-04-14
OK, I'll bump and rephrase. I'm using the LPIA architecture, so trying to narrow down what's causing this. Would someone using Docky please try it on their system (you can reboot cleanly - just hit ctrl-alt-f1, log in, and type 'sudo shutdown -r now' and you'll be fine) and report what happens?

---

### Post by Darkshade on 2009-04-14
Same behavior here - both Firefox and About Do. I'm using Do 0.8.1.3

The only difference (or maybe not?) is that I'm able to move my mouse when everything seems locked and press the Close button on the About Do window, then everything goes back to normal. It's the only place I can click though.

---

### Post by scaine on 2009-04-14
Same here.  Soft lock when running About Do, but I can click on the "close" button to restore the whole system.  Do version 0.8.1.3, running on a MacMini (ie intel graphics), compiz enabled.

---

### Post by Confuseling on 2009-04-14
OK, thanks. I can't click close (either the dialogue button or the window button, though mouse does move), but it's still always let me reset happily. I can't find anything in dmesg, x-session-errors, or /var/log/messages - maybe someone who can successfully kill it can have a peek too, or if anyone has suggestions of where else I should look they would be welcome. Might also be worth someone for whom quit is working running it from a console, and seeing if it spits anything out - I'm not seeing anything here.

scaine, you say you're on a mac mini, so I suppose that eliminates architecture.

I will sign up to launchpad and file some bugs tomorrow. Cheers.

---

### Post by binbash on 2009-04-14
same here.

---

### Post by FuturePilot on 2009-04-14
It seems that when I click About Do the only thing that it will let me click on is the Close button. Everything else seems locked.

---

### Post by Confuseling on 2009-04-15
Bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/361679](https://bugs.launchpad.net/ubuntu/+source/gnome-do/+bug/361679)

The firefox issue I reported, then realised immediately that it was duplicate. Apparently it's fixed in a newer version.

---

### Post by Confuseling on 2009-04-15
Can anyone not using intel graphics and experiencing this please post a comment to that effect on the launchpad bug report, or just post here and I'll notify the dev who may be barking up the wrong tree.

Thanks.

---

