---
title: "vista won't recognize ubuntu live cd"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by satrapes on 2012-08-14
Hey has anyone else had the problem where you download and burn a ubuntu live cd and you can't open it in windows vista? The weird part is that in another computer that runs windows xp it shows perfectly.

---

### Post by darkod on 2012-08-14
Why would you want to open it in windows vista anyway? You need to boot your computer with it, not open it inside windows.

You might have some security settings in vista preventing it to run, etc.

---

### Post by kurt18947 on 2012-08-14
> **darkod said:**
> Why would you want to open it in windows vista anyway? You need to boot your computer with it, not open it inside windows.

You might have some security settings in vista preventing it to run, etc.

I was having the same question unless Satrapes was trying to set up WUBI.  If hardware will support it,  Win 7 (don't have Vista) runs very nicely as a guest in Virtual Box.  The two O.S.s  each with an office suite open used a bit less than 1 Gig RAM.

---

### Post by darkod on 2012-08-14
> **kurt18947 said:**
> I was having the same question unless Satrapes was trying to set up WUBI.  If hardware will support it,  Win 7 (don't have Vista) runs very nicely as a guest in Virtual Box.  The two O.S.s  each with an office suite open used a bit less than 1 Gig RAM.

Even in that case you are doing it wrong. Using the whole cd for only wubi.exe is a waste, a big one.

First you need to download the image, burn the cd, open it in your windows and click the wubi.exe which will start downloading everything all over again.... :)

In that case simply download the wubi.exe and start it, not the whole ISO.

Alternatively, extract the wubi.exe from the downloaded ISO without burning it on a cd, put the ISO and the wubi.exe in a same folder and start wubi.exe. In that case it will use the ISO without downloading again.

And after all of this said, my recommendation not to use wubi at all. Use proper dual boot instead. Wubi is a quick try (and you can do the same with the cd in live mode), not a long term install as many people try to use it. Expect problems if you plan to keep it long time.

---

### Post by satrapes on 2012-08-15
Guys i am really sorry for your troubles. As it turns out my cd/dvd drive is malfunctioning somehow and it has (i think) nothing to do with the operating system. My cd recognizes what kind of cd it is but doesn't read any data it says 0 bytes even though it is written. Anyhoo i did it with a usb drive, so i am going to tag it as solved.

---

