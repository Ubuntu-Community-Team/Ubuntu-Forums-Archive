---
title: "Notifications lingering too long?"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by katie-xx on 2010-03-15
Possibly Im imagining this but does anyone else think the notifications are lingering for a while too long?


Kate

---

### Post by ffi on 2010-03-15
notify-osd is broken by desing, the fact I can even click away a notification annoys me so much, so I removed it and installed notification-daemon

---

### Post by katie-xx on 2010-03-15
> **ffi said:**
> notify-osd is broken by desing, the fact I can even click away a notification annoys me so much, so I removed it and installed notification-daemon

Aaaah ..enlightenment thanks.
I guess this has been filed as a report ?

Kate

---

### Post by sgage on 2010-03-15
Notifications have always lingered too long. The fact that you can't click them away is absurd, and the fact that you can't even adjust the timeout is ridiculous. I really think the way they implemented notifications is obnoxious.

---

### Post by Keyper7 on 2010-03-15
> **katie-xx said:**
> Aaaah ..enlightenment thanks.
I guess this has been filed as a report ?

Actually, ffi's post was just general complaints about NotifyOSD and had no relation to your question whatsoever.

What exactly to you mean by lingering too long? You mean compared to Karmic?

---

### Post by katie-xx on 2010-03-15
> **Keyper7 said:**
> Actually, ffi's post was just general complaints about NotifyOSD and had no relation to your question whatsoever.

What exactly to you mean by lingering too long? You mean compared to Karmic?

I actually mean too long per se ..but yes compared to 9.10 as well.
I can only find 4 outstanding bugs for notifyosd and none relate to length of time displayed. [https://bugs.launchpad.net/notify-osd](https://bugs.launchpad.net/notify-osd)
Im not certain this would be a bug ..presumably its intended behaviour ??



Kate

---

### Post by Keyper7 on 2010-03-15
> **katie-xx said:**
> I actually mean too long per se ..but yes compared to 9.10 as well.
I can only find 4 outstanding bugs for notifyosd and none relate to length of time displayed. [https://bugs.launchpad.net/notify-osd](https://bugs.launchpad.net/notify-osd)
Im not certain this would be a bug ..presumably its intended behaviour ??

Maybe they are making experiments related to [Bug 340996](https://bugs.launchpad.net/notify-osd/+bug/340996). Did you notice if the length varies according to the size of the contents?

You might also want to check the latest changelogs in the NotifyOSD package.

---

### Post by Digital Hick on 2010-03-15
> **katie-xx said:**
> Possibly Im imagining this but does anyone else think the notifications are lingering for a while too long?


Kate

No, they seem fine.  8 seconds I would say is how long they last.  How long do they stay for you.:popcorn:

---

### Post by Keyper7 on 2010-03-15
> **Digital Hick said:**
> No, they seem fine.  8 seconds I would say is how long they last.  How long do they stay for you.:popcorn:

[8 seconds sounds a little bit too much](https://wiki.ubuntu.com/NotifyOSD#Animations%20and%20durations)

---

### Post by katie-xx on 2010-03-15
> **Keyper7 said:**
> Maybe they are making experiments related to [Bug 340996]("https://bugs.launchpad.net/notify-osd/+bug/340996"). Did you notice if the length varies according to the size of the contents?
You might also want to check the latest changelogs in the NotifyOSD package.

Seems reasonable to me that may be the reason. Well spotted :)
I think Ill record this for a while to confirm if it is related to text length

Kate

---

### Post by Digital Hick on 2010-03-15
> **Keyper7 said:**
> [8 seconds sounds a little bit too much](https://wiki.ubuntu.com/NotifyOSD#Animations%20and%20durations)

Well, it may be to long for some.  According to the link you gave, 5 seconds is the base on non-critical and 10 seconds for critical.

And the terminus, listed at the bottom, is 15 seconds max for all.  So 8 falls within those constraints even if it is long.

---

### Post by Digital Hick on 2010-03-15
Actually, looking at that blueprint again, it explains why I get two different things in different positions sometimes.  Confirmation and notification is split into separate 'threads'.  The notifications are supposed to scroll also it would appear.

You would have to get quite a few messages in a short period of time to fill up the right side of the screen.  The most I have ever had at once is three I think.:popcorn:

---

