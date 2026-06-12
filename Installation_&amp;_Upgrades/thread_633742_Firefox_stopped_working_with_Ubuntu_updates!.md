---
title: "Firefox stopped working with Ubuntu updates!"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2007-12-06
Hi.  I'm a new user to Ubuntu, ruin the 64-bit version on an AMD dual-core 5GHz+ machine with 2GB of RAM.

I installed all the recommended update for Ubuntu, and now Firefox isn't working properly.  When I tried to add the flashblocker add-on, I got the following message:

[img]http://i4.photobucket.com/albums/y122/darkeyes_lewj/Screenshot.png[/img]

What do I need to uninstall, and how do I do it?

---

### Post by mouseboyx on 2007-12-06
Has flashblock always worked before?
```

sudo apt-get remove --purge firefox

sudo apt-get install firefox

```

---

### Post by MQMike on 2007-12-06
IMHO, this is the way to go, all the way:

Firefox (latest), Thunderbird (latest):   [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

(have a look at their explanation of what they do and why)

---

### Post by lewisskinner on 2007-12-06
> **mouseboyx said:**
> Has flashblock always worked before?
I got flashblock for Firefox on Vista and it worked, and I had flashblock on on Ubuntu before, but have since done a clean install.

I then downloaded the updates, and loaded a website with a flash animation I didn't want, and I realised I'd forgotten to add flashblock, but when I tried, I got the above message

> **mouseboyx said:**
> ```

sudo apt-get remove --purge firefox

sudo apt-get install firefox

```
That didn't work

---

