---
title: "Problems in 12.10 after updating the kernel with nvidia proprietary drivers"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by tjajab on 2012-12-28
Hi,

each time I get kernel updates in 12.10 my graphics get all screwed up, one of the reasons being that I have the proprietary Nvidia drivers installed (the normal ones from the repos). So on reboot, all I see is a blank desktop in a low resolution, and I cannot see the Unity menu or interact in any way (except by right-clicking and creating a file of a type that when double-clicked upon may open some program I may be able to use in any way ;) ).

I have now found a way to fix the problem: Ctrl-Alt-F1 takes me to a text terminal, and after login I do```

uname -r (to see which kernel release I have)
sudo apt-get install linux-headers-x.x.x-xx
sudo apt-get install linux-headers-x.x.x-xx-generic
sudo reboot
```
where x.x.x-xx is the appropriate kernel release.

Still, this is a bit complicated and not so easy for the other members of my family. Does anyone have a permanent solution on this issue?

---

### Post by WierdKid on 2012-12-28
[http://ubuntuforums.org/showthread.php?t=1981213]("http://ubuntuforums.org/showthread.php?t=1981213")

I had the same thing, took care of it for me.

---

### Post by tjajab on 2012-12-28
> **WierdKid said:**
> [http://ubuntuforums.org/showthread.php?t=1981213]("http://ubuntuforums.org/showthread.php?t=1981213")

I had the same thing, took care of it for me.

I looked at the thread, but it didn't really seem to cover my issue, as my problems seems to be that the Linux headers are not installed alongside the new kernel, and so some of the proprietary stuff (Nvidia prop drivers, Virtualbox, etc) cannot recompile (or adapt?) to fit the new kernel.

My problem also has appeared only in 12.10, so the problem does not seem related to my issue. Thanks anyway for your suggestion!

Best regards,
Andreas

---

### Post by bogan on 2012-12-28
Hi!,**tjajab,**

If you also run: ```
sudo apt-get update
sudo apt-get install linux-headers-generic # as well as the cmds you listed
```And then 'remove --purge' the existing driver and re-install it, that should be permanent.

At least it will if the people responsible for this stupidity correct things for the next kernel update.

Chao,** bogan.**

---

### Post by WierdKid on 2012-12-28
Not sure as to the Virtual Box and stuff, but I know my problem was because of the proprietary NVidia drivers, the fix I linked to handled the NVidia issue, but it sounds like your problem might have other causes.

Note: My issue was on 12.10 but I'm on a clean instal of that version instead of an update so again it could be different.

---

### Post by Bobhuber on 2012-12-28
> **WierdKid said:**
> Not sure as to the Virtual Box and stuff, but I know my problem was because of the proprietary NVidia drivers, the fix I linked to handled the NVidia issue, but it sounds like your problem might have other causes.

Note: My issue was on 12.10 but I'm on a clean instal of that version instead of an update so again it could be different.
No its not different. The most ridiculous thing I have ever encountered is trying a clean  install  of 12.10 along with Nvidia drivers of any flavor and I have been using Ubuntu for years. Why this has not been fixed or even released like this is beyond me and I'm sure has caused a lot of new users to stay with Windows. Don't get me wrong I'm running 12.04 with Gnome 3 and it has turned out to be the most stable releases in many years of using Ubuntu. The original bug report on this issue was treated as an OH WELL and apparently still is.  Vent over.

---

### Post by WierdKid on 2012-12-28
Well if its the same issue, nomodeset gets you through the install, then that fix gets everything working just fine.

---

### Post by tjajab on 2012-12-29
Hi,

thanks all of you for your input. I will try to install the generic headers, reinstall the graphics driver and wait and see until the next kernel release. If it works then, I'll mark this as solved.

Thanks again for your time and input.

Best regards,
Andreas

---

