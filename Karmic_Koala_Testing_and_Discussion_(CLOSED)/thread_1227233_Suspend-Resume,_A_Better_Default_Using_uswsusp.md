---
title: "Suspend-Resume, A Better Default Using uswsusp?"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raronson on 2009-07-30
I'd like to pass along a link from the Apple forum for the devs to consider using the uswsusp package for power management suspend-resume: [http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

I'm not sure if it works equally well on all hardware, but I was having trouble with resume working properly (sluggish mouse and keyboard on resume from suspend) and this fixed it.  Ignore the battery portion of the howto, as it's n/a.

Just for your consideration.  Great work on Karmic though!  Thanks for everything.

---

### Post by phenest on 2009-07-30
What computer do you have? Suspend and hibernation work flawlessly on my Dell Precision M90.

---

### Post by raronson on 2009-07-30
It's a macbook4,1.

---

### Post by zoomy942 on 2009-07-31
lol.  my suspend resume has never worked on any distro.  no sweat though, the boot up is so fast anyway

---

### Post by dgf on 2009-07-31
Since Karmic suspend and hibernate are working great on my laptop. :)

---

### Post by nystire on 2009-08-01
I wish I could say the same. On a Toshiba Satellite P105-S9337, I haven't had working suspend or hibernate since I started with Ubuntu (Warty era).

---

### Post by buzzmandt on 2009-08-01
I've only tried suspend, but works on acer aspire 3680 laptop

---

### Post by raronson on 2009-08-01
Suspend-resume works on my macbook4,1, it's just that upon resume I get extremely sluggish performance.  The touchpad seems to only process every other click, and it's quite a chore to get it to where you want it on screen; like it's on ice, but moving slowly.  Keyboard is affected as well, sometimes key presses are ignored.

Unfortunately, the uswusp (s2ram, s2disk) package that I originally recommended taking a look at only worked for a day, and I naively posted prematurely.

Still trying to figure out what's going on.  I think someone suggested creating another user account and trying suspend-resume with no desktop effects enabled.  If it works, I'll just add the metacity --replace commands to the sleep and resume scripts and try that for a while.

Thanks for all the replies.

---

