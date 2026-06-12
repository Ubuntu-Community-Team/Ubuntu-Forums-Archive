---
title: "roll back VLC to older version"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-09-28
When VLC did an update, it can no longer capture a stream from my v4l2 capture card.

Mplayer can still capture the stream.

Where can I get the older version?

---

### Post by moviemaniac on 2009-09-28
There should be an old version in your /var/cache/apt/archives

---

### Post by sdowney717 on 2009-09-28
Thank you!
that fixed the problem completely.
there are 6 vlc related files you need 
I copied them into a folder
removed the bad version 
then ran 
sudo dpkg -i *.deb in that folder from terminal

And it is all working! vlc 1.01 works, vlc 1.02 does dont work

---

### Post by andrewabc on 2009-09-28
Maybe file a bug so it might get fixed for future releases?
That way if it doesn't get fixed you can complain without people asking why no bug filed :)

---

### Post by sdowney717 on 2009-09-28
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/438211](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/438211)
ok , i gave it a try.

---

### Post by andrewabc on 2009-09-28
For future reference it is 1.0.2 and 1.0.1 you are missing a "."
Using correct number schemes should make it easier for people to find (example, I press ctrl+f in firefox and search for 1.0.2, 1.02 will not show up).

---

