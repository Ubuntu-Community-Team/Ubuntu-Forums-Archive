---
title: "Installing codecs for other use"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by ritterrav on 2007-07-06
Ok, i have a girlfriend who just got a toshiba laptop, and you know to play MP3's when ubuntu's just installed you gotta downlaod the codecs and stuff, but she does not have any internet YET (until she moves to college in months and a half) and i worked hard to dual boot vista and ubuntu, and she is not computer savy and i would like her to get to like Ubuntu, but with out her being able to play her fav songs, she wont give it a shot,. 

Also Ubuntu does not detect her sound card, so even is i got the codecs on there some how i still be in the dark. 

So what im asking is there a way i can download the codecs to play mp3s and what not so i can put them on her computer when i go to visit her? 
Also what can i do with the sound card?

---

### Post by Nonno Bassotto on 2007-07-06
On packages.ubuntu.com you can download the packages for later installation. Be careful to track down dependencies, though, otherwise you will go there and won't be able to install anything because of some missing package...


I think you can do this: use a live CD to have a virgin install of ubuntu, try to install all codecs (you might have add other repositories for this) and copy the list of the packages the system asks to install. I think you basically need:

- everything which starts with gstreamer, except for the dev or dbg or doc packages
- libdvdcss2 (if legal in your country
- maybe flash
- the dependencies of these packages

Then download everything from packages.ubuntu.com and bring all this goodies to your girl.

---

