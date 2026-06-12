---
title: "Settings for indicator-applet?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jimmio on 2009-10-27
Hello all,

Are there any settings for the indicator applet? It's really annoying me. There's a large gap between the top bar and the indication, and it only shows one indication, then once that goes away, another one shows up. The old one was perfect, the new one is horrid.

Any settings anywhere for it or do I just have to remove it from the bar?

Thanks,
Jim

---

### Post by 5nak3 on 2009-10-27
Sorry

---

### Post by 5nak3 on 2009-10-27
Sorry I might be a bit dense here, but what do you mean about the indicator applet. 

Are you talking about those black popups for instance when someone logs into Empathy or Pidgin, or do you mean the little envelope sitting in the top panel?

If you mean the little envelope, I cannot help you as I do not use that, in face I remove it right away.

But if you mean the notification popups I might be able to help.

---

### Post by jimmio on 2009-10-27
The notifications themselves are annoying me a lot. The mail indicator thing never hurt anyone :p

---

### Post by jblackhall on 2009-10-27
I believe the reason for the gap is that space is reserved for high priority notifications.  Feel free to correct me if I'm wrong though.

---

### Post by qamelian on 2009-10-27
> **jblackhall said:**
> I believe the reason for the gap is that space is reserved for high priority notifications.  Feel free to correct me if I'm wrong though.

No, you're correct. I can't find the thread right now, but it has already been explained that this change is intentional on the part of the devs, and the position of the notification depends on the type of notification. It was done this way as a usability experiment.

---

### Post by jimmio on 2009-10-28
> **qamelian said:**
> No, you're correct. I can't find the thread right now, but it has already been explained that this change is intentional on the part of the devs, and the position of the notification depends on the type of notification. It was done this way as a usability experiment.

An experiment? I'm thinking about looking for the source to try and change in myself.. because at this point I just want them to go away.

---

### Post by Keyper7 on 2009-10-28
> **qamelian said:**
> No, you're correct. I can't find the thread right now, but it has already been explained that this change is intentional on the part of the devs, and the position of the notification depends on the type of notification. It was done this way as a usability experiment.

Just one addendum: it's not about priority, but about synchronicity.

The explanation in details, from Mark Shuttleworth himself, can be found here:

[https://lists.launchpad.net/ayatana/msg00752.html](https://lists.launchpad.net/ayatana/msg00752.html)

PS: The OP seems to be confusing indicator-applet with notify-osd. The former is the envelope thingy. The latter is the bubbles.

---

### Post by jimmio on 2009-10-28
Alright, so what's the name of the package and where can I find the source to ubuntu packages so I can change it?

Or better yet, can I just swap out the package from Jaunty or will that likely break it?

---

### Post by jimmio on 2009-10-28
Sorry for double post, but I just manually replaced  /usr/lib/notify-osd/notify-osd with the one from Jaunty, and all is good. :D

---

### Post by Keyper7 on 2009-10-28
> **jimmio said:**
> Alright, so what's the name of the package and where can I find the source to ubuntu packages so I can change it?

Or better yet, can I just swap out the package from Jaunty or will that likely break it?

If I remember correctly, removing the package notify-osd and installing the package notification-daemon will bring the pre-Jaunty notifications back. You must do both operations in one go, though, as there are important applications that demand that one of them are installed.

---

### Post by 5nak3 on 2009-10-28
Well since we are talking about the notify-osd. I also didn't like the bubbles and their gap. So I went about trying to find a solution.

I found this thread

[http://ubuntuforums.org/showthread.php?t=1300902](http://ubuntuforums.org/showthread.php?t=1300902)

which pointed to this fix

[https://edge.launchpad.net/~gilir/+archive/updates/+sourcepub/776615/+listing-archive-extra](https://edge.launchpad.net/~gilir/+archive/updates/+sourcepub/776615/+listing-archive-extra)

since the fix is a deb file, i downloaded and installed it and I got the jaunty-esque behaviour for my notification bubbles :)

If someone could shed some light as to whether or not this was a good move on my part I'd very thankful. I've had no problems with it though so I cant complain about it I guess.

---

### Post by qamelian on 2009-10-28
> **Keyper7 said:**
> Just one addendum: it's not about priority, but about synchronicity.

The explanation in details, from Mark Shuttleworth himself, can be found here:

[https://lists.launchpad.net/ayatana/msg00752.html](https://lists.launchpad.net/ayatana/msg00752.html)

PS: The OP seems to be confusing indicator-applet with notify-osd. The former is the envelope thingy. The latter is the bubbles.
Ah, that's right! Thanks for posting this. I remembered that there was a reason for the change but not the details. :)

---

