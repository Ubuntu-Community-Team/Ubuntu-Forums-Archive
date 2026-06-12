---
title: "Rhythmbox's lyrics plugin"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by malfist on 2007-09-14
I'm getting Server did not respond to all of rhythmbox's lyrics look-ups. It was working, now it's not. Someone said to uninstall gstreamer0.10-pitfdll and that didn't fix it.

Anyone know what is wrong?

---

### Post by Jasal on 2007-09-15
I'm getting the same error, only noticed it today, Can't think of anything I may have done to cause it.

---

### Post by asakurax on 2007-09-15
same here
kind of annoying...

---

### Post by gali98 on 2007-09-15
maybe the server is just down for a bit.

---

### Post by asakurax on 2007-09-17
bump!

btw: on some songs the plugin does work, but only on like 3 out of 1000 songs...

---

### Post by malfist on 2007-09-18
I think it shows the ones that are already cached.

---

### Post by joel_gil on 2007-09-18
yup... ive been gettin the server things for weeks now...
but until now i started lookin for it. i tohught it was just me...

anyone knows whats goin on?

---

### Post by Blutack on 2007-09-19
Guy with the cached lyrics, could you please let us know the name of the place they come from?  I can't remember exactly.  Still the same problem, could be the API has changed or the organisation providing them has changed.

---

### Post by malfist on 2007-09-19
I think it's pulling it off my harddrive...The only ones I can see are the ones I looked at before the 'server not responding'

when it first started, it would flash the cached (I'm assuming cached) text, then flash Server did not respond, then back to the cached text.

I don't know what is going on, it was just a guess.

edit: nothing is coming through the console.

---

### Post by lupin492 on 2007-09-20
Not trying to get you off-topic, but .. have you tried "Exaile" ?   I find it closer to Amarok than Rhytmbox, and lyrics work well, the same goes for the cover manager, and works with Shoutcast's radios list.
Try and report !
Regards! :popcorn:

---

### Post by asakurax on 2007-09-22
ooo
nice software
lyrics work
thx a lot!

---

### Post by malfist on 2007-09-23
I dug around and found RhythmBox's lyric's source (/usr/lib/rhythmbox/lyrics) and I was looking into the sourcecode, in lyrics.py, line 175 it states:
	url = "http://api.leoslyrics.com/api_search.php?auth=Rhythmbox&artist=%s&songtitle=%s" % (

api.leoslyrics.com doesn't respond in the browser. I'm gonna look around and see if I can fix it. Should I submit this as a bug?

---

### Post by malfist on 2007-09-23
It seems leoslyrics search engine is down and that is what rhythmbox relies upon for it's lyrics plugin. I've e-mail leo and am awaiting a responce.

Anyone on Rhythmbox's dev team here?

---

### Post by malfist on 2007-09-23
Got on IRC, should be fixed in the latest build from SVN.
To get just:
```

svn co http://svn.gnome.org/svn/rhythmbox/trunk rhythmbox

```
and then follow instructions for building and installing.

---

