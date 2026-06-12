---
title: "Pop-up Notifications preferences doesn't change message location"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Muflon on 2009-10-11
Using the Pop-up Notifications(notification-properties) doesn't have any affect on the position of the notifications on the screen.

You can subscribe to this bug if it also affects you.

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/394871](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/394871)

Muflon

---

### Post by go7Ul1ai on 2009-10-11
The notification-properties application only works with the old notification deamon.. There is no plans to allow users to configure notify-osd and it's positioning.

---

### Post by Muflon on 2009-10-11
> **lee.jarratt said:**
> The notification-properties application only works with the old notification deamon.. There is no plans to allow users to configure notify-osd and it's positioning.

Thanks Lee. I will mark this solved.

Muflon

---

### Post by hikaricore on 2009-10-11
> **lee.jarratt said:**
> The notification-properties application only works with the old notification deamon.. There is no plans to allow users to configure notify-osd and it's positioning.

Really?  That's an absolute shame..

---

### Post by TrueTom on 2009-10-11
> **hikaricore said:**
> Really?  That's an absolute shame..

Or sheer incompetence...:)

---

### Post by hikaricore on 2009-10-11
> **TrueTom said:**
> Or sheer incompetence...:)

This is gnome we're talking about, could be.

---

### Post by 23meg on 2009-10-12
> **hikaricore said:**
> This is gnome we're talking about, could be.

Neither Notify OSD, nor notification-daemon are part of GNOME, so no, it's not GNOME you're talking about.

---

### Post by ricsi-pontaz on 2009-10-12
> **Muflon said:**
> Using the Pop-up Notifications(notification-properties) doesn't have any affect on the position of the notifications on the screen.

You can subscribe to this bug if it also affects you.

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/394871](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/394871)

Muflon

And this will be the final position of the notify? I hope it's not.

---

### Post by autocrosser on 2009-10-12
This has been talked about for the last couple of months &---yes that is the "current" final position--unless the devs change their minds.....it was put there so people can hit the close/min/max buttons without dismissing the dialog.....I don't use a top panel so it works very well for me----but as in anything, some will like it---some won't.  If you don't like it---convince a developer to write a config panel for the daemon & get it run thru the motus.....I'm working with the SUM developer to get a update so grub2 has one.

So, as with anything---be proactive & contribute to the process.

---

### Post by novafluxx on 2009-10-12
"Ubunut - By Developers, for Developers

If you don't like something, FIX IT YOURSELF OR STOP WHINING, 'cause our decision is final."


Seems to be the way things are headed.

If you can't program the change yourself, you're basically told to shut your mouth or contribute. Or we can ask someone with programming knowledge to do it for us.


9.10 is looking to be pretty Microsoftish to me...in my humble opitnion of course.

---

### Post by SeanBlader on 2009-10-12
I agree with Novafluxx, and on top of that, I don't think that sort of attitude is going to solve Bug number 1.

---

### Post by autocrosser on 2009-10-12
What I'm saying is to talk about it in a constructive manner (and searching for the topic wouldn't hurt either....) I guess that I'm a bit testy about all the talk about this--there must be pages of thread about it from the last couple of months & the "I don't like it--it's stupid" tone wanted the answer I gave also (in my opinion).

---

### Post by ktp on 2009-10-12
> **autocrosser said:**
> What I'm saying is to talk about it in a constructive manner (and searching for the topic wouldn't hurt either....) I guess that I'm a bit testy about all the talk about this--there must be pages of thread about it from the last couple of months & the "I don't like it--it's stupid" tone wanted the answer I gave also (in my opinion).

I have/had strong feeling about this issue since day one (pre-9.04) and I am in the same boat as you...getting really sick of talking about it =).  The bug is there and lets hope dev/designers consider it important issue.  

Besides I don't think this is going to make or break 9.10 since it was like this in 9.04 (which doesn't make it right or wrong).  UI is hard to design since everyone is different.  This is one of the reasons for configurations but that can also complicate things.  Lets hope the right balance is found.

---

### Post by novafluxx on 2009-10-12
This is why we want front-ends or easy to read config files to edit these settings, so they devs only have to worry about defaults, not trying to please everyone.

---

### Post by ktp on 2009-10-12
> **novafluxx said:**
> This is why we want front-ends or easy to read config files to edit these settings, so they devs only have to worry about defaults, not trying to please everyone.

This is the bug you need to comment on:

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095)

---

