---
title: "embedded style liveCD?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Forlornity on 2007-05-09
Hey there, I'm looking to develop a LiveCD version of ubuntu with only the bare essentials and a couple of programs installed. 

Basically, it needs to be a liveCD which will run a single program (written in .NET) automagically on boot.

I'm expecting this is going to be rather hard to achieve (for me) so I put it to you guys to help me out.

Thanks, Forlornity

---

### Post by Forlornity on 2007-05-09
...bump...
anyone?

---

### Post by starcraft.man on 2007-05-09
Why do you want to create a stripped down version of Ubuntu to run a single app on boot up? I don't understand the purpose... you do know you can install Ubuntu onto a USB and rip whatever you want out of it, then just clone it to any PC...

It sounds to me like your going to a lot of work, can you please be specific on what you aim to do and what app you need?

---

### Post by Forlornity on 2007-05-09
Well I need to have a program run on boot which will run a .NET app, I have no idea as to the real purpose of it as I'm helping out a friend who just requested that I find a way of running a .NET app from a liveCD running in Linux.

Here's the general idea:
Turn PC on...
Insert CD before boot from HDD
Boot from CD
Run OS
Run .NET Program
Do Stuff
Shut Down
Take disc elsewhere


As I said, I'm not entirely sure what's going to be happening in the program or what the purpose is but this should be enough to get going?

thanks, Forlornity

---

### Post by starcraft.man on 2007-05-09
Ummm, first of all I think theres a fundamental problem to that list...

.net is Microsoft's proprietary framework... you can't "just" pop it into Ubuntu (once again, Ubuntu is not a giant cheap windows emulator), at least not to my knowledge. Nor do I think the WINE emulator either contains .net or can install .net because then there wouldn't be a project called [Mono.]("http://en.wikipedia.org/wiki/Mono_%28software%29#Current_status_and_roadmap") Now, Mono which might be your solution, isn't complete yet... it hasn't even completed implementing the 2.0 API and then theres the 3.0...

Unless you have a timemachine to move to the future, I don't see you accomplishing this task. Unless you and your "friend" code the remaining bits of mono, make it stable and then compile an ISO yourself >.>

Sorry to be the bearer of bad news.

---

### Post by Forlornity on 2007-05-09
I suspect he'd be fine with using an unstable release, according to him he has a .net boffin so I presume he'll be able to code around any problems he may come up with.
Any idea just how usable mono is yet?

thanks, Forlornity

---

### Post by starcraft.man on 2007-05-09
> **Forlornity said:**
> I suspect he'd be fine with using an unstable release, according to him he has a .net boffin so I presume he'll be able to code around any problems he may come up with.
Any idea just how usable mono is yet?

thanks, Forlornity

Heres the [main]("http://www.mono-project.com/Main_Page") site and [wiki's]("http://en.wikipedia.org/wiki/Mono_(software)") article.

First problem is if the program your coding is for 3.0 your out of luck, project hasn't even finished with 2.0. As for how stable 2 is right now, I doubt its that stable I haven't heard of a far along beta finalizing testing. Your welcome to direct your friend [here]("http://www.mono-project.com/Use") and he can read the api documentation.

---

### Post by Forlornity on 2007-05-09
I'll be sure to point him there, dunno what he'll think of it though.

thanks anyway, I'll get back to you with the end result.
Forlornity

---

