---
title: "horrors of ATI on AIGLX or XGL"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by gothique on 2006-11-09
After updating from dapper, to my surprise X stopped working. After some research I found out that this is because of AIXGL in the new xorg not being compatible with the fglrx driver I need for my ATI X550 card. I also found a workaround by disabling the composite extention,... 

This workaround kind of sucks because it prevents me from using any of the great new features like compiz or beryl. I wanted to give this a try, after all, the several demonstration video's I have seen do look attractive. 

After more research, I found out that I should be able to get it working with Xgl. There were several reports of people getting Xgl to work with an X550 card, so I went and followed [this]("http://forum.beryl-project.org/topic-4863-1.html") howto. 

I rebooted the machine, and Xgl fired up,... and that's about it.
Xgl showed the old gray X grid, with my mouse cursor showing a hourglass. Nothing else happened. Appearantly, it had locked up completely. I couldn't even kill it properly, I had to use the -9 switch to shut it down.

So now, my obious question is, how do I fix it? :)
I googled around all day, and like every good internet citizen, forums are my very last resort. (in addition to IRC, but the Xgl channel was IdleVille)

([here]("http://pastebin.com/820737") is my xorg.conf, by the way.)

---

### Post by Babovand on 2006-11-19
You are not alone , I have the same problem with my radeon 9600XT, Twice!

> Xgl showed the old gray X grid, with my mouse cursor showing a hourglass. Nothing else happened. Appearantly, it had locked up completely. I couldn't even kill it properly, I had to use the -9 switch to shut it down.

same problem. But for me i retured to the console then back to the old gray and then again to the console were it got hanged, i could type but no command worked and i could not use my backup files. so i formed to hole disk. since i don't use dualboot :/

---

### Post by gothique on 2006-12-06
> **Babovand said:**
> 
i could type but no command worked and i could not use my backup files. so i formed to hole disk. since i don't use dualboot :/
Well that's a bit extreme, isn't it? Couldn't you boot with a cd and mount your drive, and fix it?

Anyway, given the numbers of replies (1) to this thread sofar over a period of almost a month now, I take it no one has a solution. Bummer. I guess I'll be waiting for either a new fglrx driver or a new xorg release where the issue is fixed. (or a new xgl release, but I'd rather stick to xorg w/ aixgl)

---

