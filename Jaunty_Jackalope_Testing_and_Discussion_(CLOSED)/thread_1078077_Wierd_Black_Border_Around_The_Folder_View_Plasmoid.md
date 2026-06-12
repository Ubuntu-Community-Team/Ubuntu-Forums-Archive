---
title: "Wierd Black Border Around The Folder View Plasmoid"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-02-22
There is a strange black border around my folder view widget on my desktop. I've set everything to default and even tried removing and replacing the widget. I've change the theme to something else and then back to Oxygen. Please check the screenshot to see what I mean.

---

### Post by sweleys on 2009-02-23
I have had the problem since a few days ago when there was a kde update.

---

### Post by ruik on 2009-02-23
Same here.

---

### Post by RIchard James13 on 2009-02-23
Easy solution use a black background :)

More complicated solution might be to delete you plasmoid settings file.

the file is in ~/.kde/share/config/ and is either 
plasmarc 
or 
plasma-appletsrc

I can't guarantee that will work but it might be worth a try. Note after doing that you have to re-add all your plasma widgets.

---

### Post by zenarcher on 2009-02-23
I'm also having the same problem here.

Cheers,
zenarcher

---

### Post by kde4-core-user on 2009-02-23
Jaunty has updated to Qt 4.5 RC yesterday. These plasma-errors are well known, I hope they will be quickly resolved.

For me it is not only the folderview, I can also see in other plasmoids, mhh ..."faulty lines", which look disgusting too! :-(

---

### Post by nferenc on 2009-02-23
Same problem here.

---

### Post by jlacroix on 2009-02-23
I'm glad I'm not the only one.

QT 4.5 is supposed to fix the system tray glitches, so as long as it doesn't cause breakage with the final release, I'm happy.

---

### Post by inportb on 2009-02-23
Well, it does fix the tray glitches. It does not fix the GTK+ glitches, though =p

---

### Post by halfsane on 2009-02-23
My folder view is set to Desktop and it is not showing all of the files in my desktop folder (I can access all of them through the file browser).


Anyone else?

---

### Post by kde4-core-user on 2009-02-24
> **halfsane said:**
> My folder view is set to Desktop and it is not showing all of the files in my desktop folder (I can access all of them through the file browser).

Maybe, you have the filter enabled?

Folder View Settings > Filter > “Show all files”

---

### Post by RIchard James13 on 2009-02-24
Yay I get to join the black border club. I didn't have the black borders but my plasma was playing up so I deleted the plasma config files. Now I have the black borders and my plasma is not fixed. Randomly some widgets are not displaying. If I mouse over them they come back then they disappear if you mouse over some other widget. Actually I believe the activity bar widget is the culprit as removing it removes the problem and adding it makes the widgets disappear.

The other thing the activity bar does is removes the background from the notification tray.

I have one thing to say about KDE 4.2 and that is at least it looks trendy when it stuffs up

*EDIT*

Do we have a bug report filed against this bug?

---

### Post by jlacroix on 2009-02-24
I was just about to ask that too. Is there a bug about it? I'll file one if not and then link to it here.

---

### Post by ruik on 2009-02-24
Go ahead! :)

---

### Post by Hospadar on 2009-02-24
looks like these problems are a known issue
[http://aseigo.blogspot.com/2009/02/plasma-qt-45-tokamak-etc.html](http://aseigo.blogspot.com/2009/02/plasma-qt-45-tokamak-etc.html)

---

### Post by jlacroix on 2009-02-24
I'll post the bug report this evening. :)

---

### Post by jlacroix on 2009-02-24
It looks like there is already a bug report about this:
[https://bugs.launchpad.net/ubuntu/+bug/333842](https://bugs.launchpad.net/ubuntu/+bug/333842)

If you are having this problem and have time, please comment on it so they will know it's not just a isolated incident.

---

### Post by Mazza558 on 2009-02-24
Does the update to QT 4.5 explain the improved performance I've been noticing?

---

### Post by jlacroix on 2009-02-25
*BUMP*

If you're a victim of this bug, please comment on the bug report.

---

### Post by RIchard James13 on 2009-02-26
*** BUMP ***

Please add a comment to the bug report. At the moment there are only four people confirming this bug. If we can get that number to ten then they will take more notice of it.

---

### Post by taavikko on 2009-02-26
> **RIchard James13 said:**
> *** BUMP ***

Please add a comment to the bug report. At the moment there are only four people confirming this bug. If we can get that number to ten then they will take more notice of it.

There's no need to confirm it anymore.
That just creates poor signal/noise ratio.

Click "affects me too" button.
Or change the status of the bug to "confirmed" If your affected also.

---

### Post by RIchard James13 on 2009-03-07
With the latest KDE 4.2.1 this no longer appears.

---

