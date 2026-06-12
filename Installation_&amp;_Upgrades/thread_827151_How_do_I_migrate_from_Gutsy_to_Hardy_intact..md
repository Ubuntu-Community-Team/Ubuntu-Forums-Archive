---
title: "How do I migrate from Gutsy to Hardy intact."
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by skew on 2008-06-12
I recently received my Hardy CD in the mail and would like some guidance on how best to install it. FWIW, I would have just downloaded the ISO but where I live there is only dialup available(56k). YA, I know, it really sucks only having dialup!  Anyway, I digress...

  Although I'm currently running Gutsy, and have it the pretty well the way I like it, I'd like to start taking advantage of some of the improvements available in Hardy.  So, how can I install Hardy and transfer my current setup over? I have enough space on my drive to make a separate partition for ver 8.04 without having to touch my current setup, if that'll make it easier.  In the past when I upgraded I did so from scratch, basically starting over from zero, reinstalling the programs I wanted, setting up compiz, etc. That always seemed to be a colossal waste of time. I appreciate that I may have to do some of those things but I assume that there must be some way I can lessen this time consuming chore.  

So, is there some way of transferring over at least some of what I've got  from Gutsy?  Configuration, bookmarks at least?  Ya I am kidding about the bookmarks. 
      
I just want to know if it's even possible, and if so what's the best way to do it. Or, am I asking for the sun, moon and stars here?  

Thanks

---

### Post by avtolle on 2008-06-12
I'd suggest making a separate home partition, as more fully and clearly set out in the link. That should be of help in preserving the settings, etc. 
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
Then, install your new 8.04 to the / partition (don't touch /home, obviously); I'd reformat it before installing to it.

Otherwise, back up your home folder onto external media, and, once installed, restore by copying over the old stuff. Hopefully this will work well, too.

---

### Post by snowpine on 2008-06-12
Hi Skew, it is too bad you don't have faster internet. All you would need to do is go to the Update Manager and click the "Upgrade to 8.04" link. This will keep all of your settings and data intact. You could try it, but it would take a loooooong time at 56k! :)

Avtolle's suggestion about setting up a separate home partition is a good one, too. The only disadvantage to installing Hardy from the CD is that Hardy is so new, there are important updates coming out every day.

---

### Post by avtolle on 2008-06-12
Yeah, and at 56k, these would take a long time as well. Is there any broadband hookup you can access? I'm thinking about Apt on CD, which as I recall, would let you (or someone on your behalf) d/l the updates, where they could be written to a CD, and then you could upgrade from the CD. I've only been reading about this, and no experience with it, but I'm aware it is out there.

---

### Post by skew on 2008-06-12
Thanks for responding guys.  

  Unfortunately some of us here in Canada are being left to rot in the dark ages, abandoned by both our government and the telcos. We're too far away from the big cities and too separated from each other to warrant even a second glance when it comes to providing us peasants with high bandwidth connections. The only alternative (satellite) is outrageously expensive.   Okay, I'll get off my soapbox now.

The simple answer is no.  I have no way of getting access to a high bandwidth connection. And yes you can weep for me, I do it often enough. Especially when I consider what I'm missing out on.  Or you can laugh, like Ralph on the Simpsons, I actually get that more then sympathy.   Damn this soapbox is high, you can see for miles from up here. ;-)

All kidding and bitterness aside...  

  I'll wait a couple of days and see if i get anymore bites on this tread, The separate home partion idea does make sense though, I should have figured that one out on my own, duh! 

Thanks again for the help guys.

---

### Post by snowpine on 2008-06-12
> **skew said:**
>   Or you can laugh, like Ralph on the Simpsons, I actually get that more then sympathy.

HA-ha!!! :)

Seriously, if I were you, here is what I would do. Since you have a stable install of Gutsy that is set up just the way you like it, keep it! Move your home directory to a new partition. And then set up a third partition for Hardy. Spend some time with it and make sure it is stable and it does what you need it to do before you get rid of Gutsy. Are there specific features of Hardy you are interested in, or do you just want it because it is "new and improved"?

ps if you don't have the space for all those partitions, you can back up your entire Gutsy partition to an external hard drive as a disk image (let me know if you need instructions), then in case Hardy doesn't work out for you, you can put it back exactly the way it was.

Edit: This thread will tell you how to back everything up: [http://ubuntuforums.org/showthread.php?t=825680](http://ubuntuforums.org/showthread.php?t=825680)

---

### Post by skew on 2008-06-12
> **snowpine said:**
> HA-ha!!! :)


Et tu, Brute? I mean snowtree,..er pine..  sheesh... ;-)

Okay great! I'll check out your link and consider my options. 

   If do I go the ext HD route, I will take you up on your offer of assistance. Never did have much luck with that whole disk imaging thing in the past. The last time I tried doing something similar I came across errors with locks, or was it links symbolic or imagined, I can't quite remember anymore. 

Anyway thanks! I'll check back in tomorrow.

---

