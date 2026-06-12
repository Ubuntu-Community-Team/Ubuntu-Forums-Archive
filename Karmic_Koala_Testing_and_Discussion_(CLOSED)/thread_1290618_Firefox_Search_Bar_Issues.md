---
title: "Firefox Search Bar Issues"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by samh785 on 2009-10-13
Hi forum! I recently upgraded to Karmic Koala around 2 weeks ago, and just about everything is going perfectly. There is just this one little nagging issue that I've noticed, and I would like to fix. 

The problem is pictured here:
[IMG]http://img73.imageshack.us/img73/2526/searchbar.jpg[/IMG]

When I have a search item selected (like google is) the icon shows up. However when I use the drop down menu to use a different one, no icon shows up at all. It used to work fine in jaunty, and I'd like it very much to work here. Thought I do admit it works fine without it... just a pet peeve.

Thanks in advance

samh785 :P

---

### Post by swoody on 2009-10-13
Are you still using Firefox 3.1.x or are you using 3.5.3? I am using the latter, and the icons appear as usual for me. Firefox 3.5 is available in the repos. If you haven't been using the newer version, you can install it via the repos or use:
```
sudo apt-get remove firefox-3.1 && sudo apt-get install fireox-3.5
```

---

### Post by samh785 on 2009-10-13
I'm using firefox 3.5.3 

If it helps at all, I installed karmic totally from scratch (meaning I used the live cd to erase jaunty and install karmic over it)

---

### Post by swoody on 2009-10-13
Yes, I did a fresh install as well, but again mine shows the icons just fine. This is pretty odd :)

---

### Post by samh785 on 2009-10-13
yeah, I really don't understand it... :P oh well I guess. Maybe the magical open source fairies will fix it.

---

### Post by inportb on 2009-10-13
They'd fix it if you'd lodge a bug report about it.

---

### Post by lovinglinux on 2009-10-14
From gnome menu, open "System >> Preferences >> Appearance", click the "Interface" tab and tick the option "Show icons in menus". You will probably need to restart Firefox.

---

### Post by samh785 on 2009-10-14
> **lovinglinux said:**
> From gnome menu, open "System >> Preferences >> Appearance", click the "Interface" tab and tick the option "Show icons in menus". You will probably need to restart Firefox.

That did it! No idea why that was unchecked though.

---

### Post by FuturePilot on 2009-10-14
> **samh785 said:**
> That did it! No idea why that was unchecked though.

It was an upstream decision to remove the icons from all menus and buttons. That option exists for people who liked the icons. See [https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/407621]("https://bugs.launchpad.net/ubuntu/+source/libgnome/+bug/407621")

---

### Post by swoody on 2009-10-15
> **samh785 said:**
> That did it! No idea why that was unchecked though.

Glad to hear it's working :)

Remember to mark your threads as [SOLVED] when you get an answer, it will help other users who may encounter this same issue in the future. Just click on 'Thread Tools' in the top-right of this page, and then select 'Mark as solved' Thanks :)

---

