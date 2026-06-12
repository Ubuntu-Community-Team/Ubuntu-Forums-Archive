---
title: "Ubuntu Desktop won't display after latest kernel upgrade"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by rsun on 2008-02-16
This has always been my fear. 
Every time a kernel related upgrade I often worried whether the desktop would survive especially to do with video card related upgrade, as this had happened to me before to my old HP 6630.
This is what happened this time.
I proceeded to upgrade to the latest kernel 2.6.21-386 on my Dell PIII machine. I noticed in one of the upgrade files it has something to do with some fixes or improvement to i9xx Intel ???. I proceeded anyway.
After the reboot, the desktop was set to use 640x480 resolution which is not the original default. I then went to change it to 800x600 and it somehow went to 1280x768 which makes the screen panning. I went to change it again this time I select the Use Default option hoping it would take my default. The screen went blank after I hit OK.
I turned off the computer and hit Esc to start it with the 2.6.20-16 generic and 2.6.17-12 generic both displayed blank (not even a cursor) after the Ubuntu splash screen.
Can someone please help me to recover this. There's a conflict of the kernel with my nVidia TNT2 video card.
My Dell PIII:
Dell Optiplex GX110
677MHz
384MB RAM
nVidia TNT2 video card.
OnBoard card is not used.

rsun

---

### Post by PmDematagoda on 2008-02-16
Are you able to boot the 2.6.21 kernel? If so, that should fix your problem.

But if you cannot boot the new kernel then you may have to recompile the Nvidia kernel to work with the old kernels.

---

### Post by rsun on 2008-02-16
> **PmDematagoda said:**
> Are you able to boot the 2.6.21 kernel? If so, that should fix your problem.

But if you cannot boot the new kernel then you may have to recompile the Nvidia kernel to work with the old kernels.

I don't have the 2.6.21 in the list. There's only 2.6.22-14, 2.6.20-16, 2.6.17-12 and older available.
Is there a way to uninstall the latest kernel and go back to my previous version before the upgrade?

rsun

---

### Post by PmDematagoda on 2008-02-16
Could you post as to how you installed the Nvidia driver in the first place.

---

### Post by RgnKjnVA on 2008-02-16
This thread helped me recover from the same thing two days ago. Hope it helps. 

[http://ubuntuforums.org/showthread.php?t=357767](http://ubuntuforums.org/showthread.php?t=357767)

You can choose an older kernel if you interrupt GRUB at start up and get it's selection menu. If you're having trouble interrupting and are using a KVM switch to allow 2 machines to share one monitor, you may have to connect the keyboard directly to the Linux machine.

---

### Post by kostkon on 2008-02-16
> **rsun said:**
> This has always been my fear. 
Every time a kernel related upgrade I often worried whether the desktop would survive especially to do with video card related upgrade, as this had happened to me before to my old HP 6630.
This is what happened this time.
I proceeded to upgrade to the latest kernel 2.6.21-386 on my Dell PIII machine. I noticed in one of the upgrade files it has something to do with some fixes or improvement to i9xx Intel ???. I proceeded anyway.
After the reboot, the desktop was set to use 640x480 resolution which is not the original default. I then went to change it to 800x600 and it somehow went to 1280x768 which makes the screen panning. I went to change it again this time I select the Use Default option hoping it would take my default. The screen went blank after I hit OK.
I turned off the computer and hit Esc to start it with the 2.6.20-16 generic and 2.6.17-12 generic both displayed blank (not even a cursor) after the Ubuntu splash screen.
Can someone please help me to recover this. There's a conflict of the kernel with my nVidia TNT2 video card.
My Dell PIII:
Dell Optiplex GX110
677MHz
384MB RAM
nVidia TNT2 video card.
OnBoard card is not used.

rsun

How did you install your Nvidia driver? This problem usually happens when you install the driver using *Envy* or manually from *Nvidia* instead of using the one provided in the repositories.

---

### Post by rsun on 2008-02-16
> **PmDematagoda said:**
> Could you post as to how you installed the Nvidia driver in the first place.

It was a while ago when I got the nVidia to work with my Dell machine. I think I got it to work by following The Ubuntu guide or from some links from the Ubuntu website. There were many trials and errors I finally got it to work.

The only options I have right now is to run in recovery mode. None of my previous version in GRUB would run the graphic Desktop.

rsun

---

### Post by rsun on 2008-02-16
> **RgnKjnVA said:**
> This thread helped me recover from the same thing two days ago. Hope it helps. 

[http://ubuntuforums.org/showthread.php?t=357767](http://ubuntuforums.org/showthread.php?t=357767)

You can choose an older kernel if you interrupt GRUB at start up and get it's selection menu. If you're having trouble interrupting and are using a KVM switch to allow 2 machines to share one monitor, you may have to connect the keyboard directly to the Linux machine.

I choose the older kernal from GRUB. No luck

rsun

---

### Post by rsun on 2008-02-16
> **kostkon said:**
> How did you install your Nvidia driver? This problem usually happens when you install the driver using *Envy* or manually from *Nvidia* instead of using the one provided in the repositories.

I tried many ways for a long time to get the nVidia to work. Finally it was the driver from Ubuntu repository that got it to work. I found the solution from one of the guides.

rsun

---

### Post by PmDematagoda on 2008-02-16
Can you tell me what Nvidia driver version the Nvidia TNT2 card uses?

---

### Post by kostkon on 2008-02-16
Try to boot into safe mode and reconfigure your X server (better boot with the latest kernel):
```
sudo dpkg-reconfigure xserver-xorg
```

I hope you haven't damaged your system by turning it off after the screen went blank.

Nevertheless, do the reconfiguration and see what happens.

---

### Post by rsun on 2008-02-16
I got it back YES.
I went into the safemode, and copied a backup of xorg.conf over the latest one. It's now up and running in my original set up.

btw, my other new computer (Compaq 5230) I bought before Christmas also runs Ubuntu 7.10. I upgraded that without any problems. I got rid of the pre-installed Vista faster than it can say Estala-Vista. I installed Wine on it and run WOW under Wine.
I also run a 7.10 server, but that one does not have X installed.
My experience was, every time, a new upgrade for the kernel (with video card fixes) is available for my older computers, there's always some incompatibility issues. This is something people should be aware of.

Anyway, thanks for all the help.

rsun

---

