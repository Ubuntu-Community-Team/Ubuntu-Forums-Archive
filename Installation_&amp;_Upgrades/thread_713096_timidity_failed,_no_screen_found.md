---
title: "timidity failed, no screen found"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by itchy88 on 2008-03-02
hello friends!

i just installed ubuntu studio on a friend's computer for dual boot with xp.  i got xp working, but studio fails at loading timidity and then pops up a screen telling me an error occurred:  no screen found.

i've some poking around and re-configured the xconf.  no dice.

i figured i could load up ubuntu live and copy it's xconf, but it displays the loader screen just fine then tells me the resolution is set too low and crashes.

the graphics cards is nvdia geforce 7 onboard.  thanks in advance for any help.

---

### Post by itchy88 on 2008-03-06
okay, so i've narrowed it down to the nvidia drivers failing in xorg.

since live won't boot (probably for the same reason), i tried running the nvidia xorg writer in recovery mode:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-03.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-03.html)

it told me that it wouldn't run in runtime1, only runtime 3 which turns out to be the full operating system environment.  which won't run unless i can get nvidia up and running on xorg.

eiiiiahhhh!

does any know if i'd be better off trying an install of studio hardy heron alpha?  would it be written with some regard for nvidia cards?

there's a guide for manually retooling xorg on the nvidia site:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-b.html)
but it's a little over my head.

last question:
would the alternate cd for gutsy gibbon 7.10 boot any different than the install i have currently for studio gutsy gibbon 7.10?  if i could get it going, i could then just upgrade to studio from regular ubuntu, but i'm guessing the xorg compilers are the same for both regular and studio.

---

