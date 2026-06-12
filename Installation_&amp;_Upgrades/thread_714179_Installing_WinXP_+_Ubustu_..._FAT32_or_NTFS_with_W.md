---
title: "Installing WinXP + Ubustu ... FAT32 or NTFS with WinXP?"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2008-03-03
Soon I will be installing WinXP and Ubuntu Studio on one of my computers. I'll probably install WinXP before Ubuntu to (hopefully) make the install process easier.

When I install WinXP, should I choose FAT32 or NTFS?

In the past I have used both file systems, different times, with XP.

Does one of those file systems "work better" with Ubuntu or Linux in general?

(I'm thinking... if I need to install an app to access the XP partition while I'm logged into Ubuntu... maybe FAT32, or vice versa, NTFS, would be better... or maybe it doesn't make a difference?)

I'm going to attempt to put 8gigs, or less, on the WinXP partition. It's only a 40g hard drive and I'd like as much of it to go into Ubuntu Studio as possible (audio recording and editing, eating space).

The sole purpose in putting XP on is to play the game Maple Story, minimum required 1.5g with a recommended 3g. Microsoft's site says WinXP (Home or Pro, either is fine with me) requires and recommends 1.5g on the harddrive. Somehow, I find that hard to believe. I won't be adding anything to the XP side except: MapleStory, anti-virus type stuff, and will probably have to put "SP2" on it. I have a hunch SP2 alone will eat up a lot more space.

In any case, my main question really isn't "what's the minimum harddrive space I can put into WinXP" (though I welcome responses)... the main question is if I'd be better off with FAT32 or NTFS.

Thanks in advance!

-Prof.

---

### Post by Pumalite on 2008-03-03
Both can be read and written to from Ubuntu. Fat32 does not allow files larger than 4 GB (I'm not a Windows user though).

---

### Post by logos34 on 2008-03-03
> **Th3Professor said:**
> The sole purpose in putting XP on is to play the game Maple Story, minimum required 1.5g with a recommended 3g. Microsoft's site says WinXP (Home or Pro, either is fine with me) requires and recommends 1.5g on the harddrive. Somehow, I find that hard to believe. I won't be adding anything to the XP side except: MapleStory, anti-virus type stuff, and will probably have to put "SP2" on it. I have a hunch SP2 alone will eat up a lot more space.

In any case, my main question really isn't "what's the minimum harddrive space I can put into WinXP" (though I welcome responses)... the main question is if I'd be better off with FAT32 or NTFS.

Is running this Maple story on Wine a possibility?  Then you wouldn't need crummy XP at all.  You've probably already thought of that.  I know next to nothing about games, but just thought I'd mention it (athough even if you could you'd probably take an unacceptable performance hit, dunno).

The real min. disk space reqs for XP are (IIRC from last time I installed XP) ~ 2 GB.  But that's before the sp2 and updates.  It also depends on how much space you allocate for swap, sys restore, hibernation, the defaults for which can really eat up a big chunk of space. And on top of it all you need to leave 15% free for defrag to run properly.   What I'd do if I were you is play it safe--give it 3-4 gigs initially, then turn all the above mentioned stuff down to the absolute min (disable hibernation entirely), and see how much space you have left over.  Then use Gparted on the ubuntu live cd to shrink the XP partition down to free up the max amount of space for ubuntu install.

Use NTFS.  FAT32 is an inferior file system (i.e. above-mentioned file size limit, easily fragmented, security, etc).  The ntfs-3g driver will give you read/write access from linux.

---

### Post by digital_exhaust on 2008-03-03
I would recommend NTFS. And really, your going to want at least 10g for your XP install.. by the time you get SP2 installed and all the other updates, you'll need the space.

---

### Post by logos34 on 2008-03-03
> **digital_exhaust said:**
> And really, your going to want at least 10g for your XP install

You don't need THAT much space...my last install with ALL the updates, sp and apps/programs (quite a lot too) was under 10 gb! (actually the partition was 9.77 gb and used space ~75%.  I had all the sys tools turned down to min.)

Remember, he's not putting ANYTHING on XP except av and the game.

---

### Post by Th3Professor on 2008-03-03
The first time I had both WinXP and Linux (or Unix, I forget which it was at the time), I put 10g into XP. It was unnecessary.

The last time I had both WinXP and *nix, I put 8g into XP. Even then I had some space to spare.

(In both situations, I had XP up to "SP2", I installed an anti-virus app and a couple anti-spyware apps, and finally I had installed Maple Story... that's with the 8g WinXP partition.)

Microsoft says the XP OS takes up 1.5g... I found somewhere else that it'll help to reserve 3g just for the OS (maybe that's after SP2 and all the other patches).

Something like AVG Anti-Virus Free Edition is supposed to take, I think, only 30 MB. Anti-spywares like Spybot S&D is supposedly 12 MB, and Ad-Aware SE Personal something like 50 MB.

It looks like Microsoft's requiring 500 MB for the actual SP2 package, adding up to 1 gig during "peak installation", an additional 260 MB for something they're calling "working space", an additional 200 MB just for the "files that remove SP2" (sheesh!), and an additional 30 MB free space on the first primary partition (aka install XP before Ubuntu). That 1 gig "peak install", my guess, is just that (not required otherwise, aka after SP2 has been installed, so I'd install my game after SP2).

The game Maple Story is supposedly 1.5g, and they say consider having 3g available.

Conservative space for XP+SP2+AV/etc+MS(game)...
5gigs.

(But would 5g work?) :confused:

More flexible space for all of that...
8gigs.

(I already know that works... trying to trim it down some more.)

All of that is including SP2's temporary 1 gig "peak installation".

So I wonder if I put MapleStory on absolutely last, if I could cut it down 1 gig. Maybe I should have 3 gigs available for Maple Story's install, though it might only be a 1.5g game. Theoretically that takes me down to 7g but then up to 8.5g (the +1.5g for the game's install process). lol this is silly.

Well I *know* from experience that 8g is more than enough, I just don't remember how much wasted space I had afterwards. So I know I can go less than 8g, just don't know how much less. Blah.

Anyway, my main question, regarding file systems...

I'll go ahead and go with NTFS. :) Thanks all for the input. :)

---

