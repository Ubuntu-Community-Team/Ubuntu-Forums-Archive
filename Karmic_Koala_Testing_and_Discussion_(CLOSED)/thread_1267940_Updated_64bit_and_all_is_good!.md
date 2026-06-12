---
title: "Updated 64bit and all is good!"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-09-16
I didn't update my 64 bit yesterday as I had a 'little' drama on my 32 bit after updating yesterday.
Had about 240 updates and all went smooth and reboot was ok as well.
Hope every one else is getting things sorted out :):)

---

### Post by b3n87 on 2009-09-16
Is there much difference between 64bit and 32bit? Speed wise mainly?

Also does Flash work ok?

---

### Post by dino99 on 2009-09-16
you are lucky, mine still broken (dbus related)

---

### Post by taavikko on 2009-09-16
> **dino99 said:**
> you are lucky, mine still broken (dbus related)

This is why I 
```
devil@core7:~$ uptime ; uname -r
 17:49:52 up 7 days,  1:10,  2 users,  load average: 0.57, 0.23, 0.09
2.6.31-10-generic
```
Won't boot desktop as often during test cycles...

Laptop get's the HC treatment :)

---

### Post by DougieFresh4U on 2009-09-16
Just updated 32 bit installed and rebooted, all was good here. So glad as I don't really need drama today.

---

### Post by madmetal on 2009-09-16
> **b3n87 said:**
> Is there much difference between 64bit and 32bit? Speed wise mainly?

Also does Flash work ok?

I switched from 9.04 32bit with ext3 to 9.10 64bit with ext4 and the performance is much better.

At 64bit i use the Swfdec 0.8.2 plug in cause i don't want to mix my system with 32bit libraries.

Works great except some minor sites , but just using more cpu than in 32bit.

Although Karmic Koala is still in Alpha i am amazed by its stability :)

---

### Post by b3n87 on 2009-09-16
> **madmetal said:**
> I switched from 9.04 32bit with ext3 to 9.10 64bit with ext4 and the performance is much better.

At 64bit i use the Swfdec 0.8.2 plug in cause i don't want to mix my system with 32bit libraries.

Works great except some minor sites , but just using more cpu than in 32bit.

Although Karmic Koala is still in Alpha i am amazed by its stability :)

Are you aware theres a native 64bit ALPHA Flash plugin from Adobe? I thought it was best to use that?

---

### Post by Jim March on 2009-09-16
I'm on 64bit with Intel 965 video.  All is completely usable, bootup still looks pretty funky, some oddball errors, no graphical boot until I get to the KDM login screen.  But again, 100% functional no sweat :).

As to flash: believe it or not, flash now works BEST in 64bit, if you know "the trick".

"The trick" is a dirty trick Adobe is playing.  They've created a 64bit flash player, same version number as the release 32bit, but marked "alpha" when from all we can tell, it isn't.  Apparently they don't want to piss off Apple or Microsoft by releasing Flash64 "officially" for Linux first.  So they've marked working code as alpha - a damned peculiar situation.

Look here for my notes on Flash64:

[http://ubuntuforums.org/showthread.php?t=1241313](http://ubuntuforums.org/showthread.php?t=1241313)

Since I wrote that I've done some more digging and am completely convinced this isn't "alpha" at all.  Worst case it's late beta.  BY FAR the best flash on Linux - and I run Hulu full screen a lot, kind of an acid test.

After all the years of weirdness, if getting solid flash is the goal 64bit is now THE top answer!

As to 64bit in general: I have 2gigs RAM right now.  That's supposedly right on the edge between the faster performance of 64bit code and the increased memory footprint of 64bit.  Below that, esp. a gig or less, you want 32bit for memory savings.  Above 2gig, you should consider 64bit.  Between 3 and 4 gig, you have to run either 64bit or the server kernel.  Past 4gig you need 64bit, period.

Still, with 2gig and 64bit Karmic, I'm seeing no problems at all and would re-install it again under similar circumstances.

---

### Post by madmetal on 2009-09-16
> **b3n87 said:**
> Are you aware theres a native 64bit ALPHA Flash plugin from Adobe? I thought it was best to use that?

I wasn't till now. Thank you and Jim March for the info :)
:KS

---

### Post by benjamimgois on 2009-09-16
Thanks for the tip guys. Now i'm running Jaunty 32bits, recently i installed 4Gigs of RAM on my notebook, but jaunty 32bits only recognise 2,9Gigs. I'm planning to update to Karmic 64bits when it's released on Beta. My only fear was with Flash. But isn't firefox only 32bits ?

---

### Post by andrewabc on 2009-09-16
> **benjamimgois said:**
> Thanks for the tip guys. Now i'm running Jaunty 32bits, recently i installed 4Gigs of RAM on my notebook, but jaunty 32bits only recognise 2,9Gigs. I'm planning to update to Karmic 64bits when it's released on Beta. My only fear was with Flash. But isn't firefox only 32bits ?

I have 3gb ram, using jaunty 64bit. Flash works fine for me. Flash may be 32 bit I don't know or care as long as it is working :P.
I know I've gotten errors while trying to install flash from "add/remove" and it complained not available for my architecture or some crap. So installed from synaptic.

intel g965

---

### Post by Tibuda on 2009-09-17
> **benjamimgois said:**
> Thanks for the tip guys. Now i'm running Jaunty 32bits, recently i installed 4Gigs of RAM on my notebook, but jaunty 32bits only recognise 2,9Gigs. I'm planning to update to Karmic 64bits when it's released on Beta. My only fear was with Flash. But isn't firefox only 32bits ?

Firefox is open source. If Mozilla don't release a 64bits binary, we can just get the source and compile it for 64bit. We can't do that with Flash.

---

