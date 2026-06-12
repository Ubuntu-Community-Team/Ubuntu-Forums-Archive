---
title: "ltsp server stop sending packet"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by noliuz on 2008-03-22
hi , please help me. 
i installed ltsp on a computer which spec is CPU celeron 2.8Ghz ,Ram 1.5GB. everything 
work fine. but when i used 1 client to play mp3 song and surf the internet with firefox together ,the client computer is freezed. sometimes 20 seconds , 1 minutes or sometimes freeze over. but the server is fine ,nothing error and can do everything with no lag or problem. i used darkstat to sniff the packet that is sent outm from server and found that when the client is freezed the server dont send anything outgoing. i dont know what 's  happen ? need help. 

PS. i'm sorry with my bad english :)

---

### Post by skaber on 2008-05-14
you should use xrestop on the client and verify that there is no local application that overloads the available memory.

I bet you are having a huge amount of memory being used by eiher firefox or pulseaudio. In case it's X, i'm working on lowering the memory consumption in the X server which is mostly due to Firefox.

---

