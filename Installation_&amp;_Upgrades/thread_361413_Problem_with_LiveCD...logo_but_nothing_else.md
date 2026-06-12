---
title: "Problem with LiveCD...logo but nothing else"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by wickstopher on 2007-02-14
Hello, there!  After a wonderful and simple experience installing Ubuntu on my own machine, I've been trying to help my friend install it on his old Dell OptiPlex GX1 after Windows XP ate itself from the inside out.  It's got 512MB RAM and a Pentium III processor (not sure on the specs for the cpu, forgot to check last time I was over there).   I have run into some trouble, however.  I've tried both the Xubuntu and Ubuntu liveCDs (both of which work flawlessly on my machine), and on both discs, when the system attempts to boot from the CD, I get the Ubuntu/Xubuntu logo, but none of the boot options that you normally see.  It just freezes at the logo.  The strange thing is, the Gparted LiveCD worked just fine on his machine, and we were able to reinstall XP (much to my dismay) from the microsoft disc.  So it's obviously not a problem with the disc drive.  I'm not too familiar with tooling around in the BIOS settings, so I'm not sure if that is where the problem lies.  Perhaps I need to try the alternate install CD?  I burned a copy, but I'm afraid it may present the same problem (i have yet to attempt it on his machine).

---

### Post by wickstopher on 2007-02-19
Well, as of yet, nobody has responded, but in case anybody is interested in a solution but hasn't had any advice to offer, I found somewhat of a solution.  Apparently, any CD using 6.10 edgy has a bug in it that makes it freeze up with certain graphics cards (particularly ATI, and this machine has an old ATI rage card or some such).  There is apparently a workaround to this, if you can get to the options menu, but I wasn't even getting that far.  I tried Xububntu (including the alternate install disc), Ubuntu, and more recently Linux Mint 2.2 Bianca, and got the same problem with all 4 discs (which worked flawlessly on my machine).  Xubuntu 6.06 did the trick, though.  Haven't installed it yet (it completely froze up and I had to shut down the machine when I tried to configure his wireless USB device on the liveCD, and no time tonight) but will be attempting it soon.

---

### Post by viper on 2007-02-19
Just a thought, could the cd rom drive be failing ?

---

### Post by wickstopher on 2007-02-19
No, the drive is fine.  Like I said, I installed XP just fine, and other liveCDs work fine.  It's just the Edgy Eft based distributions (Ubuntu 6.10, Xubuntu 6.10, LinuxMint 2.2 Bianca) that aren't working, and I'm fairly certain it is because of some issue playing nice with the graphics card.

The problem that I'm having with (all of) the 6.06.1 distributions (and I started another thread for this [here]("http://www.ubuntuforums.org/showthread.php?t=365060")) is that whenever I attempt to activate a wireless network connection, I get a total system freeze, which is no fun for anyone involved. :confused:

---

### Post by riggits on 2007-02-19
I had this problem too.  6.10 doesn't install on my machine & I've got a X600 Radeon card.
OpenSUSE works, Windows works, but no Ubuntu.
Alternate install doesn't help either.  Tried Ubuntu (i386, AMD64) and Kubuntu (i386, AMD64) with reg. and alternate discs.  Nothing works.
Any workarounds appreciated.

---

### Post by Ionix on 2007-02-19
Hi I am also having a similar problem.

I can see the menu when the livecd first boot up... but the ubuntu logo on the loading portion seems somewhat different from what i usually see.

Attached is a screenshot when my ubuntu 'freezed' and stop loading.

Notice the logo looks different somehow, and there is a "line" in the middle of the screen. This is always what that happen when ubuntu loads to the last block of the progress bar.

Can anyone offer my a solution? thanks

My system is P4 3.2Ghz, 1GB CORAIR RAM, ATI X800 Grahpic, and 250 Seagate SATA.

---

### Post by HellionDarkLord on 2007-02-19
If you really want Ubuntu 6.10 (edgy) then you are going to have to do some things that aren't very fun or easy.

What I had to do:  Install 6.06 LTS completely, upgrade using the live cd for Edgy while running Dapper, Reboot into failsafe from the boot menu and reconfigure the xserver-xorg. 

That got me to the point where I could do everything in the desktops except scroll upwards with the mouse or scrollbar because it messed everything up.  Then I attepmted to download drivers for my video card and found out that the only drivers available through the manufacturer were indeed open source, but only good for Xfree86 and not Xorg.  So I went through all the hassle to convert Ubuntu to xfree86 but in the end got nowhere. 

I did everything exactly as I was supposed to, and I know what I'm doing. After only a day of smooth running I tried to upgrade the system thinking to do some art with gimp and Whammo!! everything blew up on me.  I suppose that I shouldn't really have messed with it, but HEY I'm new to Ubuntu and have only tried a few times to really use the system.

I'm no expert, but I think that the xserver setup in Edgy needs some serious reworking because EVERYTHING works fine here in Dapper Drake 6.06 LTS

That's my piece.

---

### Post by wickstopher on 2007-02-19
I only wish that configuring a wireless USB device worked out of the box for 6.06 (and that's the only way he can access the internet, so until we can get that straightened out, linux just isn't a viable alternative for him).   I can't get Edgy to run on my friends' computer, but I can't get Dapper to configure wireless without total system freeze (not even on my own machine!).  Maybe Feisty Fawn will work come April....*sigh*

---

### Post by Ionix on 2007-02-20
Hi to all

My problem still persist with version 6.06 LTS too.

But gladly this time the clues about problem is more comprehended.

Flow (with attached screen shot):

I select boot LiveCD (6.06)
After it finish loading, this screen "Failed to start the X Server" appear.

The attached pics are the subsequence screen i saw before i was left with the terminal screen where i din do anything and type "reboot"

Please advise.

---

### Post by Ionix on 2007-02-20
*Bump

---

### Post by Ionix on 2007-02-20
*Bump

---

### Post by Ionix on 2007-02-20
*Bump

---

### Post by wickstopher on 2007-02-20
what's with the bumps?

---

### Post by BlackWoxs on 2007-02-21
> **Ionix said:**
> Hi to all

Flow (with attached screen shot):

I select boot LiveCD (6.06)
After it finish loading, this screen "Failed to start the X Server" appear.

The attached pics are the subsequence screen i saw before i was left with the terminal screen where i din do anything and type "reboot"

Please advise.

Can you post a copy of the log file /var/log/Xorg.0.log it might help get some ideas.

I'm far from an expert, however I had a similar problem with a ATI Radeon X600 on a Dell Dimension - I had to start with using the VESA driver. Ran

 sudo dpkg-reconfigure xserver-xorg 

after a similar set of screens and selected the vesa drivers.

---

