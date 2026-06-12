---
title: "Upgrade 8.10 to 9.04 niggling problems"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Tootler on 2010-03-02
I first installed Linux near the "expiry" date of 8.10 so I did not update at that time as I was still getting used to the system. I have decided now to update so updated to 9.04. The update went OK but there were a few problems. Most I have managed to resolve but there are two niggling problems that I can't see how to solve.

[LIST=1]
[*]On booting up, the volume control is muted. It does not matter what setting it was when I shut down, it comes up muted at start up nor does it matter whether I start up from "cold". I have looked in startup applications and sound settings and cannot see a checkbox there which I need to check/uncheck. I also looked in other vaguely likely items in the System menu but nothing. With 8.10 the volume control "remembered" the setting it had on shut down. How can I set this in 9.04 - and also for the future as once I have everything sorted in 9.04 I intend to go on and upgrade to 9.10.

[*]I have Qsynth/fluidsynth installed as I need a midi synth to playback files in a music notation editor I run in Wine. When I upgraded, Qsynth began to start up on booting (Previously I used to have to start it manually). This is not a problem in itself but it seems to interfere with the startup of the HPLIP device manager for my printer. During startup, I get a message box from the HPLIP device manager to the effect "Unable to find system tray, device shutting down" and it does not load which is a nuisance. I have removed Qsynth for the time being but would like to reinstall it if I can ensure that it does not start during startup, but I can start it manually when I need it.
[/LIST]

---

### Post by SnickerSnack on 2010-03-02
Is there are reason that you have not upgraded to 9.10?  It may be that those problems will be fixed by upgrading, or that you'll fix them in 9.04 and then they'll be broken again when/if you upgrade.

If you want to fix this in 9.04, then I have an inkling of what you need to do, but it'd be best to wait for someone with more experience to help you.  I might give incomplete or outright bad advice.

---

### Post by Tootler on 2010-03-03
> **SnickerSnack said:**
> Is there are reason that you have not upgraded to 9.10?  It may be that those problems will be fixed by upgrading, or that you'll fix them in 9.04 and then they'll be broken again when/if you upgrade.

The main reason is time. Along with upgrading I needed to reorganise my hard disks - mainly to shrink the windows partition and expand the linux one. This also involved making parallel changes to the external hard drive I use for backup. All in all it took me nearly 3 days to get everything sorted, backups done and the upgrade completed and I needed to get on with other things. 

Also by sorting out these problems now, I will know how to deal with them in future and can get things up and running properly more quickly. The major problems I had, I had had before when I moved my Wubi installation on to a dedicated partition but had forgotten how I dealt with them and wasted time finding the solutions. This time, I am saving the solutions as I go so that I can deal with the problems more quickly and waste less time.

Cheers

Geoff

---

### Post by Tootler on 2010-03-05
Bump

No one any suggestions?

---

