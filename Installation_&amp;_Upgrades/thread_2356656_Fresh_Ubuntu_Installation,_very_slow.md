---
title: "Fresh Ubuntu Installation, very slow"
date: 2017-03-25
forum: Installation &amp; Upgrades
---

### Post by megamichiel on 2017-03-25
Hello,

I booted up my laptop this morning only to find out that due to lack of storage windows wasn´t able to boot, and I couldn´t even remove all files. I decided to finally give Ubuntu a try and the installation process was flawless. As soon as I got into the desktop, however, it didn take too long and Ubuntu went very, very slow. Restarting did not fix it and the threads I looked at which had similar problems did not do anything, so I decided to post this on here (using the same laptop, when typing it takes 1/2 to 1 second for the text to refresh). Part of my computer´s specifications, I believe these are most relevant:
Intel Core i7-3612QM (I believe @ 2.1 GHz), 8GB of RAM, 240GB SSD.
It doesn´t seem like I´m not giving the OS enough.

Storage space was perfectly fine with only a few GBs used and tons left, and this is a screenshot of my CPU usage:
[IMG]https://i.imgur.com/O2Cpz8F.png[/IMG]

I checked out GSmartControl, and the only think in pink was ¨Temperatures¨, but there we some things that said ¨pre-failure¨.

Has anybody experienced this or does anybody know what could potentially fix this?

Thanks,
Michiel

---

### Post by TheFu on 2017-03-25
Try disabling the "speed step" feature in the BIOS.

If you want more details from the Arch guys: [https://wiki.archlinux.org/index.php/CPU_frequency_scaling](https://wiki.archlinux.org/index.php/CPU_frequency_scaling)

---

### Post by ajgreeny on 2017-03-25
Your computer spec with Intel Core i7-3612QM (I believe @ 2.1 GHz), 8GB of RAM, 240GB SSD should be more than good enough to run Ubuntu quickly and certainly without those very high cpu figures shown by htop, but what you have not told us is the graphics card in the machine, if there is one.

If you do not have a separate graphic card and use the integrated Intel graphics only I think something must have gone wrong in the installation as that machine with the IGP would work fine.
Let's see the output 9in terminal of ```
lspci -k
``` which will show the pci devices including graphics and wifi etc etc; that might give us a clue.

---

### Post by megamichiel on 2017-03-25
> **ajgreeny said:**
> Your computer spec with Intel Core i7-3612QM (I believe @ 2.1 GHz), 8GB of RAM, 240GB SSD should be more than good enough to run Ubuntu quickly and certainly without those very high cpu figures shown by htop, but what you have not told us is the graphics card in the machine, if there is one.

If you do not have a separate graphic card and use the integrated Intel graphics only I think something must have gone wrong in the installation as that machine with the IGP would work fine.
Let's see the output 9in terminal of ```
lspci -k
``` which will show the pci devices including graphics and wifi etc etc; that might give us a clue.
It has an NVIDIA GeForce GT 630M. If you need the lspci output:
```
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)    Subsystem: Lenovo GF108M [GeForce GT 630M]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
```

[COLOR="#FF0000"]EDIT:[/COLOR] I´ve been a while for a few hours and now I came back. It took me a while to realize that the cpu is not being overloaded as quickly (not noticing anything) this time. I´m temporarily closing this thread unless it starts to happen again.

---

### Post by ajgreeny on 2017-03-25
You may find that the nvidia driver works even better than the current nouveau driver you are using, so probably worth trying Additional Drivers to see what's available.

I've never had an nvidia card so have no personal experience of this, but if you try it and it does not work you can always revert to nouveau again.

---

### Post by megamichiel on 2017-03-25
[SIZE=4]== Reopening, I guess after a break it was faster for a while but now it´s back ==[/SIZE]

@ajgreeny I tried it without luck :(. Do you need any other info?
@TheFu My BIOS does not support that, but thanks for the suggestion.

So far I´m quite liking Ubuntu, both the OS and the community :). Let´s hope this problem will be resolved soon.

---

### Post by TheFu on 2017-03-25
ajgreeny is looking for more than just the GPU info.  The more info you provide, the more likely we are to google a solution. Sometimes there are specific issues with specific chips/cards.  

Using the best, newest, **approved**, drivers is always a good idea if the default drivers installed aren't working.  If they do work, don't touch them.  For Linux systems, it usually isn't needed to get a driver like we do with Windows. Going directly to the vendor is not usually the best answer.  Use the package manager to load any proprietary drivers for your system and OS. These have been tested and are the most stable.  Those from the vendors often have terrible issues. Of course, if the default drivers and those proprietary drivers installed through the package manager don't solve an issue, then there isn't much choice except trying the vendor's latest. This can be ugly and might require building and linking the driver manually.

Just because your BIOS doesn't support something, doesn't mean you can't control it some other way. The link provided is a little hard-core, but has some useful information.  I google's your specific CPU for issues. That link was a common answer. Just sayin'.

---

### Post by mikewhatever on 2017-03-25
Have you tried installing the recommended nvidia driver? Have you tried another web browser? The high cpu usage is mainly due to Chrome going mad.

---

### Post by megamichiel on 2017-03-25
> **TheFu said:**
> ajgreeny is looking for more than just the GPU info. The more info you provide, the more likely we are to google a solution. Sometimes there are specific issues with specific chips/cards. 

Using the best, newest, **approved**, drivers is always a good idea if the default drivers installed aren't working. If they do work, don't touch them. For Linux systems, it usually isn't needed to get a driver like we do with Windows. Going directly to the vendor is not usually the best answer. Use the package manager to load any proprietary drivers for your system and OS. These have been tested and are the most stable. Those from the vendors often have terrible issues. Of course, if the default drivers and those proprietary drivers installed through the package manager don't solve an issue, then there isn't much choice except trying the vendor's latest. This can be ugly and might require building and linking the driver manually.

Just because your BIOS doesn't support something, doesn't mean you can't control it some other way. The link provided is a little hard-core, but has some useful information. I google's your specific CPU for issues. That link was a common answer. Just sayin'.
Put the info in a pastebin: [http://pastebin.com/rUXVu17u](http://pastebin.com/rUXVu17u)
I manually downloaded a driver for the graphics card earlier but it did not change anything. I´ll remember what you said.
I had looked into the page a little bit already, but I´ll do some more research. Thanks for your assistance.

> **mikewhatever said:**
> Have you tried installing the recommended nvidia driver? Have you tried another web browser? The high cpu usage is mainly due to Chrome going mad.
I actually downloaded chrome to see if firefox had anything to do with it, but it didn´t. I also had quite a few things synchronized with it so it helped me get going a little quicker. This was the reason I had it opened, but I could try without it for a bit.

---

### Post by TheFu on 2017-03-25
If you boot off a live-distro (not installed), say on a flash drive, does the performance still suck?  If so, I'd look at HW and network issues.  If not, then it is probably personal or system settings.  

To check if it is personal settings, create a new userid and login as that. If it is fast, then the issue is when personal settings for the other account. If not, it is with system settings, most likely.

Would be worth trying lubuntu, xubuntu and/or ubuntu-mate in this testing.

We just need to narrow down the cause.

---

### Post by megamichiel on 2017-03-26
> **TheFu said:**
> If you boot off a live-distro (not installed), say on a flash drive, does the performance still suck?  If so, I'd look at HW and network issues.  If not, then it is probably personal or system settings.  

To check if it is personal settings, create a new userid and login as that. If it is fast, then the issue is when personal settings for the other account. If not, it is with system settings, most likely.

Would be worth trying lubuntu, xubuntu and/or ubuntu-mate in this testing.

We just need to narrow down the cause.
I actually installed the OS using a flash drive, so I could already test it. It unfortunately does not affect anything. I think right now I´m going to opt for W10 again because I don´t think the laptop can handle Ubuntu properly (I forgot to mention, it´s a Lenovo Z580 which is from quite a few years ago). I´m getting a new computer possibly some time soon, and I think I´ll give it a new try on that.

Thanks a lot for your help.

---

### Post by TheFu on 2017-03-26
Any Core i7 should fly with any Ubuntu version.
If the GPU isn't the greatest, using a different GUI will make a huge difference.  On Linux, the GUI is just another program and Unity is the heaviest GUI out there that requires a mid-level GPU to be happy.  Most other version don't have this issue (none, actually).  Unity is the default GUI for Ubuntu.

Lubuntu runs well on almost any hardware - I've seen it fly on a Pentium4 from 2006.  Xubuntu and Ubuntu-Mate have almost the same level of low-graphics requirements, but feel nicer.  For the time you've already spent on this, I'd feel bad if you walk away with out a viable solution.  Please try Ubuntu-Mate. I think you'll be surprised at how great it is, especially compared to Windows.

No need to reload the entire OS - just install the **mate-desktop** package, then logout, select the "gear" at the login screen, pick a different desktop type, "Mate" in this case, then login normally.

---

### Post by RobGoss on 2017-03-26
With the specs you have you should not have slowness issues is this a new installation?

1- Have you been experiencing this slowness since you install Ubuntu?

2- Did you install any new application recently that maybe causing this slowness?

3- How did the Live desktop run before you installed Ubuntu?

---

### Post by megamichiel on 2017-03-26
> **TheFu said:**
> Any Core i7 should fly with any Ubuntu version.
If the GPU isn't the greatest, using a different GUI will make a huge difference.  On Linux, the GUI is just another program and Unity is the heaviest GUI out there that requires a mid-level GPU to be happy.  Most other version don't have this issue (none, actually).  Unity is the default GUI for Ubuntu.

Lubuntu runs well on almost any hardware - I've seen it fly on a Pentium4 from 2006.  Xubuntu and Ubuntu-Mate have almost the same level of low-graphics requirements, but feel nicer.  For the time you've already spent on this, I'd feel bad if you walk away with out a viable solution.  Please try Ubuntu-Mate. I think you'll be surprised at how great it is, especially compared to Windows.

No need to reload the entire OS - just install the **mate-desktop** package, then logout, select the "gear" at the login screen, pick a different desktop type, "Mate" in this case, then login normally.
I might test it out some time later, but at the time I had stuff to do so I went back to windows 10. I also realized there were a few things I needed to settle on it as well. Next time I'll have a go at mate. 

> **TheFu said:**
> Any Core i7 should fly with any Ubuntu version.
If the GPU isn't the greatest, using a different GUI will make a huge difference.  On Linux, the GUI is just another program and Unity is the heaviest GUI out there that requires a mid-level GPU to be happy.  Most other version don't have this issue (none, actually).  Unity is the default GUI for Ubuntu.

Lubuntu runs well on almost any hardware - I've seen it fly on a Pentium4 from 2006.  Xubuntu and Ubuntu-Mate have almost the same level of low-graphics requirements, but feel nicer.  For the time you've already spent on this, I'd feel bad if you walk away with out a viable solution.  Please try Ubuntu-Mate. I think you'll be surprised at how great it is, especially compared to Windows.

No need to reload the entire OS - just install the **mate-desktop** package, then logout, select the "gear" at the login screen, pick a different desktop type, "Mate" in this case, then login normally.

> **RobGoss said:**
> With the specs you have you should not have slowness issues is this a new installation?

1- Have you been experiencing this slowness since you install Ubuntu?

2- Did you install any new application recently that maybe causing this slowness?

3- How did the Live desktop run before you installed Ubuntu?
1. Yes, without having installed any programs and just browsing after the installation it was already abnormally slow. This also makes #2 obsolete. 
3. I did not test the live desktop for I needed to get back to work as soon as I could. Later I did have a go at it, but it wasn't any different.

---

### Post by TheFu on 2017-03-26
For the next time around: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
is probably what you want to follow, in this order:

a) install OS
b) apt update && apt upgrade
c) install nvidia binary video drivers

For me, the install is about 15 min.  Update/upgrade is 5 min more.  I don't have any nvidia or AMD/ATI GPUs, but bet that is 1 min or less.  I've been happy with the onboard IGP from intel.  The driver is pre-installed as i915 on my Core i3.
```
$ lsmod |grep i915
i915                 1265664  3
video                  40960  1 i915
i2c_algo_bit           16384  1 i915
drm_kms_helper        147456  1 i915
drm                   364544  4 i915,drm_kms_helper

```
I am not a gamer.

Linux does have a steep learning curve.  It is NOT Windows. There are a few great articles about the differences, taken from a Windows background.  It really is whatever you get used to.  Kids who grow up in Linux homes have similar issues with Windows, though they are more flexible since they've seen at least 5 very different GUIs which are commonly used on Linux.

Nothing against Windows. I have a few of those installs myself, but they are used for very specialized needs, not for daily use here, as you might expect. ;)

Anyway, when you are ready to try again, we'll be here.

---

