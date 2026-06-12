---
title: "Cannot Boot After Update"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by birdboy30 on 2011-07-12
I recently installed Ubuntu 11.04 via wubi.exe to dual-boot between Ubuntu and Windows XP Home Edition. Ubuntu was the default OS to load on boot. I tried running a few updates in Ubuntu through the update manager, followed the instructions in the wizard, and restarted my computer when asked. The computer now automatically boots straight into the "GNU GRUB version 1.99~rc1-13ubuntu3 Minimum BASH-like line editing is supported..."

I have only just started to get into Linux. I have no idea how to get through this portion. I can't load back into Windows either (at least...I'm not sure how to. I never get the opportunity to choose which OS to launch). I've tried researching this issue, but still not having a lot of success. My only current option is to completely reformat my HD, but this is (hopefully) not going to be needed. If I could just get back into Windows I think I could probably reinstall with Wubi. Any suggestions? Please let me know if more info is needed.

---

### Post by bcbc on 2011-07-12
to get back to windows, see problem #1 and solutions #1 or #2 from the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198").

If you get a chance, please also run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

PS is that a grub rescue> prompt or just a grub> prompt. Did you also perhaps set the timeout (time to display operating systems) in the windows boot manager to zero and the default OS to boot as Ubuntu?

Any other info you can think of would be helpful as the problem you are describing (although common before 11.04) doesn't happen on 11.04 (not normally).

---

### Post by birdboy30 on 2011-07-12
I'm sorry. It may have not been Ubuntu 11.04. That's just the current build that I'm downloading to put on a flash drive (in case I need to reinstall). I downloaded the latest build about 2 months ago...so it probably was pre-11.04. Thanks for the update. I'm going to try looking over that thread as well.

I didn't make any changes to the boot timeout, but I do know that it was defaulted to load Ubuntu after about 20 seconds or so (if I didn't make a OS selection). I will dig a little deeper and get back asap. Thanks for the information!

---

### Post by bcbc on 2011-07-13
> **birdboy30 said:**
> I'm sorry. It may have not been Ubuntu 11.04. That's just the current build that I'm downloading to put on a flash drive (in case I need to reinstall). I downloaded the latest build about 2 months ago...so it probably was pre-11.04. Thanks for the update. I'm going to try looking over that thread as well.

I didn't make any changes to the boot timeout, but I do know that it was defaulted to load Ubuntu after about 20 seconds or so (if I didn't make a OS selection). I will dig a little deeper and get back asap. Thanks for the information!
That 20 second timeout would be fine. If you had 10.04 then definitely use the wubi megathread for the solution (Problem 1).

Once you fix that, look for the permanent fix as well (below problem 2) as that's known to occur after problem 1.

---

