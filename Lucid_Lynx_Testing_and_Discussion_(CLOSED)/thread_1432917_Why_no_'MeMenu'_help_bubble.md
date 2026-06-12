---
title: "Why no 'MeMenu' help bubble?"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-03-18
I just noticed that virtually everything on the desktop and in the drop down menus gets a help bubble telling you what you are looking at does when you hover your pointer over. 

However the new MeMenu is missing this, on my system anyway. Would it be possible to get someone to include this feature for it? Especially since this is a new feature, some hints at the purpose of the blank box (what it updates when you write in it), chat, broadcast and ubuntu one would be very useful. Both for new users and those upgrading from the previous LTS!

Anyone know if this is going to be addressed or where to go to get something applied during the Beta testing period?

---

### Post by cariboo on 2010-03-18
Report the problem as a bug:

```
ubuntu-bug me-menu
```

I'm running gnome-shell at the moment, so I can't comment about the tool-tip.

---

### Post by 23meg on 2010-03-18
One point to note is that the broadcast field is supposed to only appear if you have set up an account. But that isn't implemented yet.

---

### Post by victor9098 on 2010-03-18
> **cariboo907 said:**
> Report the problem as a bug:

```
ubuntu-bug me-menu
```

I'm running gnome-shell at the moment, so I can't comment about the tool-tip.

I ran that in terminal and got the following message:

> Package me-menu does not exist

23meg, yes I have set up my facebook/twitter/flickr accounts in gwibber but I just thought it was inconsistent with the rest of the desktop not having a tooltip, especially for a feature that they have been promoting so much.

---

### Post by cariboo on 2010-03-18
Sorry about that, I was sure I saw a memenu package, but the package to file the bug against should be, indicator-me, eg:

```
ubuntu-bug indicator-me
```

---

### Post by Mr. Picklesworth on 2010-03-18
Bug report exists, don't worry:
[https://bugs.edge.launchpad.net/indicator-application/+bug/527458](https://bugs.edge.launchpad.net/indicator-application/+bug/527458)
:)

---

### Post by victor9098 on 2010-03-19
Thanks everyone! I love it when a plan comes together.

---

