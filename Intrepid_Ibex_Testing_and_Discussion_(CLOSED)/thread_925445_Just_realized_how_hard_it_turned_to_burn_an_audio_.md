---
title: "Just realized how hard it turned to burn an audio CD"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-09-20
Burning an audio CD used to be so simple that my mom had no trouble doing it. When she put a blank CD in the tray a dialogue would ask her what she wanted to burn, a data CD or audio CD. Then serpentine opened and she just had to drag the files.

Now she gets a dialogue asking her what program should be used to handle the blank CD, but only one is actually shown (nautilus) and she doesn't know what brasero is for anyway. Even if she remember she wants to use brasero, she might be presented the data project thingy so she has to figure out she has to open file &#8594; new project &#8594; new audio project. THEN drag the files and hit burn.

There is absolutely no way my mom can figure that out. The process has gone too complicated, and I would like to open a bug about it. But since it's about the dialogue you get when you insert the CD, what package should it affect?

---

### Post by zekopeko on 2008-09-20
me thinks that this could be easily solved by presenting the old nautilus "Burn data or audio?" dialog and then simply put a button on the colored strip (the one that says Burn CD/DVD) that will open brasero with setting relevant to what you where doing(if you where making an audio cd then open brasero in audio cd mode and auto import all the files that where in the nautilus cd burn dialog.

---

### Post by ronacc on 2008-09-20
why not just install serpentine for her ? its still in the intrepid repos , just not a default .

---

### Post by Bou on 2008-09-21
> **ronacc said:**
> why not just install serpentine for her ? its still in the intrepid repos , just not a default .

Two reasons, basically:

-She still wouldn't get the dialogue asking what kind of CD she wants to burn.
-It's not her I'm worried about, it's the fact that an easy action got overcomplicated by default.

---

### Post by olskar on 2008-09-21
> **Bou said:**
> Two reasons, basically:

-She still wouldn't get the dialogue asking what kind of CD she wants to burn.
-It's not her I'm worried about, it's the fact that an easy action got overcomplicated by default.

Good, I think we must never forget the people who knows less about Ubuntu then we do. It's easy to forget that these minor problems actually are problems for new people because experienced users simply install serpentine.

---

### Post by ronacc on 2008-09-21
agreed , sometimes the devs get too carried away with the "one size fits all" apps and lose sight of ease of use . In you moms case just tell her to stop pirateing music and she won't have the problem :lolflag:

---

### Post by gnomeuser on 2008-09-21
I believe that if you put a blank media in the drive while Banshee is running all you have to do is drag songs to it and hit burn then it does the work. That seems very natural to me, burning a music cd should be done in the context of my media player, but there is naturally room for improvement. Maybe adding an icon for burning a cd when an album is selected in the player and a blank media is in the drive.

---

### Post by Bou on 2008-09-21
> **ronacc said:**
> In you moms case just tell her to stop pirateing music and she won't have the problem :lolflag:

Hey dude, it's legal here in Spain :)

So, what package should I file the bug against? What's responsible for the old dialogue?

---

### Post by ronacc on 2008-09-21
I have no idea what handles that dialogue , just file the bug against "I don't know" and they will sort it out.

---

### Post by Bou on 2008-09-21
Well, I just filed a bug with no specified package: [https://bugs.launchpad.net/ubuntu/+bug/272902](https://bugs.launchpad.net/ubuntu/+bug/272902)

---

### Post by ronacc on 2008-09-21
I did a little investigating and you can set the dialogue to open a blank cd with the program of your choice , expand selections and choose open with other application pick the burner you want (you may have to install it if it is not a default) then check the always perform this action . see attached screenshots .

---

### Post by Bou on 2008-09-21
Hum, it seems you can launch brasero in audio mode with "brasero -a" or data mode with "brasero -d". I guess an easy solution to the problem would be the following:

[[IMG]http://img516.imageshack.us/img516/5800/screenshotblankcdrdiscbp0.th.png[/IMG]](http://img516.imageshack.us/my.php?image=screenshotblankcdrdiscbp0.png)[[IMG]http://img516.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

It's still not as easy as the original dialogue, since the user still has to click the dropdown box to see all the available options. But al least is much more straightforward than what we have now.

What do you think?

---

### Post by ronacc on 2008-09-21
yes thats a good way to do it. I think that overall having a choice of which application to use when you insert a cd/dvd is a good thing rather than just having to accept the default , and you can tell it to perform that action when you insert the next cd without asking , a bit more complicated but also more flexible .

---

