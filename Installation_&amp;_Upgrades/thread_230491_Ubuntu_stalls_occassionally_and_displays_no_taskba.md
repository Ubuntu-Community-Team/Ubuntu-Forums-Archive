---
title: "Ubuntu stalls occassionally and displays no taskbar"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by sovin on 2006-08-06
I recently upgraded to dapper drake from breezy badger on my compaq presario 2700. about 3 days after using dapper drake my computer would occassionally stall completely, requiring a hard reboot in order to continue.. 

also, the bottom 'bar' does not display the window's i have open. could anyone please help me with this?

---

### Post by _simon_ on 2006-08-06
Probably a dumb question but if it's not displaying winodws you have open, are you sure you have the "Windows List" added to the panel?

I guess you know how as you've used Ubuntu before but just in case you don't...

Right click on your panel (bottom bar) and select "Add to panel" select "Window List" and press ok.

As for you first problem this sounds similar to what my other half was experiencing. I am not sure how I fixed it but I was setting up XGL + Compiz for her. After adding the following repos to her sources lists a few things updated and the problem was fixed.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

Maybe worth a try just adding them.

```

sudo gedit /etc/apt/sources.list

```

Just add them to the bottom and press save then run your update manager and press CHECK.

Don't worry it won't install XGL or anything but if there are any updates to software already installed then those will display.

---

### Post by sovin on 2006-08-07
Thanks for the reply. The window listing problem was pretty foolish of me. Turns out I somehow moved the bar to hide the window's behind the trash can.

I'm still stalling at random times without notice. I followed the steps you gave me but I haven't experienced any difference in their uncanny timing (they seem to always catch me just as i'm finsihing a document). I've stalled twice while writing this very reply.

I've noticed that many of the freezes come when i'm opening or closing a tab in firefox. Could this give any hint as to the cause of the problem + a fix to it?

---

### Post by sovin on 2006-08-12
-bump

---

### Post by sovin on 2006-08-17
-bump

---

### Post by missingxtension on 2006-10-25
-bumb
but with some more info 
it says panel detected already running 
can n e 1 tell me where to delete the file from so it wont think its already open?

---

