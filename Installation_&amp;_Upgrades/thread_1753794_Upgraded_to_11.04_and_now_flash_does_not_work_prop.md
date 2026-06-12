---
title: "Upgraded to 11.04 and now flash does not work properly :@"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by CARTER141 on 2011-05-09
I upgraded Sunday to 11.04 from 10.10. Now websites do not display flash correctly. Youtube so far is the only flash site that works as it should. I tried the latest download and install of Flash, but still no joy, any ideas?

---

### Post by Royke on 2011-05-09
Hello CARTER141 


About the same thing here but it also didn't work on my 10.10 before. But this is only with firefox. On another browser it works ok! The funny thing is that i saw it doesn't work properly on windows(vista) with firefox too. The same flickering and uncomplete images as on Ubuntu11.04. I still have 10.04 on my machine too and flash works ok on it.

After some search i saw that at least Mozilla is doïng what they can about it. I really hope for a fully working open-variant of flash some day, when even myspaceplayers can be handled correctly, or are we there yet?

---

### Post by collisionystm on 2011-05-09
> **Royke said:**
> Hello CARTER141 


About the same thing here but it also didn't work on my 10.10 before. But this is only with firefox. On another browser it works ok! The funny thing is that i saw it doesn't work properly on windows(vista) with firefox too. The same flickering and uncomplete images as on Ubuntu11.04. I still have 10.04 on my machine too and flash works ok on it.

After some search i saw that at least Mozilla is doïng what they can about it. I really hope for a fully working open-variant of flash some day, when even myspaceplayers can be handled correctly, or are we there yet?


Install Flashaid from the firefox addons. OR

If you want to do it yourself ;) you can...

download Flashplayer 64 from here 

[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

Flash 32 ... 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

You want the Linux .tar.gz

Download the file, open it with Archive Manager

Extract the libflashplayer.so file inside to your desktop

Open terminal

```
cd Desktop
``````
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/
```Restart Firefox. VOILA!  You are now rocking with updated Flash.

---

### Post by CARTER141 on 2011-05-10
Hey guys, thanks for the replies.

I decided I wasn't too keen on 11.04, having only recently come to Ubuntu so have reinstalled 10.10 LTS for now, which works no issues found (touch wood)

---

