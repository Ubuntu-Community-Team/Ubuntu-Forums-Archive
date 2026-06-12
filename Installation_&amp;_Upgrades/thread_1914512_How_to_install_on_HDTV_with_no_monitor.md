---
title: "How to install on HDTV with no monitor?"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by latebeat on 2012-01-24
Hello all,

I have an old htpc which is running win7 and I want to reformat it and run Ubuntu on it. However, my problem is that I don't have an extra monitor and my TV is connected via component (doesn't support hdmi). :popcorn:
When I reboot and run the live cd I can see the grub menu as well as the bootsplash but as soon as the gdm starts loading I get a black screen. I know that the system is working as I can hear the ubuntu login sound in the background when the system finishes loading. My gpu is an old nvidia one.

So is there a way to install ubuntu without a TV monitor, just using my HDTV?

Any help is greatly appreciated!

---

### Post by cbanakis on 2012-01-24
you probably need to install the restricted nvidia drivers to get the component to work.

not sure how that can be accomplished.

Maybe do a re-install, and hit F4 at the boot options screen to enter safe mode, and install the driver then?

---

### Post by latebeat on 2012-01-24
> **cbanakis said:**
> you probably need to install the restricted nvidia drivers to get the component to work.

not sure how that can be accomplished.

Maybe do a re-install, and hit F4 at the boot options screen to enter safe mode, and install the driver then?
Hmm.. I really don't know how I could do that with no monitor. Is there no way to auto detect the tv and the fact that there's no monitor plugged in like windows does? I mean the bootsplash and the boot menu all work fine?

---

### Post by uteck on 2012-01-24
From the liveCD, try the menu along the bottom of the screen for boot options, I think it is F5 or F6 and select "nomodeset".  That should get things to show up on the TV.

If that works, then after you install Ubuntu you will have the same problem.  After the bios screen press the shift key to bring up the grub menu and then highlight the kernel and press 'e' to edit it and add "nomodeset" without the quotes after "quite splash"
To make this permanent, edit /etc/default/grub
then run update-grub

You may have to make an xorg.conf file to use after you install things since my TV is not detected properly over component cable and the system auto detects it as 1024x768. You should be able to Google for that if needed.

---

### Post by SeijiSensei on 2012-01-24
Does the TV have a VGA port?  That would be the easiest solution.

Some NVIDIA cards have a circular S-Video connector that works with many televisions.  If you have one of those, that would probably be the simplest solution.

---

### Post by latebeat on 2012-01-24
> **uteck said:**
> From the liveCD, try the menu along the bottom of the screen for boot options, I think it is F5 or F6 and select "nomodeset".  That should get things to show up on the TV.

If that works, then after you install Ubuntu you will have the same problem.  After the bios screen press the shift key to bring up the grub menu and then highlight the kernel and press 'e' to edit it and add "nomodeset" without the quotes after "quite splash"
To make this permanent, edit /etc/default/grub
then run update-grub

You may have to make an xorg.conf file to use after you install things since my TV is not detected properly over component cable and the system auto detects it as 1024x768. You should be able to Google for that if needed.

nomodeset worked like a charm!! Thanks a lot!
You were right, my resolution is improperly detected but at least I have something to start with!
Unfortunately the tv doesn't have an hdmi or vga port. That would make life easier indeed.

---

