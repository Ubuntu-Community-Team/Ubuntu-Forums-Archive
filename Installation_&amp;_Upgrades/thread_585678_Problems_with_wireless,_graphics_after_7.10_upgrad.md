---
title: "Problems with wireless, graphics after 7.10 upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Doofus Magoo on 2007-10-21
Howdy all; thanks for another great release. I upgraded from 7.04 to 7.10 this Saturday, and things seemed to go very well. It took a few hours, I rebooted, and was on my way.

This morning, however, I came downstairs, putzed around a bit, rebooted (don't remember why, but I think it was to reconfigure Apache to listen on port 808 (since my ISP blocks incoming port 80 traffic)), and now I'm having issues with both my graphics (Nvidia card, natch) and wireless networking. This may or may not have anything to do with the upgrade, but given the coincidental timing (and the fact that I'm using ndiswrapper + proprietary nvidia drivers), I can't help but think there's a relation between my having upgraded and the problems I'm now having.

Since I think I'm closest to fixing the display problem, I figure I'll focus on getting that one resolved first. When I boot up initially, I get stuck in a loop of "Ubuntu is running in low-graphics mode," at which point I click "Continue." Eventually, I'm able to Alt-F2 to a login prompt, and after loggin in, I get the "Failed to start the X server" error (failsafeXServer, too many arguments on line 47) and get dumped to the CLI.

At this point if I sudo dpkg-reconfigure xserver-xorg from the command-line, accept all the default values (nv driver), and then startx, I'm taken to my old desktop (hurrah!). However, the next time I reboot I'm back at the same place I started (boo) -- low-graphics mode, X server not starting until I reconfigure and startx.

Any help on how I can this to permanently resolve itself (at which point I could move on to fixing the wireless issue) would be greatly appreciated!

---

### Post by Doofus Magoo on 2007-10-21
One more data point, in case it's relevant.

After I dpkg-reconfigure, and then startx, I can't do any administrative-type stuff (e.g., Restricted Drivers Manager) from the desktop -- I get a "Failed to run (whatever) as user root. Unable to copy the user's Xauthorization file" error.

---

### Post by GurneyHalleck on 2007-10-27
I'm also having trouble with "Ubuntu is running in low graphics mode", but I'm using a Radeon 9700 Pro.

Things were fine after I upgraded. It's only since I disabled the proprietary ATI driver, then re-enabled it that things have gone awry.

No matter what I try, I can't get rid of this error, and I'm permanently stuck in 800x600 mode.

Is there a way to repair the graphics system configuration in Ubuntu, because none of the settings I've tried in the Administration menu have fixed this.

---

### Post by GurneyHalleck on 2007-10-27
Ah, got it fixed, thanks to an online review. The reviewer had the same problem once he'd tried to enable proprietary drivers (this time for an nVidia card), and he offers a solution to repair the graphics configuraion:

[http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/](http://technical-itch.co.uk/2007/10/19/ubuntu-710-upgrade-first-impressions/)

NOTE: Once you stop the gdm service, you will lose your deskop and be dropped to a text-only login prompt, which means you won't be able to see your web browser any longer. So write down the commands (there are only three of them) otherwise you'll have to swear a bit and reboot like I had to.

The X server configuration tool is a bit of a relic of years past, but once you've chosen sensible options, it will rewrite the x.org configuration file and you should then be able to run Ubuntu with decent graphics modes again.

---

