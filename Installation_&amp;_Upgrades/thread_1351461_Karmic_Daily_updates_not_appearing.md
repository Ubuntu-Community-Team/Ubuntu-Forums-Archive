---
title: "Karmic: Daily updates not appearing"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2009-12-10
In previous versions of ubuntu there was a star that appeared when new updates were available. In Karmic this is not happening. How do I put in back on?

Robin

---

### Post by Robbyx on 2009-12-12
Is there a solution?

---

### Post by wojox on 2009-12-12
[http://reformedmusings.wordpress.com/2009/11/14/recovering-daily-update-notification-in-ubuntu-9-10-karmic/](http://reformedmusings.wordpress.com/2009/11/14/recovering-daily-update-notification-in-ubuntu-9-10-karmic/)

---

### Post by avtolle on 2009-12-12
> **Robbyx said:**
> In previous versions of ubuntu there was a star that appeared when new updates were available. In Karmic this is not happening. How do I put in back on?

Robin
This is a guess that even if you change the default for non-security update notification from 7 to 1 day, you will not get the star in the top panel, but rather a minimized Update Manager notification in the bottom panel. If this is the case, then clicking on the notification will open Update Manager in full size, and you would then install from there.

---

### Post by avtolle on 2009-12-12
From the release notes to 9.10, run ```

gconftool -s --type bool /apps/update-notifier/auto_launch false
``` in the terminal.

---

### Post by Robbyx on 2009-12-12
Thanks for the help.

I couldn't find the configuration editor in the applications -- system tools even though it is installed, so I followed 

gconftool -s --type bool /apps/update-notifier/auto_launch false

This went through without error, but nothing has changed on the panel. Where should I look for the update icon?

Robin

---

### Post by avtolle on 2009-12-12
As I said earlier, I suspect you won't get the icon, but rather an item appearing in the bottom panel notification area reading Update Manager.  I note that there was nothing today on my two systems I ran updates on yesterday, if this is helpful.

---

### Post by Robbyx on 2009-12-12
We shall see tomorrow. Thanks.

---

### Post by phillw on 2009-12-12
> **Robbyx said:**
> We shall see tomorrow. Thanks.

All the devs may be 'playing' with Lucid, of course ?

Everyone complains about updates 'breaking' their systems -- mebbie they got fed up of all the complaints ;-)

But, seriously, I've found the updates slow down near a weekend and they become less frequent over time as fewer are needed.

You will have your update manager setup the way you want it, on my system, any non 'may break something' ones are carried out silently.

It's always a surprise to find a new kernel has been waiting for a couple of days to get itself installed :P

Regards,

Phill.

---

### Post by Robbyx on 2009-12-12
I found the update manager and started it. It said it could only do a partial update. I let it go ahead and then as part of the preparing to upgrade the following packages were not capable of authentication 

firefox
firefox-3.0
firefox-3.0-branding
firefox-3.0-gnome-support
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
prism
xulrunner-1.9.1
xulrunner-1.9.1-gnome-support


Hitting close to the error window prevented any further updates, but there was no other choice but to close it.

Robin

---

### Post by lemming465 on 2009-12-12
Check if your *update-notifier* package is installed.  If not, add it back.  If so, try *dpkg-reconfigure update-notifier*.  Or just hit the "reload" button in synaptic or run *sudo aptitude update* occasionally if you are willing to live with manual.

---

### Post by zooounds on 2010-03-22
I do not getting any notifications either....

VERY annoying.

---

### Post by zooounds on 2010-03-22
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

