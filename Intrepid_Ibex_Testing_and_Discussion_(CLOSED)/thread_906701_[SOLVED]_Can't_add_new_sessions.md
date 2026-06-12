---
title: "[SOLVED] Can't add new sessions"
date: 2008-08-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scaine on 2008-08-31
I've just noticed that I can't add any new sessions in Intrepid.  Regardless of what I enter (by typing, or by using "browse"), I just get an error "The Startup command cannot be empty".

I've had a (brief) search on these forums, and a (very brief) search on Launchpad, but nothing looks familiar.

Can anyone confirm this (I'm up to date as of the 30th on a clean install of Intrepid)?

Happy to raise a bug if so, but I suspect it might just be me, although I haven't done a huge amount of customisation on this PC.

---

### Post by autocrosser on 2008-08-31
Yes--I just ran into that this morning...I think a bugreport is in line. If you would, I'll add to it, I'm just in the midst of dinner-making & will be able to in 'bout a hour or so....

---

### Post by autocrosser on 2008-08-31
Checked & there is a current bugreport at: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/262875](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/262875)

I added to it.

---

### Post by Nullack on 2008-08-31
Can you confirm the bug in the confirm status then please

Also this is probably an upstream gnome bug have you had a look at the gnome bugzilla? Extra points for setting up a launchpad bug watch for the upstream bug - you create one if it doesnt exist in the upstream bugzilla. :)

---

### Post by autocrosser on 2008-08-31
Confirmed & reported to Gnome-Bugreport.   Cross-linked between the two.....

[http://bugzilla.gnome.org/show_bug.cgi?id=550140](http://bugzilla.gnome.org/show_bug.cgi?id=550140)

---

### Post by Xgen on 2008-08-31
In the meantime, items can be added through ~/.config/autostart.

---

### Post by autocrosser on 2008-09-01
Noted that this has been fixed upstream.....We should be seeing it soon.

---

### Post by scaine on 2008-09-01
Thanks guys - I went to bed after posting, so it looks like you've done all of the hard work for me!

Is there any point in adding my experience to the launchpad bug then?

---

### Post by autocrosser on 2008-09-01
I would say--not really. The response from Gnome bugzilla:

------- Comment #3 from William Jon McCann  2008-09-01 12:11 UTC -------
Thanks for taking the time to report this bug.
This particular bug has already been reported into our bug tracking system, but
we are happy to tell you that the problem has already been fixed. It should be
solved in the next software version. You may want to check for a software
upgrade.

---

### Post by ildfroe on 2008-09-08
I still have this bug. Hasn't it been fixed here in Ibex-land, or am I missing some updates?

---

### Post by scaine on 2008-09-08
Nope - just tried adding my x11vnc again and it's still broken here too.  I'll try the ~/.config/autostart suggestion from earlier - it's a bit of a pain constantly re-starting my vnc server whenever I reboot.

---

### Post by autocrosser on 2008-09-11
Just updated today--Sessions seems to be working again..edited one of my startups without a problem........

---

