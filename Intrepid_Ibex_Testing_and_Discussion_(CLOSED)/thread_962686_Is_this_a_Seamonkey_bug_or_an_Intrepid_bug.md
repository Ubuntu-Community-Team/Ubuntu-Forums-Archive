---
title: "Is this a Seamonkey bug or an Intrepid bug?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PierreDeKat on 2008-10-29
I'm running Seamonkey 1.1.12, installed from Intrepid's repositories. And I have been experiencing some really unusual behavior.

In the first screenshot -- see below -- Seamonkey is essentially telling me that it is having troubles with my profile directory. 

It's weird, because I can be sailing along with no troubles, and then I get this message, doing nothing particularly out of the ordinary.

So, the first time I got this message, I did: 

```
sudo chown -R pierre:pierre /home/pierre/.mozilla
sudo chmod -R 755 /home/pierre/.mozilla
```

Hoping that this would clear up any read/write permission problems, but I am still getting this same message from time to time, again, doing nothing particularly out of the ordinary.

The second screen shot is telling me that it cannot connect to a particular webpage because I supposedly have SSL disabled. The trouble is, I *don't* have SSL disabled.

In fact, 9 times out of 10, I have no trouble whatsoever perusing SSL webpages. It's just that 1 time in 10 when Seamonkey thinks I have SSL disabled.

It's really quirky how most of the time, I have no trouble. But then, just out of the blue, Seamonkey starts acting up.

So I've been closing Seamonkey and restarting it, and that fixes things for awhile, right up until the next time I have trouble.

Anybody seen anything like this in any bug reports?

TIA

---

