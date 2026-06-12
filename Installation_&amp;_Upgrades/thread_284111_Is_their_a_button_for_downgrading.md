---
title: "Is their a button for downgrading?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by J77 on 2006-10-25
Further to my most recent posts, I'm in the process of backing up my home directory with the purpose of reinstlling Breezy (from DVD) in the place of 6.06LTS.

Is there a "downgrade" button which will allow me to do this?

Or do I have to reinstall from DVD?

eta: I can't believe I mispelt "there" ](*,)

---

### Post by .t. on 2006-10-25
Don't think so... Why do you want to downgrade? I haven't seen your "most recent posts". Also, when you do reinstall, create a separate partition for /home. That way you won't need to spend time in future backing things up.

---

### Post by J77 on 2006-10-25
xserver problems with 6.06lts (dapper) when breezy worked fine - I've read the threads about downgrading the xserver and have done with no joy.

I have two separate home partitions but backed up on another server for safety purposes.

---

### Post by Jussi Kukkonen on 2006-10-25
Downgrading is not officially possible (some adventorous people have done it, Google for *Debian downgrade*), sorry.

Another option is to try 6.10 -- it'll be released any day now. Using Breezy is not a long time solution because the security fixes will stop in six months...

---

### Post by frodon on 2006-10-25
Edgy wil lbe release in few days now, maybe you could try it intead of reinstalling breezy.
And the release candidate of edgy is already available.
However it's always a good practice to create a ghost image of your ubuntu partition before any upgrade or just when your install is fine thus you never need a reinstall.

---

### Post by J77 on 2006-10-25
OK - thanks for the replies.

How does one create a ghost image; what should I be creating an image of; and how would I use this image?

---

### Post by frodon on 2006-10-25
There's plenty of useful tools to create a ghost image.

Basically you create a ghost of your ubuntu partition, it will give you an archive file (.gz, .bz2 or whatever you want), concider that as if you take photo, a snapshot of your partition. Then when you brake your install or when you want to come back in the same configuration than when you did the ghost image, you just overwrite your ubuntu partition with your ghost image and you get the same thing than when you did the image in 5 minutes.

Most common and easy to use apps to do that is partimage :
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

It's in the repositories and the link to the website i provided you give you all the needed documentation to know how it works.

---

