---
title: "Problems installing onedrive"
date: 2017-01-24
forum: Installation &amp; Upgrades
---

### Post by anbu-s on 2017-01-24
I've tried to install onedrive sync from [https://github.com/xybu/onedrive-d-old](https://github.com/xybu/onedrive-d-old)

After installing, when i type onedrive-pref, it says no config file exists. during isntallation it asked for onedrive sign-in info, which i've copied and pasted it from the browser.

I see a onedrive folder in my home directory, but the content is not there. Can someone post me step by step installation of onedrive for ubuntu 16.04?

---

### Post by howefield on 2017-01-24
> **anbu-s said:**
> I've tried to install onedrive sync from [https://github.com/xybu/onedrive-d-old](https://github.com/xybu/onedrive-d-old)

After installing, when i type onedrive-pref, it says no config file exists. during isntallation it asked for onedrive sign-in info, which i've copied and pasted it from the browser.

I see a onedrive folder in my home directory, but the content is not there. Can someone post me step by step installation of onedrive for ubuntu 16.04?

That's odd because it doesn't ask for sign in information until you call up onedrive-pref.

What is the output of ...

```
onedrive-d status
```

By the way, as far as I can tell this is not being currently developed and has been that way for some time.

---

### Post by alejandrofig on 2017-05-06
Hello, i have also install onedrive, and I see all may files, but i notice that they do not sync, If i upload something then i can't find it in my folder, and also the other way around, if i save something on my folder I don't see it online. I follow the command onedrive-d status and this is the result:
Loading configuration ... OK
[2017-05-06 18:41:32,336] DEBUG: MainThread: running in daemon node.
onedrive-d -- pid: 2678, status: sleeping, uptime: 8m, %cpu: 0.0, %mem: 0.6

Does one drive takes a lot of time to sync????

---

### Post by howefield on 2017-05-07
The sync should be pretty much instant once you start onedrive with

```
onedrive-d start
```

You posted around 20 hours ago, do you still have the issue ?

---

### Post by mastablasta on 2017-05-08
> **howefield said:**
> 
By the way, as far as I can tell this is not being currently developed and has been that way for some time.

partially true.

there is onedrive-d-old : [https://github.com/xybu/onedrive-d-old](https://github.com/xybu/onedrive-d-old)

this one had development stopped 2 years ago, but it might still work.

and then there is the onedrived-dev:
[https://github.com/xybu/onedrived-dev](https://github.com/xybu/onedrived-dev)

which looks like it is under development.

by the way, while i haven't tried any of the linux drive cleints, i would sometimes get this issue at work on our business one drive account on win10. sometimes there it can also be solved by checkign it the sync already started and it it hasn't, to give it a little nudge. might be something similar here.

---

