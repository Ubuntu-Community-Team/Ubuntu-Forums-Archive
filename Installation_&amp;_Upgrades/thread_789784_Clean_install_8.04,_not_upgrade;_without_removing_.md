---
title: "Clean install 8.04, not upgrade; without removing 7.10!"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Neobuntu on 2008-05-10
Many have the new release itch before we should scratch it. If you want superior stability and everything working, I recommend waiting until about 3 months **after** a release is official. If you can't wait (like me) then here is how to scratch the itch safely. Because you just might be in the group that doesn't upgrade well. This is how I took the plunge (slightly earlier than my recommended 3 months after and 3 months before the next, coming, new Kubuntu release.)

This is both a strong recommendation (hint) and also, simply my notes on how it went for me. It will include my optimizations after the (rich) base install. Possibly, a bit of unabashed comment thrown in, for some spice. :)

This my main system (Dell D8200 desktop with added Nvidia) had (only) gusty 7.10 and plenty of hard drive space (200GB).

I choose the **K**ubuntu, 8.04, **live** desktop, i386 CD. Even though the "Alternate" CD can be more needed in special cases. I wanted to see the live one.

I like the new option to go right for the installer. I did that only to be **hung**; at trying to read the "release notes". (opps). I rebooted (easy enough) and ran the live from CD Kubuntu to check general compatibility. It was fine and summarily I ran the installer again and this time, staying far away from the "release notes" link. Gee!

I am well pleased that the installer recommended a 50/50 split of my old, large, Kubuntu ext3 partition. I said yes and it worked away but then **HUNG!** I had to waste time being patient, hoping it was doing something important but after what I know to be far longer than the job takes, I rebooted.

Now this is where it's sad; for the really green newbies and I weep for them. I pray they don't miss the on-going goodness; because of this install glitch.

Then, the installer kindly wanted to split the first successfully split partition again and luckily I caught that! So I marched forth into the "manual" partitioning. This went very well as I have done that before. It's as easy as (manual) gets. It seemed the old, big partition that contained my precious (7.10) had indeed been properly split (and turned out intact) but the new second half (before the small, common swap partition) was not formated. I formated ext3, called it "/" and off we go to finish the install without any other to do (save the defaults and passwords etc).

100% success. The point is. I did NOT kill my old install. You shouldn't either at this point. You might have to go back to it for some odd reason; until a few more inter-release updates come forth. It's a no risk game. Get it? i do not consider a new release of (K)ubuntu stable until about 3 months after it's official release.

Oh and why the KDE of Kubuntu. Why not? Gnome's fine too but I think KDE is better. Duck! Seriously, I think XP converts will like Kubuntu a bit better. KDE is not supposed to be second class to Gnome, in the Ubuntu family. Yet, why does it feel that way? Hmmm? I wonder why the kubuntu.com site doesn't match the detail and "front door" atmosphere of the ubuntu.com. I not trying to start a fight, really. I'm just saying that the Kubuntu site, could use some work. (Constructive critic to GNUnaw on.)

UPGRADES:

I like to have a hard wired Internet (Ethernet) cable plugged into the box for upgrades during the install. Still, their were upgrades to do after the install and I did them. The closer we get to my 3 months, after the release, the better these upgrades stabilize your system and the better everything "just works". 

Inter-release upgrades like this are a huge reason to use (K)ubuntu. Conversely, I **DO NOT** recommend the dist-upgrades or "managed" release upgrade, over a clean install. Conversely, those can have many more problems, even if some people squeak by. I think it turns far to many people away (early on) and wastes far more time, IHMO. That stuff is only good when your system is so many releases behind, that it doesn't matter. You don't want to start with the wrong foundation and wind up being many orders of magnitude displaced from the rest of the (K)ubuntu world. Especially when fixing or adding something else, on to (K)ubuntu.

Optimizations (and stuff):
(My notes:)

I like to set automatic login as I use One user.

I added the Termnal icon to the panel.

I installed the Nvidia driver per the neat icon on the panel.

Opps! I could only then set 800x600, so that's not cool. Plus, I could not do my geek trick of "sudo dpkg-reconfigure xserver-xorg" and set the resulution(s). That part seems to omitted. I'm sure there's some new way to do it but darned if I know what it is. A newly generated "xorg.conf" setup file is in order. I cheated, I copied my old one from the other (Gusty) partition.

**Note: Having the other, old, Gusty partition is a boon for grabbing your data! Yet, it is [B]NOT** a solution to avoid doing your backup first! Backup everything you can't live without and keep two copies.[/B]

I installed Firefox and got version "3".

I configured the clock (why?). I set my country and made the PH in time setting pH so that 5:00pm would not be 05:00pm. 

I added the Kubutu "restricted" extras from the easy "Add Programs". This for Flash and stuff.

I'm currently working on installing mplayer or something so that I can (again like in Gusty) play QT movies from my digital camera cleanly; from the Digicam application. See, this is the kind of thing that gripes me. I did it before, but now I forgot! You can rest assured that this is do-able and will be done (after Mothers Day). 

I added a few packages:

numlockx (desktops only, not for notebooks)
kmame (I'm not a kid - usually, but I have them!)
snes (for NES games and you should see the GBA game player, "VBA express" too!)
torcs (Try it and be a "real" race car driver.)
nvtv (TV out, testing)
Kmymoney2 (The Quicken killer)
Azureus
k9copy (when you have a DVD burner. Rip, Decrypt, shrink and burn.)

I plan to add "alien arena" and several other FPS that work very well without any to-do (with direct 3D easily setup).

Also, I am very **VERY** pleased that my specific (Panasonic FZ18 ) cameras "RAW" format, is now automatically (zero work) recognized and edit-able and right there, in Digicam no less! (For when I want to waste time trying to beat the jpegs that my FZ18 produces, LOL.)

I'm liking hardy a lot! We need to help those newbies. Remember the game is to get more users and they don't have to do a install. They are being cowed into just buying a new computer. This install thing **can't** be easy enough. Please consider what we can do about the glitches that I experienced. Minor for me. No so much, for others.

**Get out there boys! Thank your mama!**

God Bless you and thank you for Kubuntu!

---

### Post by code_linux on 2008-05-10
nice post... helpful! :KS

---

### Post by Neobuntu on 2008-05-12
Thank you.

I used:> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs... to get DVD and QT working. Digicam uses the Kmplayer and once we set the Kmplayer to use mplayer and not xine, my cameras QT movies play correctly (after easily importing them from my camera into Digicam)!

---

### Post by Neobuntu on 2008-05-13
I also did...> sudo apt-get install mozilla-mplayer so I could play some Quicktime trailers in Firefox.

---

