---
title: "Ubuntu quit's loading on splash screen after upgrade. &quot;"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by wolfreak_99 on 2010-06-28
I'm kind of new to the forum, so I hope I am posting in the right section, and that I didn't miss an previously posted thread of the same problem. I'll go ahead and explain what I was doing before this happened, to make sure I give enough detail and idea of whats going on.

**What was going on before:**
Anyways, around 2 or 3 am this morning, I noticed my Firefox loading rather slow (took around 5 - 7 seconds to load and navigate pages, even google, and it would sometimes become unresponsive), I thought it may have been a addon problem, so I opened up a new Firefox profile with no addons but the browser crashed upon loading the certain page I was trying to view, and I figured I'd look into it later and use Chromium for a while (I'll be open, I was trying to watch an pron tube site, and when your, you know, you don't really feel like stopping to go technical and try to fix it or whatever), but Chromium said that the flash player wasn't installed. I thought it was kinda odd, but then again I didn't want to go technical and thought maybe since mozilla firefoxs engine loaded the flash, I'd use Mozilla Seamonkey which uses the same gecko engine. The flash wasn't working either on there.

I tried looking up to see if there was a 64bit deb package for flash, but they didn't have it, and I seen someone mention that doing the 'apt-get upgrade' upgrades it, so I did that, and it also said it installed some extra packages when doing it, but I figured it was just that getlibs grabbing the extra dependencies and went along with installing them (after all there shouldnt be much to lose since its from the repository, right?)

I restarted the computer to give the updates a chance to take effect (it didn't mention to restart, but I thought I'd go ahead and do it anyways to ensure it updated okay).

**This is where the booting problem comes in:**
When my laptop restarted, the loading was going across very slowly (I have ubuntu studio installed through regular ubuntu, so it was showing the text filling up), normally it would just fill a little bit of the first "U" in "Ubuntu Studio" and then be done quickly, but now it goes slowly all the way, and when it fills "Ubuntu Studio", it stills stays there, it doesn't load on.

I pressed the down button to see the terminal and it says this:
```

fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 384229/810080 files, 10960231/32421170 blocks

```I have no clue what to do now, and I wanted to ask for help before I go trying myself editing the command line boot process.

I would appreciate some help or advice (even if it doesn't work, I'd appreciate it anyways just for you attempting to help.). I will provide any info (if shown how to retrieve it that is lol) if it helps get a better idea. I am using my mothers laptop to type this out so I have access to this while in the boot process of Ubuntu on my laptop, so I should be able to follow instructions fairly easy.

Thank you so much for taking your time to read this and thank you even more if you can help me.

---

### Post by wolfreak_99 on 2010-06-28
Does anyone have an idea what couild be the problem? Please help, I'm so frustrated with this, I've tried even [http://ubuntuforums.org/archive/index.php/t-422523.html](http://ubuntuforums.org/archive/index.php/t-422523.html) doing that and it still isn't working. I've tried all menu options. I finally had the day off today and I was going to record some guitar riffs and now I can't, I can't access the files from windows 7 (since its a fat32 partition), and I'm scared crapless that I won't ever be able to access my previous music work again. I'm wanting to cry its this frustrating.

---

### Post by wolfreak_99 on 2010-06-28
PLEASE HELP, IM SORRY IM DOUBLE POSTING BUT I JUST WANT MY MUSIC BACK. IM SO DESPERATE.

If i get Ubuntu working.. I'm removing Ubuntu Studio A.S.A.P., I have more of a chance of recording using windows vista..

---

### Post by wolfreak_99 on 2010-06-29
Maybe I could copy the boot folder from the livecd and place it in?

EDIT: nope doesn't load kernel.

Is there any way of accessing the installed ubuntus Synaptic from a live cd? Like a remote desktop type way? I want to remove Ubuntu Studio, this might make it work.. I just pray to God I hope it does.. :(

---

### Post by cchhrriiss121212 on 2010-06-30
When Ubuntu loads it is running fsck which is a routine disk checking operation and it will take a few moments longer than a regular boot. At this point you posted, do the blocks/files numbers keep moving or are they frozen at that same point whenever you boot?

If you don't want any of this, then just do a fresh Ubuntu install in the same partition, your Windows files will not be affected. I can show you a step by step guide to setting up a separate /home partition which will help you recover when your system goes belly up.

Also if you have important music on you computer, back it up, regardless of whether you use linux or windows.

---

