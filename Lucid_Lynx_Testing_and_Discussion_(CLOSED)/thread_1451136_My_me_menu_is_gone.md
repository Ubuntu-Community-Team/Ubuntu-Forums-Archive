---
title: "My me menu is gone"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FrancoNero on 2010-04-10
I ran an update on the day beta 2 came out, I guess it was a few hours too early, anyways it offered me a partial upgrade and I thought (despite having read the warning) that well it's beta 2 day, what can go wrong... well.... where's my Me Menu? it's gone. A few updates later, the whole system seems quite stable, but the me menu is out of sight.

any ideas?

---

### Post by Atermoon on 2010-04-10
Try adding the Indicator Applet Session to the panel.

---

### Post by howefield on 2010-04-10
After running the updates last night, I had an issue with 2 me menus showing on the panel, with the logout button not there. A simple reboot was enough to fix it, but I guess you have done that.

I was offered a partial upgrade in the morning and so declined it, but by the evening the packages had caught up and all was fine.

If what Atermoon suggests doesn't work, make sure that the indicator-me package is installed.

---

### Post by FrancoNero on 2010-04-10
i mean the menu with my online status, the twitter funcationality and my picture. the indicator applet session just adds the log off button

---

### Post by howefield on 2010-04-10
Is the indicator-me package installed ?

---

### Post by Uncle Spellbinder on 2010-04-10
Right click panel, then click add to panel. There should bee "indicator applet" and "indicator applet session." The latter is the "me menu". Though Gwibbler continues to crash anytime I attempt to use it.

---

### Post by FrancoNero on 2010-04-10
no that's just the thing that looks like the shutdown button, and i have that one

---

### Post by 23meg on 2010-04-10
> **FrancoNero said:**
> no that's just the thing that looks like the shutdown button, and i have that one

Indicator Applet Session is the applet that hosts both the user switcher (shutdown button) and the Me menu. However, if you don't have the indicator-me package installed, you won't have the latter.

---

### Post by repawn on 2010-04-10
> **FrancoNero said:**
> no that's just the thing that looks like the shutdown button, and i have that one

I have the exact same issue - I just assumed it was a UI change. Though there is a space where the me menu would fit perfectly. I have tried to re-install indicator applet session again but it only shows the power button that allows you to logout, etc.

---

### Post by FrancoNero on 2010-04-13
indicator-me was indeed not even installed. something must've removed it, along with gwibber etc... reinstalled it. let's see what happens after a restart :)

---

### Post by Crunchy the Headcrab on 2010-04-13
If you're using the update manager to update, don't.  Use "sudo aptitude update" to find the new packages and "sudo aptitude safe-upgrade" to install them.  The update manager will ignore dependencies from my experience.

---

