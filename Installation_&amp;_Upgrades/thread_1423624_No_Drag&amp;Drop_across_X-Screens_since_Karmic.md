---
title: "No Drag&amp;Drop across X-Screens since Karmic"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Phylax Aranatis on 2010-03-06
Hi there everybody,

being new to the forum let me express my utmost respect for all the good work that is done around here to help people solve their problems concerning ubuntu. They aren't the most important one you may encounter in life but, hey - aren't they the most fun?

So here's mine: 

For the time being a "feature" included in Karmic prevents me from upgrading to it since it's release. **It is impossible to drag and drop (URLs) across separate X-Screens.**

My setup is as follows (see also xorg. conf attached)::

[LIST=1]
[*]2 GPUs with 3 Monitors attached (which excludes Xinerama and the like)
[*]Every Monitor has a separate X-Screen
[/LIST]
Whenever I try to drag an URL (e.g. a file form nautilus) from screen #1 to screen #2 this is what happens when crossing  the border:

**The Cursor appears on the left side of both of the Screens.** On screen #1 the URL (the files Symbol) stays attached to it, on screen #2 it is simply the blank cursor. Dropping the URL drops it onto screen #1, so the one I'm coming from.

This isn't any of a problem in Jaunty and Ibex. I hope this isn't due to any profound changes done to X11. Anyone got an idea how to solve this or whether it will be gone in Lucid?

Thanks in advance and keep up the good work

Phylax

---

### Post by markbuntu on 2010-03-06
I am not sure about nvidia but I think you need to turn xinerama on to get multiple gpus working, maybe nvidia settings can do that for you. There are some threads around here about that somewhere, try the multimedia and video forum.

---

### Post by Phylax on 2010-03-07
Hi there,

thanks for the quick reply.

Unfortunately **Xinerama doesn't work across multiple GPUs.** Even if it did I wouldn't want it, as my leftmost Monitor's resolution is 1024x768 whereas my rightmost has 1200x1920.  With the third in between (1600x1200) I would end up with a **virtual desktop of 3824x1920px**. Plus I need the Xrandr extension to properly pivot Nr. 3, which I'm not certain to work with Xinerama.

What I want is to **set up 3 separate X-Screens as currently running under Jaunty** for almost a year by now, without issues. Just to make sure there's no misunderstanding:  **I needn't drag Windows across Screens**, but only URLs, like Nautilus files, Internet links etc


thanks anyway and best regards from Bavaria

Phylax



(P.S.: If any of the Moderators/Admins considers this questions to be more appropriate in the the multimedia and video forum feel free to move it there)

---

### Post by markbuntu on 2010-03-08
Because xrandr does not support multi-gpus in jaunty or karmic one way or another you were using xinerama to move between separate x screens with multiple gpus. The nvidia and ati drivers provide their own implementations of xinerama to make this possible with their gpus so it is not always obvious that xinerama is being used, but it is.

---

### Post by Phylax on 2010-03-23
Sorry for taking so long answering to your last reply,


I'm pretty sure that Xinerama is not activated, as it says in my xorg.conf:
```

Section "ServerFlags"
	Option         "Xinerama" "0"
EndSection

```

The only thing I use XRandR for is rotating Monitor #3:
```

Section "Device"
	Identifier     "Device2"
...
	Option         "RandRRotation" "1"
EndSection

```

However, I fear there still is a **misunderstanding:** 

**I do not "move" across screens in Jaunty**, at least not as if my several screens acted like one. This means I cannot and I needn't move Windows across the borders. 

But there is a thing that works flawlessly in Jaunty, which doesn't in Karmic: There is no way to drag and drop URLs (internet links, file emplacements etc.). To give an example: I'm writing a new email with thunderbird on screen #3 and I want attach a file to it. Under Jaunty I can just open a nautilus window on screen #2. I can not move this window to the other screen. But I can **drag and drop** the file onto the message window on screen #3. That's what no longer works under Karmic.

I hope to have made clear that **it is not a continuous desktop I'm yearning for**, but just the possibility to drag and drop URLs. I'm sorry to insist so much but I was under the impression that there's a misunderstanding here, so please excuse me if this further description was unnecessary.

hoping for further ideas

Phylax

---

### Post by Phylax on 2010-04-19
Sorry for bringing this up once again, but having istalled Lucid Lynx yesterday I see that the problem persists in this version. This rises doubts whether this problem is actually recognized as a "bug" or a "feature". Anyway I can guarantee that it is a serious problem for anyone using a setup with several Xscreens.

So I would be glad to hear about any further ideas concerning this issue

best regards from Bavaria

---

### Post by markbuntu on 2010-04-19
OK, I understand now. Your problem is most likely something changed in the way the clipboard is shared across x-servers which is handled by natuilus I beleive so it is maybe a missing nautilus something or some rules change somewhere.

It likely has nothing to do with the x-server or randr but I would not rule that out entirely.

Try moving something and look in the logs for any message about why it failed or why you are not allowed to do that.

---

