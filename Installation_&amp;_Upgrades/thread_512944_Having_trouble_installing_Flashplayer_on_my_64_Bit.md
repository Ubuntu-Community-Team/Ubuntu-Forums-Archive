---
title: "Having trouble installing Flashplayer on my 64 Bit Pentium D (part II)"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by BEMoorein84 on 2007-07-29
I am a beginner. The directions I was given confused me: [http://ubuntuforums.org/showthread.p...1727&highlight](http://ubuntuforums.org/showthread.p...1727&highlight). I understand that there is some problem with installing the video software on a 64 Bit system (Firefox is 32 Bit?). I have Feisty Fawn-Ubuntu. I go to Applications--> Add/Remove--> and I try to check  Macromedia Flash plugin, but I can't check it. I can highlight it (orange), but I can't check it. Is this a sign of my problems or is this my problem? Any assistance for a desperate beginner????????????

---

### Post by kidders on 2007-07-31
Hi there,

Unfortunately, the link you posted doesn't point anywhere useful.

The problem you're having has to do with the fact that a small number of companies refuse to release (or allow somebody *else* to release) 64-bit versions of their software. Browser plugins are a case in point. Consequently, many web browser companies (eg Opera) don't bother releasing 64-bit versions at all, which in turn makes plugin providers reluctant to do so ... and around we go hehe.

As 64-bit processor owners, the first decision we have to make is between 64-bit purity and a sort of a hybrid, where some things work using our native bitness, and others use emulated 32-bit operation.

**Pure 64-bit operation**[LIST]
[*][COLOR=DarkGreen]Easy on the brain, because you only have one set of system libraries, and one version of all your software.[/COLOR]
[*][COLOR=DarkGreen]"Cleaner" ... but that's only important to militant proponents of the 64-bit architecture.[/COLOR]
[*][COLOR=DarkRed]Can be a little buggy, since you'd be relying on hacky, badly maintained or reverse-engineered versions of things like RealPlayer support.[/COLOR][/LIST]**Hybrid operation**[LIST]
[*][COLOR=DarkRed]More complicated, since many system libraries are duplicated, and you may have more than one version of some software.[/COLOR]
[*][COLOR=DarkRed]A bit "inelegant" ... but 99% of people honestly couldn't care less.[/COLOR]
[*][COLOR=DarkGreen]Relatively bug-free, since official 32-bit versions of applications run side by side with your 64-bit stuff.[/COLOR][/LIST]Although I try different things from one install to the next, at this very moment, I've opted for a hybrid approach. This means that most of my applications (eg Java, MPEG decoders, and so on) are 64-bit ... but my browsers are 32-bit ... so they won't talk to each other. Consequently ...[LIST]
[*]Taking Java as an example, I've had to install 32-bit duplicates of its browser plugins, and defeat my "proper" Java's attempts to integrate with my browsers.
[*]Conversely, support for more awkward things like RealPlayer or Flash is far easier, because I can just use the official 32-bit versions.[/LIST]Anyhow, you effectively have three choices, each with their own merits and drawbacks:[LIST=1]
[*]Create a belligerently purist, exclusively 64-bit system ... making things like Flash that bit harder to get working.
[*]Do what I've done, and opt for something that can run 32-bit and 64-bit stuff side by side.
[*]Go for option #1, but add a 32-bit chroot. This option would take some time to explain properly, so I won't go into it just now.[/LIST]Once you decide which road to go down, the way to set something like your Flash player up gets decided *for* you. Not all "64-bit Flash" HOWTOs necessarily follow the same approach, which is why it's important to know what you want. Of course, you could have avoided all this nonsense by buying a 32-bit processor ... but since you haven't, it's worth taking a moment to decide how you'd like your box to work, rather than winding up falling between two stools, adopting different approaches in different situations, and tangling your Ubuntu box up in knots.

Anyhow, I hope this is useful. I'd be happy to go into more specific detail, once I'm sure I won't be making a mess of your box.

---

