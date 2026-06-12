---
title: "can't install/live cd on only one Computer"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Okie Dokey on 2007-07-06
I posted this in the hardware forum to no reply. Perhaps  I should have started here.

------------

Recently I purchased a second old computer that runs windows XP fine,but it can't seem to boot or run live Cds (both ubutu and mepis) 

I'm certain this is a hardware issue, since I can  swap the cd drives and live cds (either one) and put them into my main computer just fine (loading the live CD). I'm typng this while running the Ubuntu cd **I don't have linux installed anywhere**

the system that gives me the problem is a 1200mhz celeron with 512 mb ram, board made by Azza U644BC. 

While i'm running windows,the cd drive functions fine.  I think I'll try to find my windows instaal disk and see what happens when i boot with it. (since my repost to this forum I can confirm that the computer will boot a Windows XP Install Disk just fine).

When the old system starts ,with the live cd in, it starts up fine - for ubntu I choose the language and it proceeds to a part where it hangs at th e same place I think its loading ide-cd 89%

for the mepis cd it goes along and leaves me hanging at splash screen. 

I have a kubuntu install disk but when i try that it doesn't do any thing and either i get a beep and a restarts or the 3rd boot device,the hard drive kicks and windows starts.

Please help. I bought the old computer to learn linux

---

### Post by Okie Dokey on 2007-07-06
Just as I did in the hardware forum, I'll add more info, in this follow up posting;

-------------------

In addition I used the newest Kubuntu install disk (not the alternate install cd), not the older ubuntu 5.10 one I had mentioned in my first post. Kubuntu 7.x started up fine, the blue slider progress line that supposed to go back and forth for a minute or so, only goes to the right, then back to the left then freezes. It never recovers

Out of my frustration a used an extra old 3rd computer. The third one , a 433mhz celeron with 384 mb ram, installed fine. I the motherboard is Microstar.

So 
1.8ghz amd 1084 ram Abit mb - installs 
1200mhz celeron 512 ram Azza mb - Hangs
433 mhz celeron 384 ram Microstar mb - installs

Is there something really simple I could have missed, perhaps a bios setting? Something that windows allows/prefers but won't work for linux?

Is this the appropriate forum for this question?

Is it likely my motherboard is the problem?

---

### Post by dabl on 2007-07-06
Hmmm -- sounds like the IDE controller on the old Azza board may be sufficiently non-standard/obsolete that Ubuntu doesn't recognize it (just a guess, since that is where it hangs).

You've proven that it can boot a bootable CD, and you know that the CD ROM drive works, and you know that you have a good Ubuntu Live CD, so you're down to the BIOS and the motherboard.  Interesting that Mepis also won't play on it -- just confirms that the problem is somewhat generic to Linux.  You could try Knoppix Live CD, if you're a glutton for punishment.  I think that motherboard is not for Linux ...  :(

---

### Post by Okie Dokey on 2007-07-10
Thank you very much for the reply.  My apologies but I'm just getting started in this forum, I thought the forum sends an email if someone replies to a post, maybe i have to change that myself.



Hmmm. It's a real shame that the motherboard doesn't seem to be supported. I read that hanging at the 89% mark has happened to other people, but I never got a clear indication as to why.  Still others said that they never have heard of a motherboard that isn't supported.  I'm so brand spanking new at linux I'm just not sure it's worth my while to fight against it.

---

### Post by regomodo on 2007-07-10
unlucky there. This link will prove useful for selecting hardware in the future

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Okie Dokey on 2007-07-12
Thank You,
I downloaded the Knoppix live CD and it hangs also.
I looked into flashing the Bios on the MB but Azza turns out to be a horrible company, Award/Esupport or whatever the people are called who make Bios said they have a custom Bios available for my board, but it would cost 50$.  He said I could get my money back if it didn't work, but I don't beleive him.

I only bought this computer for 40$.

Probably the most sensible thing is to leave it as a Windows XP computer, and not try to force the issue and take the much older one,(see earlier post) Microstar mb 433mhz, 384mb ram 20gb hd (which my mom currently uses for her computer) which I've run live Cds on before and try that one instead.  

I'd have to reinstall all mom's programs on this 1200mhz azza computer, faster for her, but a pain in the *** for me.


If linux is a fit for me I likely would buy a much bigger hard drive on my current computer (2.5ghz amd 2 40gb hds, 1gb ram) and try a dual boot.

Would 433mhz with 384mb ram feel sluggish or slow with the full install of KDE?

how come this forum doesn't email when I get replies to my posts?? I have the instant email notification checked.?

---

