---
title: "Why so many usb_id errors on startup?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tsger on 2009-09-30
When Karmic Alpha 6 boots up, there are several lines of text containing the words: usb_id...unable to access...then it lists a usb device.  Even with no external usb devices plugged in, I get these errors (although not as many as I get with the devices plugged in).  Haven't seen this talked about yet in the Karmic Forums.  

Is this being addressed?

---

### Post by rajeev1204 on 2009-09-30
> **tsger said:**
> When Karmic Alpha 6 boots up, there are several lines of text containing the words: usb_id...unable to access...then it lists a usb device.  Even with no external usb devices plugged in, I get these errors (although not as many as I get with the devices plugged in).  Haven't seen this talked about yet in the Karmic Forums.  

Is this being addressed?

Same here.I get message 'enabling write through buffer'

---

### Post by forumache on 2009-09-30
> **tsger said:**
> When Karmic Alpha 6 boots up, there are several lines of text containing the words: usb_id...unable to access...then it lists a usb device.  Even with no external usb devices plugged in, I get these errors (although not as many as I get with the devices plugged in).  Haven't seen this talked about yet in the Karmic Forums.  

Is this being addressed?

Report a new bug and I'll subscribe to it. Attach a picture of your screen too. If you don't have a camera at hand, I can add a picture from my screen to the bug.

---

### Post by tsger on 2009-09-30
> **forumache said:**
> Report a new bug and I'll subscribe to it. Attach a picture of your screen too. If you don't have a camera at hand, I can add a picture from my screen to the bug.

OK, I filed a bug report [_**here**_]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/439648").

This is the first time I've filed a bug report, hope I did it right!

---

### Post by forumache on 2009-10-01
> **tsger said:**
> This is the first time I've filed a bug report, hope I did it right!

It's perfect. I will open a new bug for some other stuff which I see it does not appear on your bug report (some ohci1394 messages).

---

### Post by fut21 on 2009-10-01
I can comfirm this bug.

---

### Post by ljrmorgan on 2009-10-01
Yeah, I get this too.

---

### Post by forumache on 2009-10-01
> **fut21 said:**
> I can confirm this bug.

Not here. Visit the bug in Launchpad. You have the link above.
Although the bug's status is already "confirmed".

---

### Post by fut21 on 2009-10-01
> **forumache said:**
> Not here. Visit the bug in Launchpad. You have the link above.
Although the bug's status is already "confirmed".


I have confirmed this bug as "wedel"

---

### Post by meborc on 2009-10-01
i get this too

---

### Post by FrancoNero on 2009-10-01
yeah same here, should be merged with topics like

[http://ubuntuforums.org/showthread.php?t=1269015](http://ubuntuforums.org/showthread.php?t=1269015)

---

### Post by FrancoNero on 2009-10-02
there were a couple of updates today, but the problem persists

---

### Post by novafluxx on 2009-10-02
Merge with mine :)

[http://ubuntuforums.org/showthread.php?t=1272184](http://ubuntuforums.org/showthread.php?t=1272184)

---

### Post by fut21 on 2009-10-04
> **FrancoNero said:**
> there were a couple of updates today, but the problem persists

Yes thats true, and i still have the problem like you, really annoying.

---

### Post by tsger on 2009-10-15
Problem seems to have been resolved with this week's updates.  I am just wondering if the usb errors are really gone or just hidden behind the white ubuntu logo on startup?

---

