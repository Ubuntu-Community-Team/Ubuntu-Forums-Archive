---
title: "Does Rhythmbox Rip Audio CDs for you?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Teamgeist on 2009-09-22
The title sais it all.
Whenever I try to rip an audio Cd to MP3 it gives me these errors:

```
could not create source element for 'cdda://1#/dev/sr0' 
```

and
```
Unable to locate encoding profile for mime-type 
```

Can anybody confirm this?
I did not find a bug report on [www.launchpad.net](www.launchpad.net)

---

### Post by Longinus00 on 2009-09-22
I actually got this same problem the other day. I was in a hurry so I forgot about it. They won't rip in soundjuicer either but I'm almost certain that it uses the same underlying api as rhythmbox.

---

### Post by gordintoronto on 2009-09-22
Did you install the Restricted Extras?  What format were you ripping to?

My preference is to use Sound Juicer, and extract to FLAC format.  It's lossless but somewhat compressed.

---

### Post by Longinus00 on 2009-09-22
> **gordintoronto said:**
> Did you install the Restricted Extras?  What format were you ripping to?

My preference is to use Sound Juicer, and extract to FLAC format.  It's lossless but somewhat compressed.

I have installed restricted extras. Just like the thread starter I had a problem ripping into MP3 format.

---

### Post by Teamgeist on 2009-09-22
Restricted-extras are installed. So is lame and everything else needed.

Sound-Juicer rips just fine for me btw.

This seems to be it:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/431027](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/431027)

Fix is supposed to be in sight. We'll see...

---

