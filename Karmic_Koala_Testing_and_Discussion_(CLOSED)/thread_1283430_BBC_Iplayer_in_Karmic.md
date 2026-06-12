---
title: "BBC Iplayer in Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by capnthommo on 2009-10-05
hi
has anybody else been trying to use BBC Iplayers 'listen again' feature in Karmic?  i don't mean the download just the facility to catch up on missed programmes for 7 days from original broadcast.  it works fine using it to live stream radio shows as they happen but wont operate otherwise - no error messages or crash or anything, just sits and does nothing.  i usually have to wait for a while when upgradng before it works or the appropriate plugin, dependency and conflict issues are sorted.
if others are having or have solved this one can they let me know - don't want to file a bug report if it's just the usual lag.
i googled for other threads on the subject but there was nothing remotely recent that i could find.
cheers everybody
capn thommo

---

### Post by capnthommo on 2009-10-06
hi there
just a tiny bump
cheers
thommo

---

### Post by capnthommo on 2009-10-08
once more into the bump dear friends

any thoughts on this one folks?  this always catches me out when i upgrade, is it just wait for it or is there a solution, and i promise to write it down this time
cheers everybody
capn t

---

### Post by barrieluv on 2009-10-08
Sorry, I can only report success with iPlayer.  Listening to Chris Moyle's show from Wednesday without a hitch.

---

### Post by philinux on 2009-10-08
Been working fine for ages. Flash based so have to set processor to performance to use full screen. Does flash work on other sites?

---

### Post by ljrmorgan on 2009-10-08
I'm able to watch and listen to past programs. I'm using Karmic on an AMD64 system with the alpha 64-bit flash.

I think (might be wrong) that the catch up stuff uses flash, whereas the streaming stuff is a real player stream or something. Do you have any problems with any other flash sites??

---

### Post by howefield on 2009-10-08
> **capnthommo said:**
> ..has anybody else been trying to use BBC Iplayers 'listen again' feature in Karmic?...

No issues here with listen again, (Karmic Beta with all updates)

Can you give us a specific link to test, but I'd guess it is more to do with an issue on your side rather than a general problem.

---

### Post by philinux on 2009-10-08
Radio streams are handled via the totem plugin, Watching stream is Flash.

---

### Post by capnthommo on 2009-10-08
hi everybody
i seem to have problems with quite a few streams. this happens every time i upgrade but in the past i have solved it using the tutorial in the stickies.  but this time it doesnt want to play nicely.  it played live stream.
oops, i find that it appears to play past episodes when i go via the bbc home page rather than selecting the i player page so maybe its ok.  ill test further and see.  hopefully the problem will resolve itself.
nice to know that its not a problem with Karmic though - at least it looks as if its just me
cheers
capn t

---

### Post by tuppe666 on 2009-10-08
As it seems to be a feature that nobody is talking about totem can access the programs through totem erm badly.

sudo apt-get install totem-plugins-extra
sudo apt-get install python-feedparser
sudo apt-get install python-beautifulsoup

to get it going

---

