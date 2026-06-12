---
title: "How do I change my status from Hidden in Empathy? I'm perma hidden on MSN!"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-09-22
How can I change my status in MSN, or in each account individually? Is it even possible? I'm set available on all other accounts, but MSN is hidden and I can't figure out how to change it.

Using Karmic of course, with latest updates (as of 1 hour ago)s

---

### Post by graaant on 2009-09-22
I get this too.
However, I've now got no status bar icon either :(

---

### Post by novafluxx on 2009-09-22
I was hoping by Alpha 6 most of the issues would be complete with Empathy and we'd just test them, guess this is one of those bugs. I wonder if its already been reported.

---

### Post by graaant on 2009-09-22
Strangely, removing and reinstalling Empathy does not fix this for me. It seems the system tray icon flashes up and then quickly disappears :(

I've tried a complete removal with Synaptic and it still happens. I wonder if some config files are hiding somewhere causing this.

---

### Post by blakamin on 2009-09-23
Yet another thing I thought *I'd* broken...
It's actually hiding in you message notification area (little envelope)
Mentioned [here in launchpad]("https://bugs.edge.launchpad.net/empathy/+bug/290471/comments/11")

---

### Post by meborc on 2009-09-23
this is the same problem : [http://ubuntuforums.org/showthread.php?t=1270847](http://ubuntuforums.org/showthread.php?t=1270847)

fix - use the telepathy PPA

---

### Post by novafluxx on 2009-09-23
> **meborc said:**
> this is the same problem : [http://ubuntuforums.org/showthread.php?t=1270847](http://ubuntuforums.org/showthread.php?t=1270847)

fix - use the telepathy PPA

So if we need to use the PPA to get what I consider basic functionality...why is this going in as default haha its so sad it actually makes me laugh. If I'm going to use a PPA for my instant message client im going to use pidgin, thanks.

I gave it a chance, again, and it still fales (fales, not fails) horrible. Good Game.

I'm hoping these wonderous things from the PPA make it into Karmic repo's prior to the beta freeze...

---

### Post by meborc on 2009-09-23
> **novafluxx said:**
> So if we need to use the PPA to get what I consider basic functionality...why is this going in as default haha its so sad it actually makes me laugh. If I'm going to use a PPA for my instant message client im going to use pidgin, thanks.

I gave it a chance, again, and it still fales (fales, not fails) horrible. Good Game.

I'm hoping these wonderous things from the PPA make it into Karmic repo's prior to the beta freeze...

it is quite disturbing that the version of empathy in karmic is so...buggy

but the point is that stuff tested at the telepathy PPA will end up in karmic pretty soon... the PPA is for testing the builds before inserting into karmic... not as in other PPA's which are there due to NOT going into default install

---

### Post by terry_gardener on 2009-09-23
this happened to me i was always showing as hidden on my side and offline to contacts.
solved it by uninstalling the telepathy-butterfly package then i was showed as online.

then when i did updates it installed the telepathy-butterfly package again and it has work ever since.

---

### Post by novafluxx on 2009-09-23
I'll have to check it out again then, and see whats going on. So far I'm disappointed

---

