---
title: "Should I upgrade / fresh install 14.04 &amp; what about linux mint?"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Peter_Brandon on 2014-04-19
About a month ago, I decided it was time to start upgrading from 12.04 on my home computer, which is a laptop.  Upgraded to 13.10.  Have been having problems ever since.  I've not been able to get wifi working.  When I use LibreOffice, the top and bottom panels disappear (am using Gnome Classical; unity doesn't work at all) and  mouse clicks stop working periodically.  When the computer freezes, which happens a fair amount, and I hard reboot, audio stops working and takes hours to repair.

I'm usually reluctant to go to the latest Ubuntu release because I figure it takes a while for the worst bugs to get fixed.  Anyone think 14.04 right now would be more stable than 13.10?  I wonder whether some of the problems I've been having are due to not doing a fresh install instead of upgrading?  The downside of a fresh install, though, is that I have a lot of configuration and software added to the machine.  Also, my Ubuntu was installed as a dual boot with a complicated partition system--not sure how readily I can install on top of that.  Thoughts?  Would you go the fresh install route?

Am also wondering whether people recommend Ubuntu or Mint?  I need access to a complex file structure, so gnome-search-tool is more useful to me than unity search--though I also have Docky (smaller, moveable icons) and Synapse installed.  I strongly prefer Gnome Classical to 12.04's Unity, tho don't know this will be true for 14.04 Unity.  Gnome-search-tool is showing problems in Ubuntu.  Would Mint make more sense for someone like me?  Would it be harder to install on a dual boot?

Opinions appreciated!

---

### Post by Double.J on 2014-04-19
Hi there!

sorry to hear about the problems, was this an upgrade to 13.10 or a reinstall? Generally a clean install will have less errors. I would advise to try them; download and create live USB's to try them out.

mint's cinnamon is more like the old gnome 2, but you can also install MATE, which  was created as a fork of gnome 2 on ubuntu (remember that gnome 2 is now unsupported), and just to throw in lubuntu if the machine suffers with unity due to age.  

Regard mint; what's important is that it's 99% Ubuntu! Also factor in that their default cinnamon desktop is no longer a front end to gnome, but rather a complete DE of its own. This may impact your  decision.

At the end of the day, they are all built on the ubuntu base. I would advise downloading lubuntu, xubuntu and mint (MATE edition recommended -if unity struggles with your hardware, cinnamon may be a push) just to see how they perform. A reinstall sounds like a good idea based on the unexpected issues. Downloading default Ubuntu with unity doesn't seem like a good idea if your graphics card already struggles. Ubuntu Gnome is likely to encounter similar problems to unity ubuntu as unity is a front end to gnome 3.

As they are all built on ubuntu, there is no increase or decrease in difficulty (mint even uses ubuntu's ubiquity installer) so it really just comes down to preference! I'd advise experimenting to see what works best for you!

Jj

---

### Post by Peter_Brandon on 2014-04-19
Thanks Double.J!  

I've been looking into this for a while now.  It does seem like it'll be time consuming to do a clean install.  

That looks like an argument against shifting to Mint.  It's not entirely clear to me, but it sounds like you *have* to do clean installs with Mint (between major distros?) or is it simply that they recommend doing that?  And, is it that they recommend doing clean installs because upgrades cause more problems than in Ubuntu or because upgrading is equally problematic?  

I don't entirely know, but it looks, from my experience, that clean installs avoid problems that can all but make a system unusable.  On the other hand, they are very time consuming for me.  So, my best option seems to be to go with whatever has a recent LTS version, which would be Ubuntu (Mint doesn't have a 14.04 based version yet).

My graphics card can more than handle the load from Ubuntu; but the proprietary driver causes problems (e.g. system freezes when I have a flash drive plugged in and try to suspend, but only when the separate graphics card is enabled).  May be some graphics problem behind my disappearing panels.  Not sure what though.

---

### Post by pfeiffep on 2014-04-19
> **Peter_Brandon said:**
> About a month ago, I decided it was time to start upgrading from 12.04 on my home computer, which is a laptop.  Upgraded to 13.10.  Have been having problems ever since.  I've not been able to get wifi working.  When I use LibreOffice, the top and bottom panels disappear (am using Gnome Classical; unity doesn't work at all) and  mouse clicks stop working periodically.  When the computer freezes, which happens a fair amount, and I hard reboot, audio stops working and takes hours to repair.

I'm usually reluctant to go to the latest Ubuntu release because I figure it takes a while for the worst bugs to get fixed.  Anyone think 14.04 right now would be more stable than 13.10?  I wonder whether some of the problems I've been having are due to not doing a fresh install instead of upgrading?  The downside of a fresh install, though, is that I have a lot of configuration and software added to the machine.  Also, my Ubuntu was installed as a dual boot with a complicated partition system--not sure how readily I can install on top of that.  Thoughts?  Would you go the fresh install route?

Am also wondering whether people recommend Ubuntu or Mint?  I need access to a complex file structure, so gnome-search-tool is more useful to me than unity search--though I also have Docky (smaller, moveable icons) and Synapse installed.  I strongly prefer Gnome Classical to 12.04's Unity, tho don't know this will be true for 14.04 Unity.  Gnome-search-tool is showing problems in Ubuntu.  Would Mint make more sense for someone like me?  Would it be harder to install on a dual boot?

Opinions appreciated!

I have found that 14.04 is extremely stable on both my machines - I never used 13.10 only 12.10 & 13.04. 

> [COLOR=#000000]Regard mint; what's important is that it's 99% Ubuntu![/COLOR]

Debian is the backbone of Ubuntu, Linux Mint 16, and Linux Mint Debian. 

I believe a fresh install is preferable to an upgrade ... you may spend a bit more time getting the OS configured to your liking, but there won't be too much trouble shooting. 
A complicated file structure can be accommodated by choosing something else at install time and choosing to format or not existing partitions

---

### Post by rosswmcgee on 2014-04-19
I tried the Beta 14.04, I tried the final release many many times could install it but it would not work. Whenever I moved a mouse or if occasionally I was able to log in

the screen would go jagged red with no desktop. I tried new dvds from different mirrors, no dice. If I were to try again and I won't I would try upgrading from 12.04lts 

because a clean install would not work on this computer. I can install Fedora, Fedora mate, PC linux and any version of mint but not Ubuntu 14.04 lts.  I spent 3 days trying, just because

I like a challenge. Finally gave up. 

I just installed Mint 16 petra. installed like a breeze. Sorry to say I take 99% vs. a flawed distro.

---

### Post by Double.J on 2014-04-19
Hi there,

glad to hear you've had some progress with mint. It does sound like a graphics driver issue. Hopefully there will be no issue upgrading your mint install to mint 17 when it releases in May, however as stated, whilst cinnamon is a totally different de, the underlying ubuntu is the same. If the issue does come back, the driver would be the place to start based on your description.

Jj

---

### Post by Double.J on 2014-04-19
> **pfeiffep said:**
> Debian is the backbone of Ubuntu, Linux Mint 16, and Linux Mint Debian.

I meant this as a guide only - Debian is the top of our stream, but it's difference in OS and ideology of implementation is actually quite a diffence to the end use from ubuntu, whilst mint is very similar, with differences that come down to taste. Linux mint debian Edition highlights this difference when compared directly to standard mint.

---

### Post by Peter_Brandon on 2014-04-20
Well, I spent time looking at different OS's and decided my safest bet would still be Ubuntu.  Mint might have been possible if they had a new LTS version.  Below, I detail some of my experiences and recommendations for installing 14.04, Unity and KDE.

I did a clean install to Ubuntu and am now running Unity and KDE as desktop options.  Unity has gotten much better since I last tried it in 12.04 and looks like it would be useful for day-to-day activities.  A number of pleasant surprises and glitches (more below), but overall looks like it's functioning beautifully and is quite stable.  KDE seems to be a solid alternative for complex work situations, but I have still to adequately explore it.

Has basically taken my weekend to do the clean install, get my non-standard software in place and functioning, and deal with various glitches.

Despite my partition complexity, the Ubuntu installer worked, sort of.  The partition screen in the installer uses GUI behavior that is not intuitive or explained.  Fortunately was able to find a page giving clues about how to use this.  Everything seemed to go fine with the install, but when I tried to start my new system, the boot loader failed.  Had to install boot-repair on my installation USB to repair my installation.  So, the Ubuntu installer didn't quite get things working.

THE GOOD
Pluses of 14.04:  Problems I had seem to be gone.  System seems stable.  Beautiful interface.  More configuration options for Unity (can make launcher icons small, can get menus back onto windows).  Was able to work out how to make file searches more powerful than Unity alone:  can put gnome-search tool in unity & use it as "Search for Files" also can add Recoll, a within file search package that seems a lot more powerful than the usual Ubuntu tools for this.  With this setup Unity may prove practical for me.  Had rather few problems adding a long list of my favorite software.  Things just work.  Also, unless I'm mistaken, power usage is down by a good margin from from 12.04.

THE BAD
Flash doesn't work in Chromium; but fixed the by installing pepper flash.  Flash videos with DRM still don't work (I was trying Amazon), but fixed this at least for Firefox by following the instructions for installing Ubuntu 13.04 version of hal package.  The instructions are here:  [http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video](http://askubuntu.com/questions/362259/how-to-watch-videos-in-amazon-prime-instant-video) .  Why on earth did Ubuntu decide to remove hal when it's essential in this way?  I can only hope the old libraries continue to work.  An option is pipelight, but I gather that has security vulnerabilities and I'm a bit iffy on putting ppa's on my system.  

For the KDE desktop, I initially couldn't get the laptop to stop using dual windows with my large external monitor.  System settings seemed to think I had one continuous screen and wouldn't allow turning off the laptop screen.  Discovered this can be fixed by installing kscreen.  Again, odd that there's a kde-standard install that's supposed to load the entire KDE desktop to use that would leave out key functionality.  But, it's working and it looks terrific.

So far, I can recommend taking the leap out of Ubuntu 13.xx into 14.04, if your experience w/ 13.xx is that it was quite buggy.

---

