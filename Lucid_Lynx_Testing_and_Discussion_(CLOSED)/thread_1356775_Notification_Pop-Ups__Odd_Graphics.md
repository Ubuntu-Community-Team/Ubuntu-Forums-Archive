---
title: "Notification Pop-Ups:  Odd Graphics"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tacantara on 2009-12-16
See attached screenshot.  The notification pop-ups have grid lines running through them, and usually some error-type message.  I'm not experiencing any other problems with graphics.  In fact, I set the visual effects to extra, and all appears well.

Has this already been reported?  I've tried Google searching this, but found nothing.  Is this an issue worth putting up on Launchpad (if it hasn't been reported yet)?

---

### Post by MacUntu on 2009-12-16
It has been put in debug mode (deliberately), so nothing to worry about. :)

---

### Post by tacantara on 2009-12-16
Thanks for the quick reply :)

---

### Post by enginuysal on 2009-12-30
> **MacUntu said:**
> It has been put in debug mode (deliberately), so nothing to worry about. :)

Are we able to take it from debug mode back to production/normal mode?

---

### Post by phillw on 2009-12-30
Hi,

Not until we've tested every possible alert ;-)

Could take some time :-)

I find it useful - an easy way to remind me if I'm in 9.10 or 10.04

:lolflag:

Phill.

---

### Post by MacUntu on 2009-12-30
> **enginuysal said:**
> Are we able to take it from debug mode back to production/normal mode?

Sure, just remove 'DEBUG=1' from the file '/usr/share/dbus-1/services/org.freedesktop.Notifications.service'.

---

### Post by jfernyhough on 2009-12-30
Hmm... I tried setting DEBUG=0 (a couple of months ago) and it had no effect. I've just tried deleting the whole declaration this time.

---

### Post by n3had on 2009-12-31
Check the screenshot

---

### Post by vojtech.t on 2009-12-31
I don't know, but seems to be bug -- [https://bugs.edge.launchpad.net/notify-osd/+bug/495035](https://bugs.edge.launchpad.net/notify-osd/+bug/495035)

---

### Post by donniezazen on 2009-12-31
> **n3had said:**
> Check the screenshot

Yeah! Its been like this for over a fortnight.

---

### Post by zika on 2009-12-31
> **MacUntu said:**
> Sure, just remove 'DEBUG=1' from the file '/usr/share/dbus-1/services/org.freedesktop.Notifications.service'.Great! Thank You very much! Have a peaceful, healthy and lucky 2010!

---

### Post by Podex on 2009-12-31
[http://ubuntuforums.org/showthread.php?t=1356775](http://ubuntuforums.org/showthread.php?t=1356775)
[http://ubuntuforums.org/showthread.php?t=1362296](http://ubuntuforums.org/showthread.php?t=1362296)
[http://ubuntuforums.org/showthread.php?t=1333546](http://ubuntuforums.org/showthread.php?t=1333546)
[http://ubuntuforums.org/showthread.php?t=1324573](http://ubuntuforums.org/showthread.php?t=1324573)
[http://ubuntuforums.org/showthread.php?t=1332944](http://ubuntuforums.org/showthread.php?t=1332944)
...

Couldn't you have just searched this forum first to see if this had been reported before?

---

### Post by n3had on 2009-12-31
> **Podex said:**
> [http://ubuntuforums.org/showthread.php?t=1356775](http://ubuntuforums.org/showthread.php?t=1356775)
[http://ubuntuforums.org/showthread.php?t=1362296](http://ubuntuforums.org/showthread.php?t=1362296)
[http://ubuntuforums.org/showthread.php?t=1333546](http://ubuntuforums.org/showthread.php?t=1333546)
[http://ubuntuforums.org/showthread.php?t=1324573](http://ubuntuforums.org/showthread.php?t=1324573)
[http://ubuntuforums.org/showthread.php?t=1332944](http://ubuntuforums.org/showthread.php?t=1332944)
...

Couldn't you have just searched this forum first to see if this had been reported before?

usually i don't create new threads but thanks for the link. and i'll keep that in mind lol

---

### Post by n3had on 2009-12-31
> **MacUntu said:**
> Sure, just remove 'DEBUG=1' from the file '/usr/share/dbus-1/services/org.freedesktop.Notifications.service'.

thanks man

---

### Post by VMC on 2009-12-31
> **MacUntu said:**
> Sure, just remove 'DEBUG=1' from the file '/usr/share/dbus-1/services/org.freedesktop.Notifications.service'.

Yes, thanks! Although I wont be doing this. I want to see its development, but now at least we know where to look.

---

### Post by yelo3 on 2009-12-31
This doesn't work for me, even after a reboot

---

### Post by k3lt01 on 2009-12-31
> **soham_1207 said:**
> Yeah! Its been like this for over a fortnight.It has actually been like that since day one of Lucid, on my machine anyway.

If you take a look at it you can see its a debugging thing because it has "low urgency" written in it.

---

### Post by Vanishing on 2009-12-31
> **vojtech.t said:**
> I don't know, but seems to be bug -- [https://bugs.edge.launchpad.net/notify-osd/+bug/495035](https://bugs.edge.launchpad.net/notify-osd/+bug/495035)

its set to debug on purpose.

---

### Post by zika on 2010-01-01
> **vojtech.t said:**
> I don't know, but seems to be bug -- [https://bugs.edge.launchpad.net/notify-osd/+bug/495035](https://bugs.edge.launchpad.net/notify-osd/+bug/495035)No, it is not a bug. Just take a [look](http://ubuntuforums.org/showpost.php?p=8584329&postcount=6).

---

### Post by ranch hand on 2010-01-01
Tried this fix myself on here and it has no effect at all that I can see.

This does not bother me in the least.

I do not like that the notification box comes up so low on the screen.  It could be up as much as its full width higher and be out of the way but that is another thing all together.

---

### Post by zika on 2010-01-01
> **ranch hand said:**
> Tried this fix myself on here and it has no effect at all that I can see.

This does not bother me in the least.

I do not like that the notification box comes up so low on the screen.  It could be up as much as its full width higher and be out of the way but that is another thing all together.Did You restart gdm? A simple log-out-in should do. Position of the notification is a decision made by developers to put notifications of "first-oder" in first "row" and others in second "row" so they would not overlap at any time.

---

### Post by k3lt01 on 2010-01-01
> **zika said:**
> Position of the notification is a decision made by developers to put notifications of "first-oder" in first "row" and others in second "row" so they would not overlap at any time.They all come up in exactly the same spot. First Battery then Network Connection, sometimes they do overlap and the same thing happens in Karmic.

---

### Post by zika on 2010-01-01
> **k3lt01 said:**
> They all come up in exactly the same spot. First Battery then Network Connection, sometimes they do overlap and the same thing happens in Karmic.Ups, I've been reading blueprint and... I do not pay too much attention on them, I just corrected so that they are not in debug mode, it was ugly...

---

### Post by ranch hand on 2010-01-01
> **zika said:**
> Did You restart gdm? A simple log-out-in should do. Position of the notification is a decision made by developers to put notifications of "first-oder" in first "row" and others in second "row" so they would not overlap at any time.
I did this yesterday and rebooted then.  Since then I have been on 9.04 all night and then back on here and then restarted to boot to 3 other OS' on here to see if it was safe to upgrade here and back here now.

There is no difference in the notification box.  Beats me.  Doesn't matter to me so I just get on with things that do.

---

### Post by MacUntu on 2010-01-02
The notification position is definitely something I wanna see patched. I do understand the rationals behind the differentiation between asynchronous and synchronous notifications, but it's just so damn ugly.

---

### Post by ranch hand on 2010-01-02
It most certainly is ugly.

---

### Post by VMC on 2010-01-02
> **MacUntu said:**
> The notification position is definitely something I wanna see patched. I do understand the rationals behind the differentiation between asynchronous and synchronous notifications, but it's just so damn ugly.

Well I'm damn ugly too, and I'm not going to get fixed anytime soon, so why should the Notification :)

With those yellow lines and all, it appears they are for some sort of alignment.

---

### Post by MacUntu on 2010-01-02
> **VMC said:**
> Well I'm damn ugly too, and I'm not going to get fixed anytime soon, so why should the Notification

The benefits that come with open source software. ;) I don't expect this to happen upstream, but I'm sure sooner or later someone annoyed enough will provide a patch to move ALL bubbles to the top right corner.

---

### Post by Nysosym on 2010-01-02
Is it planed to send an event to the specific application, if i click on the notification? I wanne read a message if i click on the notification for example.

---

### Post by phillw on 2010-01-03
For those interested in the notifications, the Wiki --> [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)  Is inviting comments.

Regards,

Phill.

---

### Post by VMC on 2010-01-03
> **phillw said:**
> For those interested in the notifications, the Wiki --> [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)  Is inviting comments.
 That wiki should answer all questions regarding this topic. Very in-depth, thanks for sharing.

---

