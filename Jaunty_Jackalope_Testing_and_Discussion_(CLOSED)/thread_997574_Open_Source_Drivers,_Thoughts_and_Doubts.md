---
title: "Open Source Drivers, Thoughts and Doubts"
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mencargo on 2008-11-29
I think Ubuntu is getting to a point that open source drivers are in most cases better than the proprietary ones.

At least in my case, ATi Open Source driver works much better, but as an old Ubuntu user, I was getting used to agree to install restricted software every time it's offered, because I'm used to associate it with been able to do use the hardware or not.

I think it's time to stop offering them.

Anyway, if the user wants to install them for a specific feature that he/she needs, he/she could go to:

"System" > "Administrator" > "Hardware Drivers", and select them.

What happened to Ubuntu's open source philosophy?

Open Source should always be the first choice, restricted and commercial software should be available for those who needs them, but never offered.

This is how open source will evolve.

---

### Post by ronacc on 2008-11-30
why should they stop offering them ? let the user make the choice what they want to use on their system , make the opensource driver first choice not "only choice".

---

### Post by mencargo on 2008-11-30
I'm not implying "only", for that there's GnewSense, Debian, ...
I know Ubuntu philosophy is different in this aspect, but when a ATi driver is offered, even if it says "restricted", "propetary"...
It also says it's required to use it's full potential... well, I dissagree.
And the normal user will just say "OK" as he's used to.

So I'm not saying "remove it", just don't offer it if it's not needed.

---

### Post by autocrosser on 2008-11-30
Well, I think you make a valid point, but we've still got a way to go to reach where the Open drivers as better most of the time---right now it is once in a while they are better...Of course, in a perfect world one would check to see what drivers are needed for the hardware BEFORE it was bought--Voting with one's buying power is always the better option.

If enough people would work that way............Well, like I said "in a perfect world"--I do hope to see that day.

---

### Post by ronacc on 2008-11-30
Hideing the "restricted drivers " away would have the effect of making them unavailable for those who did not know where to look for them , I appluad ATI for their movment tword Opensource  and am infact considering a switch to ATI from my longtime favorite Nvidia for that reason .But while I support Opensource,I support choice even more . Linux has enough of an acceptance problem without presenting a roadblock right at the start,to a decent user experience , look at the endless threads about things as trivial as the default theme and not so trivial as wireless drivers . I build my own boxes and have the luxury of choice of hardware , most are stuck with what is in the box they bought and are not even considering  Linux at the time of purchase.Like autocrosser says "in a perfect world" but I am less hopeful of that.

---

### Post by cmay on 2008-11-30
i never use the restricted drivers up to intrepid ibex. bit having got used to compiz and desktop cubes on open-solaris i enabled them in intrepid. the first thing my brother do when he finally tries ubunti is to fetch the drivers from nvidia homepage and call me and ask (again) how to install them. i always tell him that he should not use them since he really do not need them. but he can not understand that. and also that ubuntu finds them by itself if he is just a bit more patient , i guess if he cant understand how this works then maybe others wont either. the warning about using restricted drivers should be more clear however. i think its should be printed in a more large font size that if one choose to use these the system can be instable and the ubuntu developers can not fix it. then those who wants stable can choose not to use them and those who wants restricted drivers can use them for the cube effect and such. if the drivers are not offered this way it is now then you are going to have a lot of post in the forums asking how to compile nvidia drivers from source from random site X or how to install the "official" ones from nvidia. 
just my thoughts on it. i do not like the restricted drivers that much but i think they are given in the most perfect way as is.

---

### Post by icarid_17 on 2008-11-30
making restricted drivers for the average convert harder to get to could make them turn away from Linux pretty instantly. (in that installing certain restricted drivers is easier than certain open source drivers, though nvidia's drivers were hellish to install and now they're broken again, for me at least) An example of this "if it doesn't work out of the box fully and completely in the manner I expect it without any help on my part, it is a complete an utter failure in every respect" mentality is thus: a couple of my friends tried it, used it for a while then started to absolutely hate it (to the point of ridiculousness) because of really stupid things that they have could fixed really quite easily (one of them said that OpenOffice.org sucked, and thus, apparently, the whole OS sucked because it had no grammar tool and the dictionary wasn't perfect, which obviously is untrue, there's languagetool for the grammar, and new dictionaries can just be installed). this is not to say that its true for everyone, I suppose that people who are willing to learn and people who aren't. the other thing is that somebody really must convince nvidia to release their drivers to the open source world (I mean, what on earth could we possibly do with them?, there wouldn't be any lost profit because nvidia lets people download them for *free* even if they don't have an nvidia graphics card)

---

### Post by Gina on 2008-11-30
A non-expert friend of mine tried Ubuntu using Wubi but had a problem with wireless - her router was too far away and too awkward to run a cable.  Seems her wireless adapter needed a proprietary driver and didn't know how to get it in Windows (with a wireless internet connection) and transfer it to Ubuntu (without a connection before driver installed - catch 22).

We who know about all this can work it out - maybe with the Windows driver and ndiswrapper - but for the average computer user, this is beyond their capabilities.  Although Windows has a command line much like Linux, few Windows users know how to use it as most things can be accomplished in the GUI,  We need some sort of automated process to either install a driver if it can be included in the distro or use ndiswrapper and prompt the user to insert their Wireless Driver CD for Ubuntu to read the driver files.

As I see it, the main stumbling blocks of changing to Ubuntu are wireless and display.  Wireless is critical if the user doesn't have a cable connection to the internet and, of course, you need a display of at least a reasonable resolution that can be used to download and install proprietary drivers if required.

As an example of display problems, my nvidia graphics produces a desktop which is twice as high as the screen - showing only the upper half of the "picture" even with the login screen.  This makes things very awkward until I use the Hardware Drivers dialog to install the nvidia proprietary driver.  Kubuntu is impossible as the menu is at the bottom, out of view.

---

### Post by autocrosser on 2008-11-30
When I upgrade my system the next time I most likely will be switching to ATI for the first time in 7 years (last was a G3 Blue & White PowerPC)--all because of the easier availability of drivers--

My Wireless card in this system is a Encore N adapter--using the Ralink open 2860 drivers--works MUCH better than the D-Link card that was in there..

Printer is a Brother HL-2070N Laser---Brother does a very good job offering drivers.

Scanner is a HP Scanjet 4370--so Xsane has no problem with it....

So currently I'm only using the closed nVidia drivers & we all know how "good" they are....

---

### Post by quickshade on 2008-11-30
I fully support the opensource drivers and what they are trying to do, but lets face the facts that to many people want to take full advantage of the hardware they have and don't want to be left in the dust by others because they made the "right" choice. Not only that but with this many distros and projects in the linux world right now, the ones that need attention are not getting it. This all is for another forum entirely but the summary is that until the opensource drivers can meet the standards (for using the hardware to full potential, not talking about the crashes) they won't have a general use for linux users.

---

### Post by autocrosser on 2008-11-30
> **quickshade said:**
> <SNIP> This all is for another forum entirely but the summary is that until the opensource drivers can meet the standards (for using the hardware to full potential, not talking about the crashes) they won't have a general use for linux users.<SNIP>


Yes--this is a topic that is best for the Cafe--wider crowd there & "could" get a bit lively--Most of us here accept the "evils" of closed source--not that we like it, but we need to test alternatives that the general public will be using in the coming months ahead & the blend of software needs to be tested to see if it even co-exists together.

---

### Post by mencargo on 2008-11-30
I see your points and I agree, user should have the choice, and it should be easy.

But there is also the other part:
The proprietary drivers from ATi didn't work well for my x1950 Pro.
I had flicker problems playing video, it was fixed turning the desktop visual effects to none.
But it could be a pain in the *** if I didn't try changing the visual effects.
And there's also the lack of nice visual effects, from a $200 dlls video card...
Anyway, when I installed Jaunty I leaved the open source drivers any try them out.
Worked perfect, altho I can't play 3D chess, hahaha, no openGL.
But I have my nice visual effects.

The thing is, this open source drivers work ok, in some aspects better than proprietary drivers.

So, in order to support open source, Ubuntu shouldn't offer restricted software just because it's available, it should only offer it if it solves a problem or gives me the ability to do something I can't, like playing 3D chess.

And even then, it should be explained clearer, so a normal user could really understand what he's agreeing to.

---

### Post by sdowney717 on 2008-11-30
Google earth wont work with open source drivers. what about accelerated video games? NO, if they work at all they work like molasses. Anyone trying to come over from windows and seeing that would think linux does not work right.

It is sort of like, dont you want your hardware performing as close as possible to its designed parameters?

---

### Post by crjackson on 2008-11-30
> **ronacc said:**
> why should they stop offering them ? let the user make the choice what they want to use on their system , make the opensource driver first choice not "only choice".
+1

Besides, they still have a long way to go. Your ATI cards may work better with opensource but mine don't.

---

### Post by Neon Lights on 2008-11-30
> **sdowney717 said:**
> Google earth wont work with open source drivers. what about accelerated video games? NO, if they work at all they work like molasses. Anyone trying to come over from windows and seeing that would think linux does not work right.

It is sort of like, dont you want your hardware performing as close as possible to its designed parameters?

Maybe not for YOU. But for some people they work just great. It all depends on the card.

---

### Post by ktp on 2008-11-30
> **Neon Lights said:**
> Maybe not for YOU. But for some people they work just great. It all depends on the card.

This is good point...not all cards are going to be supported by open source drivers...so having an option to choose is great.  And it is almost always the case that restricted driver is going to provide better support for newer cards.

So looking at providing better/easy linux usability, I think Ubuntu is doing the right thing.

---

### Post by autocrosser on 2008-11-30
The rule of thumb is that Linux "tends" to stay about 6 months to 1 1/2 years behind in hardware--I say "tends" because that is true in "most" cases....I tend to upgrade about every 6 months to stay on the leading edge for hardware support & I have noticed within the last year or so that the lead time has a shrinking trend :).

I am looking forward to the day (I think in about 5 years or so) when Windows, Mac & Linux drivers are shipped at the same time--That is the day that Linus has won!!!

---

### Post by ronacc on 2008-11-30
It could come sooner if MS screws up with 7 as bad as they did with vista.

---

### Post by autocrosser on 2008-11-30
From what I hear--that is a real possibility :).

---

### Post by ktp on 2008-11-30
> **autocrosser said:**
> From what I hear--that is a real possibility :).

But not to worry, here comes ribbon ui to recuse :)

---

### Post by Barrius on 2008-11-30
> **Gina said:**
> 
As I see it, the main stumbling blocks of changing to Ubuntu are wireless and display. 

I agree.   I've convinced two Microsoft users in the office to convert to Linux - one uses Intrepid, the other Vista/Intrepid.   Both bought new laptops, in both I had to disable IPv6 to enable wireless.

---

### Post by aseries on 2008-12-07
I have installed 8.10 on a new MSI GX630 notebook with no graphics trouble. I did have to go through all that ndiswrapper nonsense to get wireless networking.
I have a lab machine with PCCHIPS M825 that needs LINUX because I am using the XP Pro license elsewhere. I absolutely could NOT get any 8.10 or 8.04 graphics driver to work properly with the integrated VIA/S3 northbridge or an Nvidia MX4000, Geforce 2, or an old ATI Rage Pro and the SAMSUNG 151V LCD. I got no res past 800-600.
No offense, but PCLINUXOS installed ALL of the prior mentioned graphics solutions 1024-768-24 AUTOMATICALLY. It also installed the wireless AUTOMATICALLY. Of course, nothing is perfect, PCLINUXOS livecd hangs on boot on the MSI notebook, something to do with native SATA.
Now, if I could get my Linksys wireless print server to work with ANY Linux flavor.

---

