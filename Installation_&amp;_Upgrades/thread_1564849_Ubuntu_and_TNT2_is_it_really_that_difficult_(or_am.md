---
title: "Ubuntu and TNT2: is it really that difficult? (or am I missing something?)"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by julio_cortez on 2010-08-31
Hi everyone. First of all I warn you that I'm still a kind of noob in tweaking Ubuntu. I've made several "default" installations flawlessly, but this one is causing me problems.

**Machine: **1,8GHz Athlon XP, 40GB IDE HD, 256MB DDR RAM, AGP TNT2 32MB
**System: **Both Ubuntu 10.04 x86 and Xubuntu 10.04 x86.
[B]
First try:[/B] I booted Ubuntu from CD trying to install it along with Windows (shrinking it). I could see a nice Plymouth loading screen (*better than the one I see on my HD5xxx* ](*,)), but nothing else.
As soon as Plymouth stopped loading, everything disappeared and I was left with a black screen.

**Second try:** I tried installing it with Wubi: it went perfectly, I rebooted, the menu to choose whether to load XP or Ubuntu was there.. I chose Ubuntu and I couldn't get past Plymouth. Again. It behaved the same, after the Plymouth screen, nothing.

**Third try:** I tried also Xubuntu. I could see Plymouth, after Plymouth I could see something that seemed some text, resulting in Noveau being unable to do something (so I guess it's something related to the video card being too old)..

**In the end: **Everytime I tried to install/load Ubuntu, it got stuck just after Plymouth. The only difference was Xubuntu returning some kind of  Noveau error, while Ubuntu just showing a completely black screen.

So, do you think that any of these would help?

[LIST]
[*]Trying an older version (maybe 8.04 which is a LTS)
[*]Trying 10.04 alternate (I don't think it would change anything to be honest)
[*]Trying something lighter (possibly basing on *.deb packages)
[/LIST]
In the latter case, would you suggest me something in particular (keep in mind that I'm not experienced with Linux, so a CLI install would make me quake)?
The last thing.. No, replacing the TNT2 card with something more performing is not an option (the machine is not mine, otherwise I would have already done it). Either I manage to install Linux on this setup or.. I manage to install Linux on this setup.

Any help would be appreciated!! :)

---

### Post by julio_cortez on 2010-09-01
Bump!!

Had it been my machine I would have tried several installs to see if I could find one working, but..
[I]Being the machine not mine I'd really like advice.. I can't just say "let's try and see what happens"..

[/I]**PS: **thanks to whoever corrected me the tag.. Being in a hurry sometimes plays bad tricks :)

---

### Post by PaulReaver on 2010-09-01
have you tried booting into safe mode?  I think you hold in the left shift key on boot.


you mentioned the nuovo driver have you tried nvidia's proprietry driver instead?

---

### Post by julio_cortez on 2010-09-01
> **PaulReaver said:**
> you mentioned the nuovo driver have you tried  nvidia's proprietry driver instead?
Thanks for answering: I couldn't install the proprietary driver..  Installation failed :(

Do safe mode also apply to the installer? I was thinking about using  8.04 alternate, just because the PC is a little old (and 8.04 is the  "oldest" one still supported)..

> **PaulReaver said:**
> have you tried booting into safe mode?  I think you hold in the left shift key on boot.
Would I be able to do that also with a Wubi install? If so, I think you suggested me something really useful, that I still wasn't aware of :)

---

### Post by wurzzero on 2010-11-10
I konw this a little old, but did you make it?

i have a P3-750 with a TNT2 M64 32MB.

---

