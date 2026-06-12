---
title: "Command to play a soundfile that automatically closes afterwards"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by li009 on 2007-10-28
I configured my system via "Open With" (MIME) as such, that a click on a soundfile will automatically play that file. In order to do that I placed the line...> alsaplayer -d plughw:1,0 %F
... into the Open With Configuration of mp3- and wav-files. This works quite well except for one thing: Once the soundfile has played to the end, the terminal and the alsaplayer-application does not close automatically. And even worse: The alsaplayer will not accept any further soundfiles!

So if someone knows how to have that alsaplayer (or another player) automatically closed after playing a soundfile, this is the place where it will be highly appreciated :)

---

