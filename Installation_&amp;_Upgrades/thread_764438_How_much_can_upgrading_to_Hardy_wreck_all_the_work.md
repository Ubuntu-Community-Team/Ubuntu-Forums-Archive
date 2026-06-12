---
title: "How much can upgrading to Hardy wreck all the work I did to get Gutsy working?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by tomsa on 2008-04-23
I am running Gutsy on a Gateway t-1625 laptop.  It took me quite a bit of time to get audio, restricted video drivers and my bloody rtl-8187 wireless card working.  I'd like to upgrade, but I'm concerned that when I do all of the work I put into getting this computer working will be lost and I'll have to start all over again.  Is there anything I can do during the upgrade process that will prevent me from losing all the work I've already done? (I'm talking function here- I'll backup my files and such)  Please bear with me for the dumb question, but I have only been using linux for a few months and I have only done fresh installs of Gutsy- I haven't done a system upgrade yet.  Thanks for your input.

---

### Post by Pumalite on 2008-04-23
I upgraded from Gutsy for testing purposes and everything went OK. But, look around, upgrading is not a sure thing. You have to eliminate all third parties from your sources.list among other things. You might have to reconfigure your xserver, etc. I prefer a clean install.

---

### Post by iaculallad on 2008-04-23
I second to the clean install. Hopefully, upgrading to Hardy could support your wireless and video driver. After all, nothing is impossible to search when you have the internet in your hands :-)

---

### Post by tomsa on 2008-04-23
How do I remove the third party sources, if I were to go about it that way?  Is it a comand line only thing, or can I do it through the GUI?  It's not something I have had to do yet in my limited experince with linux.  I suppose after a few weeks there will be a howto with regard to upgrading (I have seen the one on Ubuntugeek), but I'd like to do my research first, forewarned is forearmed and all that.

---

### Post by tomsa on 2008-04-24
I thought of something else-my laptop is curretly dual booting vista and Ubuntu.  I am using Easy BCD to manage the bootloader through vista because apparently vista does not dual boot well with others.  Have you heard anything about dual booting vista and Hardy?  I know very little about Wubi, as it seemed to be of no concern until a moment ago. Is that a potential solution? I'd really like to not wreck my vista partition too- as it was just as much of a load of trouble to get to work.  Do you think that I could potentially just upgrade, and then edit my bootloader entries in EasyBCD- or will there be other hoops to jump through?

---

### Post by tyblu on 2008-04-24
Whatever decision you come to, perhaps wait a week or two for the first few first-release bugs to be worked through to give yourself a better shot at smooth seas.

---

### Post by omegamormegil on 2008-04-24
In my experience with Ubuntu upgrades, they have gone shockingly smoothly.  I plan to upgrade, as opposed to reinstall, from now on.

Nothing like a windows upgrade.  When you are upgrading Ubuntu, for the most part it just removes the old package, and replaces it with the new one.  Everything is modular, so it works really well.  

Hardy has a lot of improvements over Gutsy, and it is likely that at least some of the hoops you had to jump through to get everything working in Gutsy will be done for you with the upgrade/install.  

I would recommend trying the liveCD to see what does and does not work before you upgrade.  This will give you a very good idea of would work "out of the box" with a fresh install.  

Also, I've been running the Hardy Alpha/Beta/RC since February, and it has been of surprisingly high quality.  All of the issues that bothered me have been fixed.  

To sum up, I expect you will have a good experience if you choose to upgrade, or to do a fresh install after backing stuff up (a separate partition for your /home folder works wonders if you do a full reinstall, btw).  To get a preview of what you'll have when you are finished, try the LiveCD first.  

Good luck!

---

### Post by omegamormegil on 2008-04-24
Also, Wubi is amazingly easy to use to install Ubuntu from within Windows.  I'd recommend it for first timers - it makes the install REALLY easy.  I mean, much easier to install than say, MS Office.  

And according to the Wubi Guide ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)), Vista works well!  Go for it!

---

### Post by frodon on 2008-04-24
Take 15 minutes to make a ghost of your partition and keep your piece of mind ;)

You can still restore your system like it was before from your ghost image if you are not happy with hardy.

Common linux apps for this purpose is partimage, not that the partition you backup must be unmounted so the best way to make/restore a ghost image is to use a live CD which contain partimage.

---

### Post by Pumalite on 2008-04-24
Here you have a guide if you decide on the dual boot:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by tomsa on 2008-04-24
This is all really great information!  I just installed the Hardy Release candidate on an older box that we're giving to my daughter last night.  When I bought it from my friend he included a linksys (wpm300n) wifi card, and honestly, I was hoping that I would be able to use it instead of running network cable into her room.  After about an hour or so, I was able to get it working with ndiswrapper and the drivers in its CD.  Needless to say, I'm already feeling better about Hardy.  I understand that this may not be the case with my rtl8187 card on my laptop, but I still feel better about it.

I suppose I should get to the point here- can you direct me to a good howto or two about using partimage?  I can just google it, I know, but I figure one of y'all must know of at least one that's really clear and well written.  I really like the idea of just being able to restore my system to where it was if I seriously wreck my computer. :tongue:

---

### Post by Pumalite on 2008-04-24
This might help:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Spenzer4Hire on 2008-04-24
Check out Clonezilla.  Super easy.

---

