---
title: "How to Ignore Updates?"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by subscrive on 2007-06-13
Hi All,

I am using ubuntu 6.06.
I got a notification of updates - checked and found them to be xscreensaver related.

I want to disable notification for these updates permenantly.

Can anyone help me in disabling them?

-- 
~A.

---

### Post by CautionaryX on 2007-06-13
Hi,

Try going to System > Preferences > Sessions> Startup Programs and disable update-notifier. log out, log back in and it should be fixed.

---

### Post by wpshooter on 2007-06-13
My advice would be that you turn it off by unchecking the box in the **software sources **portion of the O/S under System/Administration instead of doing it in the sessions section.

---

### Post by subscrive on 2007-06-14
I dont want to disable the notification.
I want to get other updates.

I just want to disable the update of that particular package of xsaver.

Also I am using Kubuntu. So pl tell me disabling of that package in kubuntu context.

Thx.

---

### Post by bapoumba on 2007-06-14
In adept, is there a menu to lock a package version ?

---

### Post by subscrive on 2007-06-15
I didnt find any way to lock/disable/ignore update notification of a particular package.

---

### Post by bapoumba on 2007-06-15
to lock a package version either you do it from a GUI application (I know you can do it in synaptic. I do not know KDE, and I supposed the GUI application was adept. Are you using synaptic or adept ?)
Or, you pin a package version from the terminal. It's in the /etc/apt/preferences file: [http://www.die.net/doc/linux/man/man...erences.5.html]("http://www.die.net/doc/linux/man/man...erences.5.html")

---

### Post by subscrive on 2007-06-16
Thx for the replies.
A bug has already been opened against kubuntu.

---

