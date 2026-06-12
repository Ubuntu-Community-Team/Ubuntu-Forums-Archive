---
title: "xmms bug report?"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cariboo on 2008-05-29
Is it worth putting in a bug report for xmms. I tried installing it and it says it can't find libglib 1.2 even though it is installed.

Jim

---

### Post by loell on 2008-05-29
its not a bug, its a feature. ;)
theres no xmms from hardy onwards..

---

### Post by 23meg on 2008-05-29
If you didn't install it from the Ubuntu repositories (which you can't with Hardy and Intrepid), don't file a bug report on it in the Ubuntu bug tracker. That applies to all software.

---

### Post by cariboo on 2008-05-29
I know it isn't in the repostories but if enough people but in a bug report or request it, maybe it will get put back in the repositories for intrepid

Jim

---

### Post by loell on 2008-05-29
you mean you wanna file a request for package,

there has been a lot of discussion on why it isn't there anymore, you can search the forum about that.

---

### Post by jlacroix on 2008-05-29
The reason why xmms isn't in the repositories now is because xmms2 is now in the repositories. 

IMHO, xmms2 is a completely worthless, featureless, and terrible excuse for a media player, so don't bother with it. The xmms developers successfully found a way to strip away everything that made xmms good in favor of a commandline player that depends on frontends to provide a GUI, and all of the frontends as of now suck.

I'd recommend to either install xmms from source or install Audacious. To those responsible for removing xmms from the Ubuntu repositories in favor of xmms2, no offense, but how could you and what were you thinking?

---

### Post by 23meg on 2008-05-29
[QUOTE=jlacroix]The reason why xmms isn't in the repositories now is because xmms2 is now in the repositories. [/QUOTE]

No, the reason is that it's been removed from Debian. And the reason why it's been removed from Debian is that it's unmaintained and depends on GTK 1.x, which is due to be removed from Debian too.

[QUOTE=jlacroix]To those responsible for removing xmms from the Ubuntu repositories in favor of xmms2, no offense, but how could you and what were you thinking?[/QUOTE]

Again, it wasn't removed in favor of xmms2. The links below should clarify the situation:

[https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/190684](https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/190684)
[http://people.debian.org/~terpstra/message/20070702.155802.ad2e5b7d.en.html](http://people.debian.org/~terpstra/message/20070702.155802.ad2e5b7d.en.html)

---

### Post by jlacroix on 2008-05-29
> **23meg said:**
> No, the reason is that it's been removed from Debian. And the reason why it's been removed from Debian is that it's unmaintained and depends on GTK 1.x, which is due to be removed from Debian too.



Again, it wasn't removed in favor of xmms2. The links below should clarify the situation:

[https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/190684](https://bugs.launchpad.net/ubuntu/+source/xmms/+bug/190684)
[http://people.debian.org/~terpstra/message/20070702.155802.ad2e5b7d.en.html](http://people.debian.org/~terpstra/message/20070702.155802.ad2e5b7d.en.html)

In that case, I apologize, I had no idea that it depended on GTK 1.x. I'm sorry!

I guess we need a solid replacement for xmms, Audacious comes the closest but not as close as it needs to be. I wonder if there's an easy way to trick it into not depending on GTK 1.x and being okay with GTK2?

---

### Post by amano on 2008-05-29
Audacious is not just close, it IS somehow XMMS, because it is a fork of it. Well they spent some years of development into it, but not every change they made to it was bad hopefully.

---

### Post by talkingwires on 2008-05-29
> **jlacroix said:**
> IMHO, xmms2 is a completely worthless, featureless, and terrible excuse for a media player, so don't bother with it. The xmms developers successfully found a way to strip away everything that made xmms good in favor of a commandline player that depends on frontends to provide a GUI, and all of the frontends as of now suck.He calls it like he sees it, folks!

I would've used the *cheers* icon, but icon selector is apparently broken in 8.04's Firefox. Off to Launchpad, I guess...

---

### Post by disturbedite on 2008-05-30
this is just my opinion, but based on years of experience using xmms, and then years of experience using audacious, i totally disagree with ppl that feel that audacious isn't a drop-in replacement for xmms.

---

### Post by amano on 2008-05-30
From a technical standpoint Audacious IS Xmms because it is a fork.

If you don't like their changes feel free to maintain the original xmms project or create another fork.

That's the beauty of open source. The problem is not an ubuntu one. The xmms project is lacking an active maintainer, thus it was demoted from Debian und Ubuntu and probaly from most other distros.

---

### Post by worldwithoutgurus on 2008-05-30
Hmm... 
Xmms is alive and *still* kicking on Debian Etch. This is one of the many reasons that made me switch from Ubuntu to Debian.

Xmms vs audacious reminds me of vinyl LP vs CD... Audacious is pretty close to xmms but the feeling is not the same (and technically,  the eq-xmms plugin is really cool...).

Ubuntu devs should do something for xmms...

---

### Post by amano on 2008-05-31
no. this is an upstream issue and nothing ubuntu related. 

Somebody needs to step up and start maintaining xmms. Today it is just dead code.

---

### Post by MaX on 2008-05-31
Or just let the old bugger die...

---

### Post by meborc on 2008-05-31
> **MaX said:**
> Or just let the old bugger die...

which is exactly what we are doing by not having it in hardy+

those who can't live without it, please start maintaining it and port it to gtk2

it would make a nice small summer project for someone... but i guess you would end up with something very similar to audacious... 

so... what is that you so much like about xmms that is not available in audacious? got a list ready? OK, then start talking to audacious devs :) or do it yourself... again a nice little summer project

---

### Post by cariboo on 2008-05-31
For me xmms' sound output just feels better than any of the other music players out there. It's one of those things that is hard to explain, it seems to have a richer more fuller sound than audacious. Over the years I've used different music players so its not like I can't change again.

Jim

---

### Post by meborc on 2008-05-31
and both are configured the same way? oss? alsa? pulse-audio?

if equalizer is off, and you are using the same sound systems, then the output should also be the same... :) no?

---

### Post by worldwithoutgurus on 2008-06-01
No.
I'd miss eq-xmms (the builtin equalizer is crap...). The look'n feel is different too.

[http://pourunmondesansgourou.ifrance.com/Images/eq_xmms.png](http://pourunmondesansgourou.ifrance.com/Images/eq_xmms.png)

@ cariboo907
I agree with you, it's *not* the same feeling.

---

### Post by amano on 2008-06-01
A software equalizer ***** up your sound output in any way. It is a shame that people still think that they can "improve" sounds by applying some obscure algorithms over it.

A good link to uncover all those myths is: [http://www.hydrogenaudio.org](http://www.hydrogenaudio.org)

---

### Post by ssokolow on 2008-06-06
> **worldwithoutgurus said:**
> Xmms vs audacious reminds me of vinyl LP vs CD

Same. Like LPs, XMMS is fragile and, just like with the "warmer sound of analog amps" (really a distortion that could be applied digitally), some people swear by it.

---

