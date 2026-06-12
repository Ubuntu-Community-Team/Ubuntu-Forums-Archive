---
title: "ubuntu-desktop being held back in latest Karmic updates?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Squonk07 on 2009-10-02
Yesterday I took advantage of the Beta release as an opportunity to do some system shuffling I had been putting off. I downloaded the 32-bit .iso shortly after the official announcement and reinstalled Karmic afresh.

So far I haven't had any issues, but today I noticed that there is a ton of updates (138 selected) and the Update Manager is warning me that it can only conduct a Partial Upgrade. Scanning through the packages I noticed that ubuntu-desktop appears to be being held back.

I'm not going to play with a Partial Upgrade, and I was wondering if anybody else experienced this. I remember ubuntu-desktop got held back once recently, and that time it was to replace the Software Store with the Software Center. Anybody know what's going on?

---

### Post by solitaire on 2009-10-02
i've got 3 items held back```
  libbonobo2-common libgtk2.0-bin ubuntu-desktop
```I just went ahead and ran the partial. I use the terminal rather than the "Update Manager"

```
sudo apt-get update && sudo apt-get upgrade
```
Things are fine except for those 3 being held back. It will work itself out in the next updates.. ^__^

---

### Post by kansasnoob on 2009-10-02
The servers are overloaded due to people upgrading and downloading the Beta.

You were right not to do a partial upgrade.

Here in the US I find the server usually frees up in between 1AM and 5AM Central time.

---

### Post by Ichtyandr on 2009-10-02
I too have these two packages held back:
libgtk2.0-bin libbonobo2-common
ubuntu-desktop however upgraded easily

Also I know this is offtopic, but do you happen to know if it is possible to remove the annoying 60-second notification in the shutdown/restart/logout menu in the top right corner. that could be easily canceled in jaunty, is this part of the beta arrangement or actually possible to get rid of?
thanks in advance

overall seems that a very nice release is coming imho! I am finally content with the human theme look and did not tinker with it at all.

---

### Post by LKjell on 2009-10-02
> **Ichtyandr said:**
> I too have these two packages held back:
libgtk2.0-bin libbonobo2-common
ubuntu-desktop however upgraded easily

Also I know this is offtopic, but do you happen to know if it is possible to remove the annoying 60-second notification in the shutdown/restart/logout menu in the top right corner. that could be easily canceled in jaunty, is this part of the beta arrangement or actually possible to get rid of?
thanks in advance

overall seems that a very nice release is coming imho! I am finally content with the human theme look and did not tinker with it at all.
Use search button. Otherwise it is in gconf-editor, under apps, indicator-session

---

### Post by Ichtyandr on 2009-10-02
Thanks!

---

### Post by mdurham on 2009-10-02
> **LKjell said:**
> Use search button. Otherwise it is in gconf-editor, under apps, indicator-session

Thank you very much LKjell (and Ichtyandr for asking), it was so annoying. What happened to the preferences?

On the topic of things being held back. I find Synaptic handles it all quite well and seems to overcome any held-back problems.

Cheers, Mike

---

### Post by Squonk07 on 2009-10-02
I went ahead and did the update, figuring that the worst that could happen would be that I might have to spend some quality time with the CLI, or else simply reinstall (I have a separate Home partition). I also installed the ubuntu-desktop update through apt. The system required a reboot, and all was well.

This was a pretty comprehensive update. Several things got fixed for me, including a non-functional "Users and Groups" options dialog and the unreadable progress bar for the Update Manager.

Of course I'm not advocating doing a Partial Upgrade--in fact, **don't do it**--but by dismissing the P.U. dialog and just installing the updates I didn't come out too badly. **Proceed at your own risk.**

EDIT: Spoke too soon. Compiz appears to be borked.
EDIT: It's back. A reboot revived it, though it lost all my settings.

---

### Post by forumache on 2009-10-03
What I do when I see the "Partial updates" question:

I close Updates Manager, open up a terminal and type:

sudo aptitude safe-upgrade

which will do the safe upgrade, i.e. update packages but not remove anything, the held back packages will remain

then

sudo aptitude full-upgrade

and it will explain and ask: sometimes in order to update one packages, another one might be removed, etc. It will ask and I will answer (usually Yes).

---

