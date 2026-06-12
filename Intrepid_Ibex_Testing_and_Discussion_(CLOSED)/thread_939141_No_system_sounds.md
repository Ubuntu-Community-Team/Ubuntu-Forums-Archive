---
title: "No system sounds?"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2008-10-05
It seems the system sounds aren't working. I hear the login sound but that's it. I don't hear any of the other system sounds that I set. I can even preview them, but they won't play on an event. However I have no other problems with sounds. Everything else plays sounds fine like media players etc. Are the system sounds broken?

---

### Post by Nullack on 2008-10-05
Try playing the system sounds manually in the sounds window

---

### Post by mdurham on 2008-10-05
> **Nullack said:**
> Try playing the system sounds manually in the sounds window

What's that supposed to do? The OP already said "I can even preview them, but they won't play on an event." I take that to mean he has already done what you suggest. I have exactly the same problem.
Cheers, Mike

---

### Post by autocrosser on 2008-10-05
All comes to those who wait---

I went to my Hardy install & pulled the sound preference from .gnome2/sound/events/gnome-2.soundlist & gtk-events-2.soundlist & installed them in the same place in Intrepid. At least I have most of my sounds available until the new sound pref panel is fixed.

---

### Post by FuturePilot on 2008-10-05
> **Nullack said:**
> Try playing the system sounds manually in the sounds window

> **mdurham said:**
> What's that supposed to do? The OP already said "I can even preview them, but they won't play on an event." I take that to mean he has already done what you suggest. I have exactly the same problem.
Cheers, Mike

Yes. I have already done that. They play fine when I click the little play button in the preferences, but I get no sound when I click on a program in the Applications menu, for example, like I used to.

---

### Post by Grams79 on 2008-10-05
Do you have more then one audio device?
If you have sound card and an on-board sound device try this:
Go to your bios and disable the audio.
Use "Auto detect" for the options in Ubuntu sound.

What is you main sound device btw.

---

### Post by autocrosser on 2008-10-05
The only bug I can see quickly is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267215)

And it looks like it may be time to put together a new bug or see if that one is "close" enough to be added to...

---

### Post by FuturePilot on 2008-10-05
> **Grams79 said:**
> Do you have more then one audio device?
If you have sound card and an on-board sound device try this:
Go to your bios and disable the audio.
Use "Auto detect" for the options in Ubuntu sound.

What is you main sound device btw.
I only have 1 audio device. It is:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```
I tried setting everything in the sound preferences to Auto Detect but it didn't do anything.

> **autocrosser said:**
> The only bug I can see quickly is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267215)

And it looks like it may be time to put together a new bug or see if that one is "close" enough to be added to...
That looks very similar. The only difference is that nothing is grayed out for me like described there.

---

### Post by autocrosser on 2008-10-05
Did you try transferring those files from a Hardy install?

---

### Post by FuturePilot on 2008-10-05
> **autocrosser said:**
> Did you try transferring those files from a Hardy install?

Yeah, but still no system sounds

---

### Post by autocrosser on 2008-10-06
Interesting--I just reinstalled a couple of weeks ago when Alpha 6 came out & it worked for me then--I wonder what changed.....YES--the new Ubuntu sounds deb came out--must have changed some of the defaults.....Not sure what to say now.  You might start a bug in gnome-sound-properties...If so, post it & I'll try to confirm it.

---

### Post by FuturePilot on 2008-10-06
I think I see the problem. gnome-sound-properties is not writing the configuration. I completely deleted ~/.gnome2/sound, opened the sound properties, changed some things and closed it. ~/.gnome2/sound was never recreated. Still looking into this.

---

### Post by FuturePilot on 2008-10-06
Ok. I think I found it. This bug here
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507/]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507/")
Apparently there's a script missing from one of the Ubuntu libcanberra packages.

---

### Post by autocrosser on 2008-10-06
Cool--I went there & confirmed the bug--I remember something about that a couple of weeks ago--didn't keep it to mind :(

I must be going daft--take a look at:  [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703)

is where I found that answer....& the link.[]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")

---

### Post by FuturePilot on 2008-10-06
> **autocrosser said:**
> Cool--I went there & confirmed the bug--I remember something about that a couple of weeks ago--didn't keep it to mind :(

I must be going daft--take a look at:  [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/258703)

is where I found that answer....& the link.[]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")

Yeah that's where I found that bug.

And thanks for your help :)

---

