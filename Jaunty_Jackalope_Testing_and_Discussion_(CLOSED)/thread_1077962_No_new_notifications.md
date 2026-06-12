---
title: "No new notifications"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gletob on 2009-02-22
It seems that after apt-get updating, upgrading, and dist-upgrading I can't get those fancy new notifications to work and it's just my account because a new account I created has the new notifications.

P.S. I searched and couldn't find any other thread about this but if there is then I'm sorry.

---

### Post by gletob on 2009-02-22
Oops I figured it out I'm sorry to have bothered anyone:(

---

### Post by morphos on 2009-02-22
Post your solution and mark your thread as solved.

---

### Post by syko21 on 2009-02-22
I am having the same problem, please post your solution.

---

### Post by douham on 2009-02-22
> **syko21 said:**
> i am having the same problem, please post your solution.

+1

---

### Post by syko21 on 2009-02-22
SUCCESS!
```
sudo apt-get install notify-osd
```

---

### Post by autocrosser on 2009-02-22
Hmmmm---my problem is that even after "changing" the location & style--nothing "really" changes--I want to know where other than in gconf are the prefs being set?????

---

### Post by mc4100 on 2009-02-22
> **autocrosser said:**
> Hmmmm---my problem is that even after "changing" the location & style--nothing "really" changes--I want to know where other than in gconf are the prefs being set?????

They don't currently *have* any support for changing style, etc., (though I hope that will change) ... those customizations are for the old notifications.

---

### Post by autocrosser on 2009-02-22
Not good--I really dislike a plain black box with a icon & some text :?

---

### Post by ugkbunb on 2009-02-22
I am running xubuntu and I am having the same problem... purging and re-installing notify-osd has no effect. However the fallback dialogs for messages that do not check that the new notify-osd does not support interarctivity for example when all firefox downloads complete still appear. It is only the temporary black dialogs that are missing... notify-send "test" in terminal and nothing happens.

I filed a bug about it awhile ago on LP... not sure if it just me though:
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/332787](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/332787)

---

