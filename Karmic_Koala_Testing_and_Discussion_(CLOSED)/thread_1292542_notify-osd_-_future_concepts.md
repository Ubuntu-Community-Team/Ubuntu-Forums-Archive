---
title: "notify-osd - future concepts?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kestal on 2009-10-16
Though I know there have been a few changes lately to notify-osd (especially on the configuration part - I tested out a few of my own notifications which was kind of neat, too).. is there anything currently in mind for interacting with the notifications, or will it always just serve as "JUST" an informant?

Ie) an instant message or a 'new email' from someone... I'd love being able to click on the notification for it to go to my email (taken from preferred programs, or based solely on the program-specific way of doing it), or even an error message to see a detailed log about it... etc.

If nothing like this is planned, where is notify-osd going to go from here?

Also, the current slot which is saved for system notifications, is this just for testing purposes (until the code is available to prioritize the notifications on-the-fly)? or will it be like that permanently?

---

### Post by kansasnoob on 2009-10-16
You can learn more here:

[https://launchpad.net/notify-osd](https://launchpad.net/notify-osd)

You could even sign up for the mailing list:

[https://launchpad.net/~ayatana](https://launchpad.net/~ayatana)

as explained here:

[https://help.launchpad.net/ListHelp#Subscribing%20to%20a%20mailing%20list](https://help.launchpad.net/ListHelp#Subscribing%20to%20a%20mailing%20list)

---

### Post by mpt on 2009-10-16
> **kestal said:**
> Ie) an instant message or a 'new email' from someone... I'd love being able to click on the notification for it to go to my email (taken from preferred programs, or based solely on the program-specific way of doing it), or even an error message to see a detailed log about it... etc.

I wrote [notification design guidelines]("https://wiki.ubuntu.com/NotificationDesignGuidelines") to advise developers on how to provide interactive notifications if necessary. For example, messaging programs should integrate with the messaging menu to let people access new messages directly.

> *If nothing like this is planned, where is notify-osd going to go from here?*

There may be tweaks to visual style, duration *etc*, but apart from that it’s pretty much done.

> *Also, the current slot which is saved for system notifications, is this just for testing purposes (until the code is available to prioritize the notifications on-the-fly)? or will it be like that permanently?*

The current bubble positioning was decided by Mark Shuttleworth. As to whether it will be like that permanently, well, he has changed his mind about things before.

---

