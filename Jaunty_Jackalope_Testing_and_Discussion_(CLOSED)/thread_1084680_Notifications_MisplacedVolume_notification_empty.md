---
title: "Notifications: Misplaced/Volume notification empty"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dbugger on 2009-03-02
Hi guys. I just upgraded to the jaunty and I love it. It runs faster than Intrepid (just a few crashes, of course).

Just a small complaint, the notifications are a little misplaces, on top of the top bar, and when I change the volume, nothing appears in the notification.

---

### Post by forumache on 2009-03-02
Both are reported as bugs. See the temporary workarounds in launchpad.

---

### Post by medeshago on 2009-03-02
Do this:
```

sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status/

killall -15 notify-osd
```

---

### Post by forumache on 2009-03-02
Don't do this:
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status

Why would you mess Ubuntu? Make the new version not install correctly?
I, at least, try to use Ubuntu as it was designed: without a command line.

If I want to "play with Linux", I play with Gentoo. If you want to play harder, try Linux from Scratch.

I know some friends who are still configuring the network using ifconfig.

P.S. notify-osd was updated today, the bugs might have been fixed. If you did the above (cp ...) you'll never know...

---

### Post by Dbugger on 2009-03-03
> **forumache said:**
> P.S. notify-osd was updated today, the bugs might have been fixed. If you did the above (cp ...) you'll never know...

The notifications are now properly placed, but the volume change doesnt use the new notification system anymore. I guess I'll have to wait a little more

---

### Post by meborc on 2009-03-03
> **forumache said:**
> Don't do this:
sudo cp /usr/share/icons/Human/scalable/status/notification-* /usr/share/icons/gnome/scalable/status

Why would you mess Ubuntu? 
emmm... so that the notifications would actually work


> **forumache said:**
> If I want to "play with Linux", I play with Gentoo. If you want to play harder, try Linux from Scratch.
you are in no position to say who should play with what... the OP stated a problem... the next person directed him to launtchpad... and the third gave a quick fix

if you are not OK with this and think the OP will mess up his/hers computer, then you totally misunderstand the concept of alpha-testing

if you just want to use ubuntu and NOT fix things, then there is no reason to use jaunty... use stable instead... or better yet, don't use computers, you might get finger sore ;)

---

### Post by forumache on 2009-03-03
Thanks meborc, I guess you missed the point.

I report bugs, try different solutions, but I'm always able to revert to Ubuntu for human beings :)

If you start copying files around, you'll never know when the bug was fixed. Worse, another bug will appear and you won't be able to fix it, because it works for you. I cannot explain better, if you still don't understand me, let's leave it like that.

Regarding not using computers, I guess it is impossible. Of course, I can just resign from my job where I work as a software engineer and start growing potatoes ;)

Chill out, it's supposed to be fun.

P.S. The person who directed him to launchpad is... wait for it... me. Of course I'm OK with that :))

---

### Post by meborc on 2009-03-03
yeah, i understand your point. keep it vanilla... good for bug reporting :)

but i also think that a possibility to fix the problem should be there... the decision of whether to use the fix or not should be the one who has the problem... and since he is in jaunty testing, he knows the outcome of that

the thing that was missing from post 3 is the notice - UGLY FIX

and you were indeed the first reply - sorry for that

:)

---

### Post by forumache on 2009-03-03
> **Dbugger said:**
> The notifications are now properly placed, but the volume change doesnt use the new notification system anymore. I guess I'll have to wait a little more

Yes, this is know as bug 333997:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/333997](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/333997)

@meborc: no problem, everything is ok ;)

---

