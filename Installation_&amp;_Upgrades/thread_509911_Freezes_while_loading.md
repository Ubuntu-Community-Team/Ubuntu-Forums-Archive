---
title: "Freezes while loading"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by dhehmann on 2007-07-26
So I've managed to get Ubuntu 7.04 installed after Partition Magic killed XP, which is a whole other story. Anyways... Ubuntu freezes for me on the loading screen every time three of the bars fill up. It has never actually booted up for me since the install, and doesn't even make it to the login. 

Any help would be greatly appreciated.

---

### Post by kevinlyfellow on 2007-07-26
Have you tried the recovery mode?

---

### Post by dhehmann on 2007-07-26
yeah, and it freezes up at the same point. The status bar gets three bars full and then nothing

---

### Post by kevinlyfellow on 2007-07-26
Ok, when you are in Grub, press 'e'  and then down and 'e' again (to edit the second line, the kernel line).  Remove the word splash and quiet.  When you are done, press enter and then 'b'

This will show you where it is hanging.  Be sure to write down and post what it freezes on.

---

### Post by dhehmann on 2007-07-26
Done as you suggested, and this is the point where it freezes:

[IMG]http://i76.photobucket.com/albums/j35/_-___/m.jpg[/IMG]

---

### Post by dabl on 2007-07-26
Try an Alt-F1, and if nothing, a Ctrl-Alt-F1, when it gets to that "frozen" point.  Let us know what happens.

---

### Post by dhehmann on 2007-07-26
Tried the Alt-F1 and Ctl-Alt-F1 and neither worked. This time, it froze here, which should help figuring out what the problem is:

[IMG]http://i76.photobucket.com/albums/j35/_-___/m001.jpg[/IMG]

---

### Post by dabl on 2007-07-26
It's not liking your hardware -- what is the video chip?  Search the forum for "boot options" and the model of your video chip -- maybe someone's already figured out a way around the problem. :sad:

---

### Post by buzzmandt on 2007-07-26
edit the boot path again and at the end of the line add 
```
noapic nolapic
```

---

### Post by C4U53 on 2007-07-26
omg finally some with the same problem as me ( no offense ) But I get the same exact ****

I'm on a HP pavilion if that helps..

Geforce fx5200

I have another post on here with my dxdiag info if needed.. its really weird though

---

### Post by kevinlyfellow on 2007-07-26
A common boot option that helps some people need is acpi=off

Just put it right on the kernel line (where you take out splash and quiet)

---

### Post by oddin85 on 2007-07-26
fixed the lag on start up on my computer by commenting out eth1 in /etc/network/interfaces
(comment out by using the # character)

dunno if it's the same problem you're having or not

[http://ubuntuforums.org/showthread.php?p=2637781]("http://ubuntuforums.org/showthread.php?p=2637781")

---

### Post by dhehmann on 2007-07-26
Tried both the acpi=off and the noapic nolapic to no avail.

My graphics card is an ATI Radeon 9250

I'll try out searching for the graphics card as suggested. 

Thanks for the help, everyone.

---

### Post by C4U53 on 2007-07-26
I don't think it's your vid drives. but I could be wrong because I am having the same exact problem and I have a pci nvidia fx 5200. I also tried all of those commands and came out with same results. I've noticed the more I do it though before I get his exact Screen shot that it says something about usb 1 of 2 or 2 of 2 or 2 or something error -17
Using backup image ( not exactly what it says but something close)
continuing from like hda5 or something then it does all its stuff acts ok then runs into his screen shot

I've put in a bug request but perhaps you should too with your screener through launchpad .. unfourantely I don't have a digi or anything to do what you did...

I forgot to mention that when I get that weird error its when it first tries to boot then everything acts fine like it goes through the ok checks and goes to starting to boot or loading boot records or whatever but never continues

---

### Post by C4U53 on 2007-07-27
I guess there is no real answer to our problem. Just that we are screwed? I've been going at this for about 5 days. Found no solution anywhere.. Everyone just says the same thing.. try these boot options. edit this line.. I've done all these things. with no positive outcome. I've used the launchpad to report the bug. Done everything I could possibly think of. I've re-installed with every kernel. Tried the Alternate cd. the live cd. the dvd. I've messed with my bios. I've even wanted to completely wipe my system for a chance that it "might" work . But I have this strong feeling that if I did that. I would end up with the same results. then I'd just have to re-install windows. It'd be useless. but I'm going out of my head on what's wrong.

I think I've read most of this forum in the last few days. I now could even troubleshoot people through other problems they might have with ubuntu and I've never used it.

This is so broken. I highly appreciate the helpful advice from the different users of ubuntu, Don't think for a second you all have not been a big support. because you have  but where are the devs?

I want to give up. I can't. I don't even know why I concern myself with it anymore. It's just so irritating. Yet I still find myself fidgeting with it for hours on end. I almost got kicked out of my wow guild because they are all like "where you been for the last week" Guess where I've been.. Trying to get ubuntu just work.. just to launch. even though I'm even more concerned now with what problems will I have after I get it to launch.

****.. If there is anything that I could read to learn to help you guys code some stuff.. Thats fine.. Just point me in the right direction. I'll do all I can. I just wouldn't know were to start

---------------------------------------------------------------------------------------------------------------------------------------

---

### Post by C4U53 on 2007-07-27
I'm going to try Fedora. Hopefully I'll turn out better results.. If I install fedora on a different partition and it works can I access the Ubuntu Files etc see if I can try and fix the problem at all?

---

### Post by C4U53 on 2007-07-27
Ok. So I think I know how to get ubuntu. Unfortunately this doesn't really solve my problem

Well anyway. I got that fedora I got the same exact error I received from Ubuntu (see dhens screen)

I got a little frustrated and pulled out my gfx card thinking maybe it has something to do with that.. and it did.. 

I have a pci geforce fx 5200 . But the other guy with the same problem as me has a ATI raedon .. not sure if his is pci pci-e agp or what.... Is there anyway to build a kernel with my drives.. would this fix the problem ? any help appreciated.. for now I'm going to try and re-install ubuntu without my gfx card in and report the results.. Later for now..

---

### Post by C4U53 on 2007-07-27
It works! Ok.. so yea gfx card was the problem for both fedora and Ubuntu.. Now. How would I resolve such an issue other than buy a new gfx card?. I'm really poor guys heh. so If there is a work around I'd definetly like to learn how. I figure it has something to do with the kernel and perhaps the driver version or perhaps its just the card in general? I don't know. Any help appreciated. Thanks for sticking it out with me.

It's weird that the onboard vid card works fine. which is a p.o.s. 

And mine doesn't.. it's also a p.o.s just a better piece ;).

Anyway. I'm happy for now.. Just don't want to have to pop my vid card out everytime I want to boot ubuntu.. which may eventually be everytime.. its so shiney!..

---

### Post by kevinlyfellow on 2007-07-28
> **C4U53 said:**
> It works! Ok.. so yea gfx card was the problem for both fedora and Ubuntu.. Now. How would I resolve such an issue other than buy a new gfx card?. I'm really poor guys heh. so If there is a work around I'd definetly like to learn how. I figure it has something to do with the kernel and perhaps the driver version or perhaps its just the card in general? I don't know. Any help appreciated. Thanks for sticking it out with me.

It's weird that the onboard vid card works fine. which is a p.o.s. 

And mine doesn't.. it's also a p.o.s just a better piece ;).

Anyway. I'm happy for now.. Just don't want to have to pop my vid card out everytime I want to boot ubuntu.. which may eventually be everytime.. its so shiney!..

I'm glad to hear that you got it working!  Maybe the OP can solve his issue in a similar way.  Anyhow, definitely submit a bug report if you haven't already, it sounds like a big one if it also effects fedora.  (we need a bug smiley for these forums...)

Maybe its trying to load an unstable video driver?  Thats a real pickle of a dilly.

---

