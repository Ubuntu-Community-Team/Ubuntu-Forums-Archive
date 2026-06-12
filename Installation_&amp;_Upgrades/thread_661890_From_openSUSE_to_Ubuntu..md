---
title: "From openSUSE to Ubuntu."
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by rohedin on 2008-01-08
Hi there :)

A few weeks ago I made the decision to install Linux permanently. At that point I'd tried three different distributions. (K)Ubuntu, Fedora and openSUSE. 

Long story short I decided that I liked openSUSE the best so I went ahead and installed it, with Windows on my first HD and openSUSE on my second HD. The installation worked fine. It

 was fine for the first few days then suddenly the boot-up splash screen suddenly disappeared and I was left with text-only bootup. I didn't really mind, it was actually quite interesting.

A couple of days later an update for Amarok came through, but SUSE updater just crashed every time I tried to install it. That was when the updater even started, half the time YaST2 just complained about another transaction already in progress, not going into too much detail, YaST2 spiraled out of control and the entire system kept developing glitches and errors to the point I just said "Heck, I'll just install Ubuntu"


But my question here is, when I install Ubuntu (maybe Kubuntu) will the GRUB bootloader that came with SUSE cause any issues? Or will Ubuntu just delete it and make a new bootloader?

Thanks.

---

### Post by dabang on 2008-01-08
If you install (K)Ubuntu via the "desktop" CD, grub will be installed to the MBR of your first disk, over writing any bootloader that was previously installed at that location. If you have Windows installed on another partition it should be added automatically to grub. So, should be no problem. (SUSE did likely do the same, over writing the windows bootloader with grub and adding Windows to the grub menu?)

---

### Post by pbcartwright on 2008-01-08
you probably have either an NVIDIA or ATI video card.. that's why you got the text-only login.. you will have the same issue no matter what distro you install. as for grub, it doesn't matter what distro yo install, you can have 2 or 3 different distros installed and grub will let you choose which one to boot up.
with kubuntu you have to tell it to install the non-free NVIDIA driver.. once you do that, you will be OK. you might also want to install envy, which installs the video driver foryou..  :
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by rohedin on 2008-01-08
> **dabang said:**
> If you install (K)Ubuntu via the "desktop" CD, grub will be installed to the MBR of your first disk, over writing any bootloader that was previously installed at that location. If you have Windows installed on another partition it should be added automatically to grub. So, should be no problem. (SUSE did likely do the same, over writing the windows bootloader with grub and adding Windows to the grub menu?)

Yup, that's what SUSE did. Thanks for confirming that with me.

Also, pbcartwright, wrong thread :razz:

---

### Post by dasunst3r on 2008-01-08
I went from Ubuntu to openSUSE two days ago and switched back over its networking and hotplug capabilities.  In particular, the ipw3945 module wouldn't survive across suspend/resumes and I would get "permission denied" errors when I plug in USB disks (hard drives or flash drives).  In this, I also learned that GNOME is so much more stable.

While I was at it, I gave KDE4 a fair shot and didn't like it.  There's only three days until release and so many things are still missing/buggy (no NetworkManager frontend?  Seriously?).

---

### Post by dabang on 2008-01-08
> you probably have either an NVIDIA or ATI video card.. that's why you got the text-only login.. you will have the same issue no matter what distro you install.
Sorry, I disagree, at least for Nvidia video cards. The default "nv" driver should work. If you like to install the proprietary Nvidia/ATI drivers use the "restricted manager" that comes with gutsy. It's easy and does the trick well!

---

### Post by Chrisoldinho on 2008-01-08
When I installed Ubuntu last night, I put on the restricted drivers for the NVIDIA card. But I then noticed that it doesn't include any of the NVIDIA control panel which I like to mess around with.

I downloaded Envy and used that, it automatically downloaded the latest drivers and installed them. It works flawlessly and it just as easy to install and use as any Windows application would be.

I'm absolutely hooked to Ubuntu now, and Windows Vista is fast becoming something I wish I didn't have. The only problem is, my family uses the laptop as well and they don't know the 1st thing about Linux.

I think I have stumbled across the main problem with Linux Distro's like Ubuntu. It's not the quality of the product because I'd argue some of the features are much superior to Microsoft. It's getting the message to the masses that will continue to be the problem, but with the cash cow that is MS it will always play 2nd fiddle..

---

