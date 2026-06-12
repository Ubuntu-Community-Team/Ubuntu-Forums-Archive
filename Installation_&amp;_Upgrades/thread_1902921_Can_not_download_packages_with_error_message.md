---
title: "Can not download packages with error message"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by bigtel on 2012-01-01
Happy new year to everyone.

I am constantly having problems with package and upgrade downloads, and I really am banging my head against the wall now. I have manage to get around this issue in the past by using synaptic or downloading updates one at a time (very time consuming) but for anything that is a few MB in size I can not get a good download.

Can anyone tell me what is wrong? Here is my latest output error


```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_9.0.1+build1-0ubuntu0.11.10.2_i386.deb
  Hash Sum mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-dbg_9.0.1+build1-0ubuntu0.11.10.2_i386.deb
  Hash Sum mismatch

```


I have tried changing repository, to no avail.!

Is there a way of testing the 'quality' of my Internet connection? Could it be the package files are being corrupted somehow? Who knows..!!

---

### Post by Paddy Landau on 2012-01-01
It certainly does sound like an Internet connection problem.

Try this:

Open Software Sources > Ubuntu Software > Download from > Other > Select Best Server.
Give it time to test and decide.
Reload.
Try your updates again.

I can't promise that this will help, but let's hope.

---

### Post by bigtel on 2012-01-01
Hmmm..

When I click on 'other' it just sits there, it does not ask me to choose a server or anything. I am sure it has worked previously, but not now for some reason. It gives me only choices of main server and United Kingdom.

---

### Post by BlueSunshine on 2012-01-02
I have this same problem as well. When I try to check for a server, it gives me the same error message when I try to use Update Manager. I'm using 11.10 as well.

---

### Post by Paddy Landau on 2012-01-02
> **bigtel said:**
> When I click on 'other' it just sits there...
Did you press "Select Best Server"?

---

