---
title: "can't change system sound"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by adredz on 2009-03-20
I want to disable the 'jungle sound' login sound but I couldn't because it always reverts to default settings each I change it. Bug?

---

### Post by cripou on 2009-03-22
Did you try System -> Preferences -> Sound, Sounds Tab, Desktop: Login, click on "Default" and select "Disabled" instead?

---

### Post by scaine on 2009-03-22
I remember having trouble changing my login sound a couple of weeks ago, but I've definitely changed it here.  I'll see if I can reproduce my steps.  It's definitely Bruce Campbell telling me "Groovy" when I log in now.  Jungle drums - sheesh.  Who thought that one up?  ;)

[EDIT : Nope, it just changes perfectly every time I choose a new sound now.  I just can't remember the issue I had with this - although I definitely did experience some strange behaviour when I first went to change it.  I'll give this a go on the MacMini up the stairs tomorrow if I get a chance, since it's still on the default sound as I only rebuilt it a couple of days ago]

---

### Post by | MM | on 2009-03-22
I have the same problem... i cannot change the system sounds, they reset to defaults everytime i open the SOund Options

---

### Post by Nullack on 2009-03-22
Bug report? :)

---

### Post by scaine on 2009-03-23
> **Nullack said:**
> Bug report? :)

Yep, I'll sort it later.  For the moment, here's the fix.

When you open the sounds control panel, you must select a theme (Ubuntu is the only one in fact) before you can make any changes to any of the system sounds.

Once you've selected, a theme, all your changes will be cool.

Clearly a bug.  I'll do it later...

[Edit : [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/347537](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/347537) now filed.  Please confirm and choose the "Affects me too"]

---

