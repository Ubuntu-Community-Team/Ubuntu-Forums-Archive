---
title: "After Install update manager suggests a partial update"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MTHarden on 2008-10-22
I am sorry if this was posted elsewhere, I tried searching and saw some similar posts but nothing that seemed quite like this, nor did any of the other suggestions help. I'm new to this...

Anyway, I recently installed a fresh 8.10 install from ISO, it installed kernal 2.6.27-4 I then did an update of 300+ updates but this broke my network card (which I have since fixed with help from others). I think the problem was a partial update that I did, and even now when I go to update manager I see a lot of choices greyed out. Things like Linux-generic and ubuntu-desktop. That all seems important so why might they be grey? And is it a problem? I had originally guessed it was for the reason listed as "Normal Changes of a Pre-release version of Ubuntu"

So how do I make these other updates ... update? Is it something with the kernel? Should I try:
```
apt-get install --reinstall linux-image-2.6.27-7-generic
```

---

### Post by jfernyhough on 2008-10-22
I'd download the latest daily CD image and reinstall rather than trying to fix stuff from an old release.

Or wait for the RC which will be out very, very shortly.

---

### Post by sdowney717 on 2008-10-22
view those greyed updates as mostly bug fixes.
you still have the functionality of the installed files.
it will eventually be resolved.

I right now have a completely updated system.

---

