---
title: "Dell Mini 9, Jaunty netbook image, and WPA"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by brimlar on 2009-04-10
Hello there.  I'm sorry to post about this because it seems there are a lot of threads out there, but I haven't been able to find one that works for my situation.

I have installed the daily Jaunty netbook remix image onto my Dell Mini 9 (because I was tired of the Dell remix), and it seems that it can't connect to WPA networks.

Now, when I was using Dell's remix (their 8.04 remix), wireless worked 80% of the time, but once in a while you did have the system lock up while trying to connect to the network.

I've tried downloading the Broadcom drivers from their website, patching them -- and that didn't work, it seems.  I also tried disabling and re-enabling the driver in Hardware Drivers -- no luck.

I'm going on vacation soon and I'd like to get Jaunty working because it is very slick (and fast)...if anyone could offer me some assistance with this, I'd greatly appreciate it.

---

### Post by armandh on 2009-04-10
try 8.10 until the kinks are ironed out or try WPA2 which seems to work OK on 8.10

---

### Post by brimlar on 2009-04-10
I kind of figured there would be kinks with the Jaunty image still...but I was hoping it was close enough to release date to be mostly okay.

So, I'm going to install the 8.10 version and I'll report back here on how it works.

---

### Post by brimlar on 2009-04-10
Looks like people are encountering a bunch of weird wireless issues such as this: [https://bugs.launchpad.net/dell-mini/+bug/300784](https://bugs.launchpad.net/dell-mini/+bug/300784)

---

### Post by buzzware on 2009-04-10
I am able to use WPA2 PSK w/ TKIP, but there is a small problem when wireless starts.  The authentication times out several times, then I'm presented with an already-populated box for encryption type and pass phrase.  Once I click OK, it connects.

My router accepts up to AES.  Dell's 8.04 allowed me to set TKIP instead of auto or AES, which helped because neither of the other modes would authenticate.  I think that's why I'm having a problem now - auto being the only option.

---

### Post by brimlar on 2009-04-13
There's some weirdness going on with the wireless driver that I unfortunately don't have time to properly troubleshoot at this time (due to the coming vacation.)  I've put XP (ugh) back on the Mini 9 for the time being.

I'm going to retry the Jaunty netbook image when it's no longer a pre-release and I'll update this thread.

However, if other people have experiences they'd like to add here, feel free to do so in the time being.

PS - I have also been using TKIP compression on my WPA-PSK wireless network.  It seems that TKIP is another noted part of the problems with this driver at the moment.

---

