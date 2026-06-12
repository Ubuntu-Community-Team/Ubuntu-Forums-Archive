---
title: "Yet another ATI driver thread"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by two4two on 2010-01-13
This may have been beat to death, but here goes anyway.  I didn't know if this was the right forum though, so if I'm wrong just tell me and I'll post it where you tell me to.  I wanted to get better use of my Radeon 9800 Pro with All-In-Wonder.  I tried the restricted-proprietary driver that came with Ubuntu and got a little of what I want:  I could get better resolution and rotate the screen, etc., but still no use of the MPEG hardware decoder.  Now, my account was the only one that had use of that driver and those features -- all the other accounts still had only the generic driver and limited features.  I saw that ATI has its own drivers called "Catalyst".  They said it wouldn't support the vid-cap part of the card, but I assume it would support the hardware MPEG decoder part of the card, and that was my goal in looking for the ATI drivers.  So I downloaded the one they pointed me to:  V9.3 (that was actually confusing because if I searched on Radeon it lead me to V9.1 but said all AIW variants are included;  if I searched on AIW it lead me to the legacy driver which was called V9.3 and included my 9800 Pro AIW.)  It said Ubuntu was one of the supported distributions.  I followed their instructions to use the GUI and came to a screen that showed only 2 supported distributions and Ubuntu was not one of them, so I went to another page that gave me a choice to do automatic (which was taking a chance) or generate packages for my specific distribution which was Ubuntu 8.10.  It generated about 5 pakages.  So it told me to use apt-get to install them and I did.  Then it said reconfigure XORG and I did.  Then I rebooted and guess what:  black screen.  So I boot into recovery mode and remove the packages and reboot.  Great -- at least other people can log in and get the same generic driver with its limited features as they did before, but with my account (the one that did the install/uninstall) I get a screen with a mosaic of color patterns and lines.  The mouse and keyborad appear to be working because when I use them the pattern of colors and such changes.  So something got hosed in my own user config.  What to do to find out what is wrong?  And what to do to get back to the very beginning?  We have a lot of stuff in here we don't want to lose.  How to save everything and re-install?  Or maybe delete my account and create a new one for me?  (We have more than 1 admin account.)  What to do?

---

### Post by Mark Phelps on 2010-01-13
Well, the first thing I would suggest is to not run everything in your thread into one big blob of text.  Hard to read.  Hard to follow.

Second, what part of hacking around with the X-server did you think was a GOOD idea?

If you're going to hack around with stuff that basic in Ubuntu, you need to learn how to make full image backups, because, considering the damage you have done, it may be the only way to get back to where you started. Recommend you check out using Clonezilla in the future for doing full disk/full partition backups and restores.

The fact is that your card is too old to have any current ATI Linux drivers.  The ones you're talking about date back to May of 2009, and as you have discovered, require breaking the X-server in order to get them running.

My advice is to consider one of the following:
(1) replace the ATI drivers with open-source -- and just live with the shortcomings.  You will get decent video, some special effects, and minimal acceleration.
(2) replace your old video card with something newer that WILL work with current Ubuntu versions.  In the ATI world, this means an HD 3x/4x/5x card.

---

### Post by two4two on 2010-01-14
Thanks Mark for reading my post and for offering some help.  I am running Ubuntu 8.10.  From the reading I've done 8.10 does support the ATI V9.3 ATI proprietary drivers.  

    I don't want to replace my Radeon 9800 All-In-Wonder.  I have an older Athlon 64 processor on an older Asus K8V-X board.  I have a triple-boot with Win98SE, WinXP and Ubuntu 8.10.  It is an AGP board and the 9800 is the best AGP 8X non-NVIDEA video card I could find for it (NVIDEA doesn't work very well with Asus boards using VIA chipsets), and considering it has a vid-cap and hardware MPEG decoder I like the card very much, but it is the best my system will handle.  This is why I wanted to start shifting over to Ubuntu.  Microsoft loves to keep pushing you into buying their latest and more hardare-demanding software and they do it by dropping support and forcing hardware and software developers to do the same, thereby forcing you to upgrade both software and hardware.  One big cabal and monopoly.  

    I don't need to upgrade my hardware and I absolutely don't want to upgrade Windoze because I don't like their Big Brother survielance and control.  I can't just yet get totally rid of Windoze because I have masses and masses of music recorded in my home studio in a proprietary format that I'd need to convert before making the cutover.  I saw Ubuntu as a way to get away from that control and do things I want to do.  I am using Audacity now to do new things because Ubuntu supports my M-audio 1010, but for now I still need Windoze to handle my old music.

    So. back to the ATI card.  Hacking around Xserver?  I followed the ATI instructions and I saw that others had been successful with the V9.3 ATI Catalyst drivers in 8.10.  I'm just asking why other users of this computer can login with their account and they somehow get the generic driver and at least be able to get at least limited functionality, but my account gets a screwed up screen.  

    I'd like to be able to fix my account and get what the other users get.  I initially went into the restricted drivers menu and installed that which came with Ubuntu, but it didn't support the MPEG decoder part of the card.  Then I saw that ATI's V9.3 Catalyst drivers were supposed to support the MPEG decoder (but not the vid-cap, which is OK), so I downloaded them and followed instructions.  That gave me the black screen.  I booted in recovery mode and removed V9.3 packages and so I get the screwed up screen.  

    Is there some file that keeps a config for which video driver they're using for each user?  Maybe I can edit that to look like the other users?  

    Or, Is there a way to set a boot option to use low graphics mode so that when I login to MY account I don't get the screwed up screen and then I can remove whatever driver is messing me up?

    Thanks for reading.  I appreciate whatever help anyone can lend.

---

### Post by Mark Phelps on 2010-01-14
Sorry, missed the part about you running 8.10 -- didn't see anything in the large blob of text mentioning that.

And in that case, you're right, you don't need to do anything to the X-server because that version DOES work with the ATI Linux Catalyst v9.3 drivers for the legacy cards.

The All-in-Wonder cards, from what I recall, require at least three different downloads from ATI to work. One is the driver, another is some WDM stuff, and the third one I don't remember.  But the gist of this is that most probably, only the basic video drivers will work in Linux; most probably, the other two will not.

Have you tried using EnvyNG?  When I was using 8.10, I found it a greate help in installing and uninstalling the ATI drivers.  Suggest you try it.

The other option is that the ATI drivers provide an option of building .deb packages for your machine.  I've had better luck using those than with just trying to build the drivers.

---

### Post by two4two on 2010-01-14
Thanks again Mark.  Actually, on my original post I think I forgot that little detail about using 8.10.  I haven't tried  EnvyNG.  Where/how to I get that?  Now, I did use the downloads from ATI's capability to build the deb packages, and it built about 5 of them.  I installed all od them (thinking they had so many because it has TV out, TV Tuner, remote control, vid-cap and MPEG decoder.  But vid-cap isn't suipposed to be supported so I don't know what the 5th one was for.  I'm going to look into the Envy method.  Thank you for your help.  I put two other admin accounts on this machine, so it's not like I can't use the machine.  I'm just a curious type who'd like to be able to use everything I've got.

---

### Post by two4two on 2012-05-08
Of course, this thread is solved.  How to mark it as such?

---

