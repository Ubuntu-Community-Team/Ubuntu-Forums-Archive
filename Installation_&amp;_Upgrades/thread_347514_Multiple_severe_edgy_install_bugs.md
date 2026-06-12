---
title: "Multiple severe edgy install bugs"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by ceverett on 2007-01-27
Last weekend some buttmunch stole my laptop with edgy loaded on it ... went right through a car window.  So, $1150 later I have a new laptop, case, USB audio card, cable, and wireless mouse (only thing Microsoft does right is mice).  

The new bittybox is an HP AMD64X2 Turion, with 1 gig RAM, 120 gig HD, an nvidia chipset including the graphics, a Broadcom 4031 wireless chip and a 1280x800 wirescreen.  

So, I download and burned the Edgy install CD and fired the sucker up.

First thing I notice is the install CD doesn't know about widescreens.  I should have taken this as a sign of things to come.

But, fool that I am, I click the installer icon.

Next up, Gparted.  Gparted separates creating partitions from assigning them to mountpoints.  Then when you go back and forth, trying to figure out which mount points to assign to which partitions it loses track of what filesystem I wanted to use (reiser) on the mountpoint I last brought up.  Finally, I give up and LET THE INSTALLER DECIDE FOR ME (Help! Help! It's computer rape!) how to partition the drive.

Once it copies all the packages, and I reboot, that's when I notice that the wireless isn't working.  When I go hunting for packages (I used to used wifi-radar for wireless roaming) I discover, there are no packages but the ones that got installed.  And I'm running a "generic" kernel instead of a AMD64 kernel, even though I downloaded and burned an AMD64 ISO.  Worst of all, I could find no way to invoke the character-mode installer.

Hey, I honestly expected some hassles setting up Ubuntu.  The widescreen thing didn't faze me because I'm used to dealing with oddball X11 configs (dualscreen, nvidia, etc).  I suppose I can't really be too pissed off at Ubuntu for not having fixed the Broadcom wireless (apparently NDISWrapper is called for), even if the issue has been understood for the last 6 months.

But Gparted is broken by design as well as flawed in execution.  It's not just bondage and discipline, it's fascist like a concentration camp guard ... no reason or thought behind it.
What's a generic kernel doing on a AMD64 installer?  And for a 700 MB download, where are all the packages?  And why-oh-why can't I find a backdoor to the character mode installer.

Guys, your installer used to be really nice.  It gave me pinpoint control when I wanted it and got out of my way otherwise.  This GUI installer is a massive step backwards.  Frankly, it's not even Microsoft quality.

Best Regards,

Christopher Everett

---

### Post by jberkes on 2007-04-24
Yes, I noticed problems with the graphical installer.  Other big problems are assumptions about the screen size.  If the video card is not recognized and you end up at a mere 800x600 resolution, you can not even see the button in the GUI installer dialog.  There is no way to carry out the installation without a text mode install!

---

