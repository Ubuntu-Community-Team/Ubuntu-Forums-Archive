---
title: "Unsure about my current ppa list"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by slpixe on 2010-10-17
Hey all,

I have a fair few "other sources"/ppa's on my software list.

But recently I have been having it just give 404/cannot find/update.
Which includes the red triangle appearing saying failed to update.

Attached is my ppa list, and which ones are failing.

I was wondering if anyone knew why these were failing, and which ones I can remove (due to updated ppa's e.g. lucid/10.10)

also if its better to have the launchpad/ubuntu tested/working copies that get the updates slow.

or the developers ppa e.g. for google products/dropbox etc.

List of ppa's
[IMG]http://img207.imageshack.us/img207/5945/ppas.png[/IMG]

List showing failed's
[IMG]http://img683.imageshack.us/img683/2756/ppafails.png[/IMG]

---

### Post by mörgæs on 2010-10-18
Did you read your post after posting? There is nothing attached.

---

### Post by slpixe on 2010-10-20
erm,
theres 2 big PNG photos in the first post.

---

### Post by endotherm on 2010-10-20
I am starting to see the images, but imageshack is way too slow. after 2 minutes of loading, still cant see the whole image, and my bandwidth here is fine.

op, when I get 404's on repos (PPA or otherwise), I usually try again in a few hours or the next day. 98% of the time that takes care of it. you can always try navigating to the repo via a browser.

---

### Post by slpixe on 2010-10-20
Yeah I did an update today and it all seamed to work fine
tried doing a check afterwards, and again 404's

img1:
[IMG]http://dl.dropbox.com/u/3450178/ppas.png[/IMG]
img2:
[IMG]http://dl.dropbox.com/u/3450178/ppa%20fails.png[/IMG]

Hopefully those load better

---

### Post by Frogs Hair on 2010-10-20
PPAs contain the packages needed to use the software and may conflict with other software. both officially supported and otherwise. Having many PPAs often leads to unresolved dependencies , that is why they are use at your own risk.

---

### Post by slpixe on 2010-10-20
oh, I thought a PPA was a external server which hosted software packages e.g. empathy.deb or something.

So they appear on my sympathic software, to download software e.g. chromium, dropbox.

and also allowed updating of the software, as most/all sortware on ubuntu cannot update itself, and uses 1 global update system (update manager).

which is why i've added stuff like the dropbox repo, so that I can download it, and it is updated..

---

### Post by Frogs Hair on 2010-10-20
The Personal Package Archive is not officially supported , some software developed through the PPA does make it into the official Ubuntu releases . Conflicts between packages do arise and some PPAs that worked with a previous version of Ubuntu may not work the current version . It is up to the user to check launch pad and make sure that the PPA they choose is compatible.

If the update manger , say in Maverick , attempts to connect to a source and does not find a Maverick package it will return an error , such as failed to fetch.

---

### Post by endotherm on 2010-10-20
> **slpixe said:**
> oh, I thought a PPA was a external server which hosted software packages e.g. empathy.deb or something.

So they appear on my sympathic software, to download software e.g. chromium, dropbox.

and also allowed updating of the software, as most/all sortware on ubuntu cannot update itself, and uses 1 global update system (update manager).

which is why i've added stuff like the dropbox repo, so that I can download it, and it is updated..

that's the general idea, yes

---

