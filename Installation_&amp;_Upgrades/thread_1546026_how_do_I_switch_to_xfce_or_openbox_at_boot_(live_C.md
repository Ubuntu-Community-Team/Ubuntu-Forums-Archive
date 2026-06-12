---
title: "how do I switch to xfce or openbox at boot? (live CD)"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by princerameses on 2010-08-04
Or which environments are installed? Gnome is too big for my older computer. 

I want to switch before the desktop loads, as I am using a live CD.

---

### Post by snowpine on 2010-08-04
[Xubuntu]("http://xubuntu.com") uses the Xfce desktop environment.

Xubuntu system requirements are here: [https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

---

### Post by princerameses on 2010-08-04
Aren't there other's installed? Like openbox or something? 

I do not want whatever is default. Gnome or XFCE or whatever.

---

### Post by snowpine on 2010-08-04
> **princerameses said:**
> Aren't there other's installed? Like openbox or something? 

I do not want whatever is default. Gnome or XFCE or whatever.

There is no official version of Ubuntu with Openbox on the Live CD. Ubuntu has only Gnome; Kubuntu has only KDE; Xubuntu has only Xfce. If you don't want Xfce, why is it in your thread title? ;)

Another option to consider (if you are an intermediate or better user) is a minimal install: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by princerameses on 2010-08-04
*sigh* ok. 

Another question, would you know how to determine which video is being used? in puppy linux 5.0? I get 1024 x 768 in puppy, but in ubuntu*, I do not have that option. (my video card is too old for my monitor, apparently) 

I would like to know what driver is used in puppy, then use it in ubuntu if I can.

---

### Post by snowpine on 2010-08-04
> **princerameses said:**
> Another question, would you know how to determine which video is being used? in puppy linux 5.0? I get 1024 x 768 in puppy, but in linux, I do not have that option. (my video card is too old for my monitor, apparently) 

I would like to know what driver is used in puppy, then use it in ubuntu if I can.

The following terminal command will tell you what kind of graphics card you have:

```
lspci | grep VGA
```

Armed with this information, you can begin to search for answers.

---

### Post by princerameses on 2010-08-04
01:00.0 vga compatible controller: s3 inc. vt8375 [prosavage8 km266/KL266]

Now how do I know what driver it's using, though? 

Or is it telling me in there?

And for minimal install, do you NEED to be connected to the internet? Because I connect to the internet via USB wireless adapter.




speaking of which, any ideas as to why the internet is going slow? (on puppy) (Not sure about ubuntu) In windows it goes pretty fast...

everything else goes fast, though. (windows open virtually instantly, ect.)

---

### Post by snowpine on 2010-08-04
> **princerameses said:**
> 01:00.0 vga compatible controller: s3 inc. vt8375 [prosavage8 km266/KL266]

Now how do I know what driver it's using, though? 

Or is it telling me in there?

I am not personally familiar with this card, however, a quick Search tells me there are many existing discussion threads on the topic for you to read...

The easiest solution may be to pick up an inexpensive supported card like nvidia.

> **princerameses said:**
> And for minimal install, do you NEED to be connected to the internet? Because I connect to the internet via USB wireless adapter.

Yes, you need to be connected to the internet to follow the Pyschocat tutorial I linked to in my previous post. I recommend a wired connection until you are up and running and can configure wireless.


Have you checked your hardware specs against the requirements I linked to in post #2?

---

### Post by princerameses on 2010-08-04
No, but I know I have enough RAM, HD space ect. 

And I was thinking xubuntu used gnome.. because it looks just like ubuntu..

As for getting a new video card, that's what I wanted to do at first, but I really don't want to spend any money on this computer...

There's obviously a way for it to work if it's giving me the correct resolution in puppy. :)

---

