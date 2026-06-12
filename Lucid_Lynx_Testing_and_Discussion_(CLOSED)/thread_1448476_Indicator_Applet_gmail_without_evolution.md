---
title: "Indicator Applet gmail without evolution"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zoff_ita on 2010-04-06
Hi, I would like to use my GMail account with the new indicator applet.

I couldn't figure out how to use it without evolution, is there any way?

I'm not interested in any other solution, so please don't suggest me gmail-notify and similar...
I've got my way to use gmail but i would prefer to find one to use the indicator applet...

Thanks in advance,
- Zoff -

---

### Post by cpmman on 2010-04-06
cgmail from synaptic.

---

### Post by zoff_ita on 2010-04-06
> **cpmman said:**
> cgmail from synaptic.

Reading the package description there is no reference to indicator applet, it simply use libnotify to use system notifications.

It's not what I'm looking for but exactly what I ask to don't suggest me:
> **zoff_ita said:**
> I'm not interested in any other solution, so please don't suggest me gmail-notify and similar...
I've got my way to use gmail but i would prefer to find one to use the indicator applet...

---

### Post by Atermoon on 2010-04-06
So basically you are looking for a way to see your unread messages inside the messaging menu (where Empathy, Evolution, Pidgin, etc are) instead of having another icon?

---

### Post by zoff_ita on 2010-04-06
> **Atermoon said:**
> So basically you are looking for a way to see your unread messages inside the messaging menu (where Empathy, Evolution, Pidgin, etc are) instead of having another icon?

Reductive but correct, yes.

---

### Post by joey-elijah on 2010-04-06
GMail Notify (gm-notify) uses the indicator applet.

---

### Post by zoff_ita on 2010-04-06
> **joey-elijah said:**
> One of the GMail applications in the software centre uses the indicator applet... I'll go find out which.

It would be awesome! Keep me updated!

---

### Post by joey-elijah on 2010-04-06
Edited post above as well - it is GMail Notify (gm-noitfy)

[http://www.ohloh.net/p/gm-notify](http://www.ohloh.net/p/gm-notify)

---

### Post by zoff_ita on 2010-04-06
> **joey-elijah said:**
> Edited post above as well - it is GMail Notify (gm-noitfy)

[http://www.ohloh.net/p/gm-notify](http://www.ohloh.net/p/gm-notify)

It looks very outdated... Last build on launchpad is almost 2years old...

How can it be integrated in lucid new indicator applet?

---

### Post by joey-elijah on 2010-04-06
Last release was less than a year ago ;)

Project states that it is : 

*A simple and lightweight highly Ubuntu 9.04 integrated GMail Notifier which takes advantages of the new and nice notify-osd and indicator-applet. Because of this it will not run with older Ubuntu versions.*

It's also used in the design mock-ups for the messaging menu in Lucid as an example of 3rd party applications that use the applet.

---

### Post by zoff_ita on 2010-04-06
> **joey-elijah said:**
> Last release was less than a year ago ;)

Project states that it is : 

*A simple and lightweight highly Ubuntu 9.04 integrated GMail Notifier which takes advantages of the new and nice notify-osd and indicator-applet. Because of this it will not run with older Ubuntu versions.*

It's also used in the design mock-ups for the messaging menu in Lucid as an example of 3rd party applications that use the applet.

Well, you were right.
Last release was in december 2009 but they didn't build deb package.

Anyway in current sources [there is a bug]("https://bugs.launchpad.net/gm-notify/+bug/433412") with lucid indicator applet, I had to change a line in python script to get it work.

It seems to be working now, thanks!

---

