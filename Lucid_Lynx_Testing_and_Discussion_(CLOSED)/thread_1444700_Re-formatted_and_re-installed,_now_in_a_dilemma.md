---
title: "Re-formatted and re-installed, now in a dilemma"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arnab_das on 2010-04-01
Was facing lots of problems with the lucid lynx installation. hence i reinstalled it. a question though. should i update now? because everytime i update something or the other breaks, because of these 'partial upgrades'.

should i wait till the final stable release is out to update? or should i update now (has something essential been released in the updates yet?)

---

### Post by ronacc on 2010-04-01
you can update anytime just do not do "partial upgrades" .

---

### Post by arnab_das on 2010-04-01
> **ronacc said:**
> you can update anytime just do not do "partial upgrades" .

okey dokey. thanks.

looks like there's a lot which has been added since the beta1 release. the update manager tells me i need to download around 333MB of data.

[[IMG]http://img87.imageshack.us/img87/3707/updatemanager001.png[/IMG]](http://img87.imageshack.us/i/updatemanager001.png/)

---

### Post by sparker256 on 2010-04-01
From A early alpha this is what I use most every day in terminal.

bill@game-1004:~$ sudo aptitude update && sudo aptitude safe-upgrade

I have not used update manager during the 10.04 series.

Bill

---

### Post by djchandler on 2010-04-01
> **arnab_das said:**
> Was facing lots of problems with the lucid lynx installation. hence i reinstalled it. a question though. should i update now? because everytime i update something or the other breaks, because of these 'partial upgrades'.

should i wait till the final stable release is out to update? or should i update now (has something essential been released in the updates yet?)

Is this an April Fools joke? If not read on.

It's hard to impart this without it seeming rude. I apologize in advance, because what follows is essentially a lecture from Grandpa.

It is a beta. Things will break. The only reason you should be running the Beta is if you are willing to help debug before the final release.

You should always update then in my opinion, else any bug reports generated automatically by apport or reported manually are irrelevant. Whenever something in the default install packages is updated, it's highly essential to keep those updated to the bleeding edge. Otherwise you could easily be reporting something that's already been fixed, and that's not good for anybody, including yourself. In fact you could be an impediment to the process as Apport retracing service must inspect and then assign triage responsibilities and status to your bug report. Enough of that happens already by accident without someone doing this intentionally for all intents and purposes. Don't bother to submit any bug reports on the Beta if you insist on continuing to use it but don't keep it updated.

If you want stability and are working with live and important data, install the latest stable release (9.10) and wait until the final is released the end of the month. Even then, you may want to wait a couple of days after the final, maybe even as late as the middle of May, to fully upgrade as more hardware becomes part of the installed base and there has been sufficient time to ferret out even more bugs.

---

### Post by arnab_das on 2010-04-01
> **djchandler said:**
> Is this an April Fools joke? If not read on.

It's hard to impart this without it seeming rude. I apologize in advance, because what follows is essentially a lecture from Grandpa.

It is a beta. Things will break. The only reason you should be running the Beta is if you are willing to help debug before the final release.

You should always update then in my opinion, else any bug reports generated automatically by apport or reported manually are irrelevant. Whenever something in the default install packages is updated, it's highly essential to keep those updated to the bleeding edge. Otherwise you could easily be reporting something that's already been fixed, and that's not good for anybody, including yourself. In fact you could be an impediment to the process as Apport retracing service must inspect and then assign triage responsibilities and status to your bug report. Enough of that happens already by accident without someone doing this intentionally for all intents and purposes. Don't bother to submit any bug reports on the Beta if you insist on continuing to use it but don't keep it updated.

If you want stability and are working with live and important data, install the latest stable release (9.10) and wait until the final is released the end of the month. Even then, you may want to wait a couple of days after the final, maybe even as late as the middle of May, to fully upgrade as more hardware becomes part of the installed base and there has been sufficient time to ferret out even more bugs.

erm...i hope i didnt give the impression that i 'wasnt' bug reporting. if i did, that wasnt intended. i have been reporting bugs since the alpha stages. maybe not to a large extent but yes, i did report quite a few. and i'm doing the same now as well. thanks to the excellent "report" feature which has been added to every error, reporting bugs is a pleasure. 

i do tend to report bugs for softwares as well. i just love the new gwibber but i think the bugs in it arent being addressed at all. gwibber still faces problems pulling tweets (at least in my case it does). i have been opening new bug reports, commenting on gwibber's bugs etc. on launchpad (well thats the most i can do really, since i'm not a programmer/developer). and thats just one example.

anyway, the thing is, i have installed 10.04 twice now, i do want to report bugs, but i want to use the OS as well. thats the reason why i asked this question. i hope i was able to explain my situation.

---

### Post by coffeecat on 2010-04-01
> **arnab_das said:**
>  everytime i update something or the other breaks, because of these 'partial upgrades'.

It's worth reading the sticky on partial upgrades.

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by arnab_das on 2010-04-01
@coffeecat

thanks a lot. that was brilliantly informative.

---

### Post by djchandler on 2010-04-02
> **arnab_das said:**
> erm...i hope i didnt give the impression that i 'wasnt' bug reporting. if i did, that wasnt intended. i have been reporting bugs since the alpha stages. maybe not to a large extent but yes, i did report quite a few. and i'm doing the same now as well. thanks to the excellent "report" feature which has been added to every error, reporting bugs is a pleasure. 

i do tend to report bugs for softwares as well. i just love the new gwibber but i think the bugs in it arent being addressed at all. gwibber still faces problems pulling tweets (at least in my case it does). i have been opening new bug reports, commenting on gwibber's bugs etc. on launchpad (well thats the most i can do really, since i'm not a programmer/developer). and thats just one example.

anyway, the thing is, i have installed 10.04 twice now, i do want to report bugs, but i want to use the OS as well. thats the reason why i asked this question. i hope i was able to explain my situation.

Sorry if that was harsh. 

Glad you gained some understanding about this. I used to code, and I know it can be frustrating if people are reporting bugs that in fact have been addressed or fixes are ready but not released yet.

Although I'm not sure of this, you may be able to use gwibber on older versions of Ubuntu if you enable backports, with the understanding that backports are unsupported. In other words, don't file bug reports if you encounter problems.

Since you want to help debug gwibber, then keep running 10.04 beta and stay up to date with all updates.

---

### Post by djchandler on 2010-04-02
> **sparker256 said:**
> From A early alpha this is what I use most every day in terminal.

bill@game-1004:~$ sudo aptitude update && sudo aptitude safe-upgrade

I have not used update manager during the 10.04 series.

Bill

Thanks for the heads up here. I had not read the sticky about Update Manager.

+1

Maybe there should be a requirement to acknowledge having read the stickies before you post or report bugs either here or on launchpad.

---

