---
title: "[SOLVED] MPlayer + Codec Installation"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Pandemic187 on 2008-01-13
I know this topic has been covered before, but I am trying to install MPlayer along with the added codecs, but I can't get it to work. I downloaded it via subversion, then attempted to compile it from source, but ./configure produced an error. Can anyone help me with this? I'd really like to completely and totally remove myself from any sort of dependency on Windows.

---

### Post by b0rka7a on 2008-01-13
Go to "Applications > Add/Remove..." and install MPlayer and all GStreamer codecs

---

### Post by zvacet on 2008-01-13
I don´t see reason to compile,but if you feel like it maybe this can help you.First clean up from what you did in that folder 

```
sudo make clean
```

and after that this command can be helpfull

```
auto-apt run ./configure
```

---

### Post by Pandemic187 on 2008-01-13
I solved without really using the terminal. The reason I was trying to do that was because I thought doing so was necessary in order to have all possible codecs, but I simply used add/remove to install MPlayer along with all the available GStreamer codecs.

I just have one more question - is it possible to change which player is used within Firefox? I downloaded the Mozilla plugin for MPlayer, but it still uses Totem. I'm not sure it matters since Totem works as well after I downloaded the codecs, but I'd like to know how to change this regardless.

---

