---
title: "Two Network Managers?"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-11
I already reported this bug, but I was wondering if there was a work around.

I have both ubuntu-desktop and kubuntu-desktop installed, and knetworkmanager (QT) and NetworkManager (GTK) both load at startup on both KDE and Gnome.

In Gnome this isn't that big of a deal, because I just rightclick knetworkmanager and close it. In KDE, however, you can't get rid of the GTK NetworkManager, and if you kill the process, your networking dies.

Anyone else that use both Ubuntu and Kubuntu have this problem?

---

### Post by xerosis on 2008-09-11
knetworkmanager doesn't work at the moment, hence needing the gnome version too.

---

### Post by jlacroix on 2008-09-11
> **xerosis said:**
> knetworkmanager doesn't work at the moment, hence needing the gnome version too.

Seriously? It wasn't until yesterday that I installed Gnome on this machine (previously it was all kubuntu) and I didn't have NetworkManager before adding Gnome, just knetworkmanager, and it worked fine for me. (Unless you're referring to laptop users).

---

### Post by xerosis on 2008-09-11
I've only ever used it for wireless so maybe ethernet works? But yeah, it's not been updated to use the new APIs yet so it doesn't work.

---

### Post by jlacroix on 2008-09-11
That explains it.

Is this also why Gnome wants to load both jockey-kde and jockey-gtk at startup?

---

### Post by ronacc on 2008-09-11
having both gnome and kde installed can cause all kind of strange things , what I do is install gnome and then just add the kde apps I want .

---

### Post by jlacroix on 2008-09-11
> **ronacc said:**
> having both gnome and kde installed can cause all kind of strange things , what I do is install gnome and then just add the kde apps I want .

Well I didn't want a partial KDE. I really don't like Gnome much at all, but I installed it because I was curious about what the new features of Ubuntu were.

While I agree that strange things did happen when both gnome and kde were installed, those problems were worked out with the last two or three releases. Having this issue is a bit of a surprise to me.

Although, having XFCE and Gnome installed at the same time is STILL problematic so I haven't even chanced it in Intrepid.

---

### Post by ronacc on 2008-09-11
I believe the problems arises because if you have two WMs installed both start some stuff (like networking) before you get to the point where you chose which kind of session you want , and I have found most kde apps run just fine under gnome , if you install them through synaptic they will drag in their dependencies gwenview and k3b both of which I prefer to their gnome equivalents run fine unfortunately superkaramba which is far ahead of any thing in gnome chokes on it .

---

### Post by jlacroix on 2008-09-11
> **ronacc said:**
> I believe the problems arises because if you have two WMs installed both start some stuff (like networking) before you get to the point where you chose which kind of session you want , and I have found most kde apps run just fine under gnome , if you install them through synaptic they will drag in their dependencies gwenview and k3b both of which I prefer to their gnome equivalents run fine unfortunately superkaramba which is far ahead of any thing in gnome chokes on it .

The thing is, that this was never a problem before.

As far as using Gnome and installing KDE apps, I dislike Gnome quite a bit so I wouldn't be able to use it as the primary window manager. I just installed it because I like to keep up on Ubuntu's development.

---

### Post by ronacc on 2008-09-11
Its been several years since I had both fully installed ,dapper I think , and I remember having problems with them not getting along real well although I don't remember specifics .

---

