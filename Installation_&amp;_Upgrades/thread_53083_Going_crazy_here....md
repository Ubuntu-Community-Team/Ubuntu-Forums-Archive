---
title: "Going crazy here..."
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2005-07-30
I'm trying ubuntu on the net for the first time, so I figured I'd add the extra repositories and install the real stuff. mp3 support etc. Also, I'm trying to convince a friend to use it, and this is his computer. So far I seem to be convincing myself not to...  :???: 

Uncommented the relevant lines, ran apt-get update and got a screen full of rubbish, which on closer examination was:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'

etc. etc. etc.


if I go to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) I can see the files, so I am connected (otherwise you wouldn't be reading this..) but apt-get can't see anything out there.

Gaim doesn't connect. It doesn't even try. 'Unable to connect almost as soon as I try to.


[COLOR=Red]**Somebody's hammering outside...**[/COLOR]  ](*,) 

Everyone's shouting in here... I need earplugs. 

Those last two aren't linux related, but aren't helping either...

Is there a smiley for 'gun to the head?

chris

---

### Post by heimo on 2005-07-30
Do you use proxy? You could try changing http to ftp.


What does it say, if you type *dig us.archive.ubuntu.com *on terminal?

---

### Post by xmastree on 2005-07-30
[QUOTE=heimo]Do you use proxy?[/QUOTE]Ok, I fixed it now...  :) 

Yes, I was using a proxy, but only for http. So the browser worked but nothing else.

Everything else was using direct connection, which needed DNS, which I hadn't configured...  ](*,) 

The banging has stopped now, too.  :)


Chris

---

