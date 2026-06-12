---
title: "New to Linux, and can't get going..."
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by luckyfox on 2010-01-19
Hey there, Lucky here!

I'm ~brand~ new to Linux, and already having some serious set backs. From what I have been told by quiet a few, I can have Linux up and running after six simple questions. Well, although that sounded awesome, I haven't had much luck. :(

Before I go any further, I have to be sure to mention, I have absolutely no technical experience at all.

I design websites, and that is about as deep as I go down the computer rabbit-hole, so please be gentle. ;)

I downloaded the ISO with bit-torent, to ensure its solidarity. Burned it to a CD as instructed, and began the instillation process.

I tried twice, waiting (maybe 20 minutes) for anything after I hit enter (besides the flashing underscore). I was able to figure out, that by removing the -quiet splash command from the install, I could see what exactly it was doing. And every time, after the same amount of time, the install would hang. I tried this several times, with the different options available with the install. The instillation first warns me about udma/33 (although I have no idea what that means) and then a final warning that the TSC is unstable (I think that is the system's way of keeping time).

After that, the CD-Rom dies, and the hard drive dies. All that remains, is the small section of log I can see, and the final two notices. 

I happen to read (somewhere) that it can be a hard drive problem. Not possible, I just installed a new one and have had Windows Vista Home Premium running on it for a while now (Windows still works fine, so obviously the installer isn't getting very far). Now, I have nothing I must keep on this computer, so I was just going to partition the entire hard-drive and install linux as the -only- OS, but I can't even get to that part!

What information can I attempt to gather to assist someone in assisting me (since I haven't found anything anywhere else), and ~please~ break down assistance into laymen's terms.

The computer is a Toshiba Satellite. Intel Celeron M, 520 @ 1.60 GHz. 2.00 GB or RAM, and the version of Vista is on Service Pack 2 (in case you need to know that). It has a slim drive and a touchpad built in.

Seriously, I really need some help if I am ever going to get this Linux working. I'd LOVE the chance to be free of Microsoft... Over $100 for an upgrade? Over $200 for a full install? I mean really, you all know where I'm coming from... For-shame Microsoft... For shame...  ](*,)

Plus, the daily annoyance of explorer.exe freezing just isn't as fun as it used to be. [-(

Any and all help is greatly appreciated. [-o<

Appreciatively,
-Lucky

---

### Post by Bartender on 2010-01-19
Reading thru your post, a few questions came up.

- How fast did you burn the .iso to CD?
- Did you check the md5 sum?
- Did you use a good-quality CD-R, not -RW?
- Do you have a test PC, or a desktop PC and a spare HDD, that you could spin up and see if the CD works on it?
- I assume you downloaded a LiveCD?  The alternate install CD is considered more reliable than the LiveCD.  But the alt-install is only for installation.  It doesn't offer the "test-drive" function that comes with the LiveCD.
- Can you try burning the download on someone else's PC?  Sometimes an optical drive just can't burn a decent disc.
- Is this 9.10?  You might want to try downloading 9.04 and give that a shot.  IMO 9.10 is a little bit fussy.

---

### Post by luckyfox on 2010-01-19
- How fast did you burn the .iso to CD?

I made two CDs. One at the fastest speed possible. And one at a mind-crashing 1x... JUST to make sure that wasn't the problem.

- Did you check the md5 sum?

(That'll be answered in the next question)

- Did you use a good-quality CD-R, not -RW?

The drive is a DVD-RW, and is new. BUT, I FINALLY got the -preview- version to get up and running. But for some reason, it will NOT load up the rescue or regular boot!

- Do you have a test PC, or a desktop PC and a spare HDD, that you could spin up and see if the CD works on it?

Actually, I don't. But again, the preview version works, so why wouldnt the full version work? I had to disable all of the strange settins (noapic, nolapic, edd=on)... So I tried editing the boot command, to include the same settings, and although it seemed to get a little further, it died just as well.

- I assume you downloaded a LiveCD? The alternate install CD is considered more reliable than the LiveCD. But the alt-install is only for installation. It doesn't offer the "test-drive" function that comes with the LiveCD.

Strangely, I accidentally downloaded the alternate version first. That's what lead me to problem solving all the way back to the standard version in live mode with all the settings ticked.

- Can you try burning the download on someone else's PC?  Sometimes an optical drive just can't burn a decent disc.

Again though... If the live version works with the settings ticked (And it really does work fine!) why wouldn't the install work just as well?

- Is this 9.10?  You might want to try downloading 9.04 and give that a shot.  IMO 9.10 is a little bit fussy.

And yes, I'm working with 9.10.... I haven't played with any other versions at this point... I'm too darn stuck on the live version working, and the full-install not!

Thank you VERY much for your assistance.

-Lucky

---

### Post by luckyfox on 2010-01-20
> **Bartender said:**
> - Is this 9.10?  You might want to try downloading 9.04 and give that a shot.  IMO 9.10 is a little bit fussy.

So I went with the suggestion. Grabbed 9.04. I was able to get into the live demo without touching a thing, and now I'm 45% through the instillation without a single hitch. Looks like the suggestion of moving to one version back rocked the problems... Every last one!

I'll let you know the final outcome once I finish.

*****UPDATE*****

OS up and running, although critical problem found: [http://ubuntuforums.org/showthread.php?t=1386193](http://ubuntuforums.org/showthread.php?t=1386193) 

Thanks for your advice!

-Lucky

---

### Post by luckyfox on 2010-01-21
I still can not run Karmic, because of this problem. Any advice greatly appreciated.

Karmic presumably incompatible with the Toshiba Satellite line. No solve found. Roll-back to 9.04 Jaunty.

---

