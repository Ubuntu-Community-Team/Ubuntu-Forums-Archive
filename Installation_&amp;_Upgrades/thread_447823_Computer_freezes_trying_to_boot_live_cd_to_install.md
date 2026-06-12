---
title: "Computer freezes trying to boot live cd to install"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by p252 on 2007-05-18
Well, this is the first time I have ever not been able to easily install Ubuntu on a computer. .. .sad day. I am trying to install Feisty Fawn on a buddies laptop. It is an hp dv6000 series laptop with an AMD Turion 64 X2, nVidia Geoforce Go graphics card, 1 gig ram, 80 gig hard drive. When I try to boot up the live cd I am able to get the UBUNTU screen with the status bar but the screen after just goes all weird and blank. . . sigh. . . What should I do? Kinda ironic, I've been singing Ubuntu's praises to all my friends and how easy it is to use and then finally one of them lets me install (after seeing my laptop with Ubuntu running great on) for them but it won't work. If it won't even boot live is it a pretty good indicator that it the laptop won't work with Ubuntu (or even that it will work but not without a lot of trouble and constant problems)?

Thanks

---

### Post by p252 on 2007-05-18
Looking around the forums reveals lots of problems with nVidian graphics cards and booting in Feisty. . . Bummer. . .

---

### Post by hessiess on 2007-05-18
i got a hp pavilion dv2000 with a nivida card and it worked perfectily, exept the boodloder cept dying!

give the alternate cd a go

---

### Post by p252 on 2007-05-19
Ok, thanks for the replies. I was able to get Ubuntu installed with the alternate feisty cd. Now, however, the system won't boot. It freezes on the Ubuntu screen with the status bar. . .  Anything I can to do at this point?

---

### Post by l-fever on 2007-06-18
I'm having the same issue with a DV-6327 cl. The alternate cd seemed to work on the install but after the first reboot it hangs at ubuntu splash screen. :(

---

### Post by Pumalite on 2007-06-18
> **l-fever said:**
> I'm having the same issue with a DV-6327 cl. The alternate cd seemed to work on the install but after the first reboot it hangs at ubuntu splash screen. :(

It could be one of two things: graphical interface problem or GRUB cannot find 'boot'. For the first, try this:


 At the command prompt: type sudo dpkg-reconfigure -phigh xsever-xorg

Then just select vesa as your video driver and use the space bar to select the resolutions
Then reboot.

For the second, try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by l-fever on 2007-06-20
> **Pumalite said:**
> It could be one of two things: graphical interface problem or GRUB cannot find 'boot'. For the first, try this:


 At the command prompt: type sudo dpkg-reconfigure -phigh xsever-xorg

Then just select vesa as your video driver and use the space bar to select the resolutions
Then reboot.

For the second, try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I used: NOAPIC NOAPCI NORIRQPOLL NOSMP after pressing the f6 key on the grub command line and the live cd install went fine. Just got to get the wireless card working now. I really like this distro of linux btw! Thanks for the help!

---

