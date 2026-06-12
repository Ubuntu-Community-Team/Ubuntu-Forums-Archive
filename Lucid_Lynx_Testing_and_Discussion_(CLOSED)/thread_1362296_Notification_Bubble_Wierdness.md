---
title: "Notification Bubble Wierdness"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Edgeworth on 2009-12-23
On x64 Lucid, this happens:
[IMG]http://i49.tinypic.com/wrz39i.jpg[/IMG]
I've reinstalled the notifications package, to no avail. It's not on launchpad, so I'm wondering if it's just me. Any advice on how to get the traditional notification (Without the lines) back?
Thanks

---

### Post by dcstar on 2009-12-23
> **Edgeworth said:**
> On x64 **Lucid**, this happens:
[IMG]http://i49.tinypic.com/wrz39i.jpg[/IMG]
I've reinstalled the notifications package, to no avail. It's not on launchpad, so I'm wondering if it's just me. Any advice on how to get the traditional notification (Without the lines) back?
Thanks

If you are having problems with a **development** release, then post them in the **development forum** (as specifically instructed when downloading any pre-release version).

There is no point whatsoever in posting issues in a forum where people only use released versions.

---

### Post by ranch hand on 2009-12-23
What weirdness is this you are talking about?  If you mean the cross hatching, that is intended for some reason.  It will go away sometime in the future.  Right now it is supposed to look like that.

---

### Post by artir on 2009-12-23
It's because it's in debug mode, so it shows the spacing between the elements and the priority bar

---

### Post by Gina on 2009-12-23
And are the rows of text supposed to be overlapping?  I guess they have still to get the formatting right.

---

### Post by autocrosser on 2009-12-23
Well---the "normal--report incorrect urgency?" is part of debug with the setting lines...the text under it would be the normal message.....so, everything looks "normal" for right now :)

---

### Post by Mr. Picklesworth on 2009-12-23
The green / red / some-other-colour bars tell you the urgency level of the notification. If you see a notification with the incorrect urgency (eg: "battery critical!" as low urgency, or "10 new RSS feed updates" as high urgency) please file a bug report against the offending package.

---

### Post by Eclipse. on 2009-12-23
Yes they are supposed to be like that for the time being, debug mode is enabled so that we can check that notifications have the correct priority.

I remember there being a thread on this before, search for it if you want more information, I'm sure there was a link to the documentation that outlined the priorities that should be set for certain notifications.That is if your interested in fixing any notification problems.:)

---

### Post by tacantara on 2009-12-23
> **Eclipse. said:**
> Yes they are supposed to be like that for the time being, debug mode is enabled so that we can check that notifications have the correct priority.

I remember there being a thread on this before, search for it if you want more information, I'm sure there was a link to the documentation that outlined the priorities that should be set for certain notifications.That is if your interested in fixing any notification problems.:)

I opened a thread on this just a week or two ago, posing the same question as the OP for this thread.  The answers by Eclipse, ranch hand, and artir, are similar to the responses I received.

---

### Post by 23meg on 2009-12-23
> **Eclipse. said:**
> 
I remember there being a thread on this before, search for it if you want more information, I'm sure there was a link to the documentation that outlined the priorities that should be set for certain notifications.That is if your interested in fixing any notification problems.:)

Here it is:

[http://ubuntuforums.org/showthread.php?t=1193705](http://ubuntuforums.org/showthread.php?t=1193705)

---

