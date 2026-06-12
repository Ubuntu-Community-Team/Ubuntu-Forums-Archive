---
title: "Today's update broke the GUI"
date: 2021-01-12
forum: Installation &amp; Upgrades
---

### Post by syntaxerrorsix2 on 2021-01-12
I installed today's update for 20.04.1 and now the only function I have is the ability to move the mouse cursor.  The screen flickers a bit and the clock is locked up.  I can get to tty4 and get CL and have done a complete update again and again with no improvement.

I've tried a clean re-install from a USB stick as well.

The video card is an Intel Corp Xeon Es-1200 so no nvidia issues.

I've got a back-up but it does me no good as I can't run and I don't even know if that will fix anything.  

I'm at a complete loss, any help would be appreciated.



Ok, it was the new kernel.  Old kernel works fine.

---

### Post by CelticWarrior on 2021-01-14
It seems to be a problem with the recently introduced 5.8 series kernel in Ubuntu 20.04.
I had to solve a similar problem with a customer's miniPC also with Intel graphics.

The only way was to find an old 20.04 installer, not the 20.04.1, as that guarantees it stays on the 5.4 series.

---

### Post by ajgreeny on 2021-01-14
There's no need to reinstall as CW seems to be implying; you can do the same thing by following the suggestion below.

Reboot to the earlier 5.4.0-60 kernel, or whichever version you have, then run commands
```
sudo apt update && sudo apt purge linux-image-generic-5.8.0-36 linux-generic-hwe-20.04 && sudo apt install linux-generic
```
Copy that command to make sure you get it correct as it's easy to miss-type such a long command.
That will remove the current 5.8. problem kernel (hence your need to firstly boot to the older 5.4 kernel from grub) and will remove also the current linux-generic-hwe-20.04 package that will otherwise continue to call for and install the most recent 5.8 version.
Some of those 5.8 kernels may turn out to be good working ones, but if you do not specifically need them for very recent hardware support I suspect the 5.4 series will be fine; it is also fully supported right through to 2025 when Ubuntu 20.04 loses support.

---

### Post by Autodave on 2021-01-14
E: Unable to locate package linux-image-generic-5.8.0-36

Thanks ajgreeny.  I did that and got the error message above.  Ignore it?

---

### Post by CelticWarrior on 2021-01-14
Find out which one of the 5.8 kernel versions you have now, uninstall that instead.

---

### Post by ajgreeny on 2021-01-14
It looks as if there has been another 5.8.0-38 kernel released today, so try that and you may find that all is well again; this kernel version has arrived only a few days after the "broken" 5.8.0-36.

With luck this one will work as expected rather than give so many users difficulties of many kinds.

---

### Post by farlander762 on 2021-01-14
```
sudo apt update && sudo apt purge linux-image-5.8.0-34-generic linux-generic-hwe-20.04 && sudo apt purge linux-image-unsigned-5.8.0-36-generic linux-generic-hwe-20.04 && sudo apt purge linux-image-unsigned-5.8.0-38-generic linux-generic-hwe-20.04 && sudo apt install linux-generic

```

Try this.  I've checked the kernel package names and included all three 5.8 kernels I have seen so far.  If your machine doesn't have one or more of these it will ignore them.

BTW, this will list he installed kernels by name so you can get them exactly correct:
```
dpkg --list | grep linux-image
```

---

### Post by GhX6GZMB on 2021-01-14
I just did an update/upgrade which resulted in 5.4.0-62 as kernel. Rock stable and functional.
Perhaps you should remove the "load bleeding edge kernel" flag from your update manager?

---

### Post by Autodave on 2021-01-15
> **ml9104 said:**
> I just did an update/upgrade which resulted in 5.4.0-62 as kernel. Rock stable and functional.
Perhaps you should remove the "load bleeding edge kernel" flag from your update manager?

"Load bleeding edge kernel"....are you being funny or is that actually an option in Ubuntu?  There is no such option in Xubuntu.

---

### Post by davehk on 2021-01-15
It is happening even if that is NOT set. My bog standard 20.04 (i.e. installed as the original  20.04 and updated by SW updater, not the later .1 installation image) installation has had two versions of the 5.8 kernel installed by SW updater, as I discovered when Ubuntu's VirtualBox would not run. Because there had been two 5.8  (5.8.0-34 and -36) updates, I had no 5.4 kernel installed to fall back on. Fortunately Oracle's latest release of VB works fine with the new kernel.

I see that -38 has now been released - don't know if that fixes the issue.

---

### Post by Autodave on 2021-01-15
-38 did not fix mine.

---

### Post by GhX6GZMB on 2021-01-15
> **Autodave said:**
> "Load bleeding edge kernel"....are you being funny or is that actually an option in Ubuntu?  There is no such option in Xubuntu.

It was meant as a joke.

That being said, the Lubuntu (my OS, but I'm certain that other distris have something equivalent) Update Manager has these options:

"Important security updates" (tick)
"Recommended updates" (tick)
"Pre-released updates" (don't tick)
"Unsupported updates" (don't tick)

Now, if in your update manager you've selected one of the last two, you tend to run into trouble. And I have a feeling that some users having issues with 5.8.0 did just that.

---

### Post by Autodave on 2021-01-15
Xubuntu is similar but not quite the same.  Anyway, I already have the equivalent (I think) as you do.  I just need to block the 5.8 kernels and figure out how to get rid of the last 5.8 kernal so that this will boot a 5.4 kernel.

---

### Post by GhX6GZMB on 2021-01-15
A tip: install Timeshift or some equivalent system backup program. It's saved my behind so many times after mucking around myself or after a botched upgrade.
It's usually already in your local repository.

Cheers.

---

### Post by kansasnoob on 2021-01-16
I opened a bug report about this:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614)

I like to use synaptic package manager to remove such things as unwanted kernels. Step one, after installing 'synaptic' (sudo apt install synaptic) is to use the search box in synaptic for 'linux-generic'. Once that's installed and you've clicked on reload, and then apply updates you should have the latest 5.4 series kernel installed. If not you may have to remove 'linux-generic-hwe-20.04' as well but be sure you don't try to remove the running kernel! Read on to understand how. You then need to reboot and select the newest 5.4 series kernel from the grub menu which, if hidden, can be displayed by pressing either Esc or Shift right after the BIOS screen passes.

You can see what versions of the kernel you have installed by running "ls /boot" but you should also run "uname -r" to see what kernel you're booted with. You should not, and probably can not remove a running kernel! Then open synaptic again and search for 'linux-generic-hwe-20.04' and mark it for complete removal (does the same thing as "purge" in the terminal) and copy the version number of the kernel you want to rid yourself of into the search box and mark all of the bits that are installed (they'll have a green box to the left of them) and repeat that for all of the 5.8 kernels). I then like to use the Custom filters button in the lower left corner to display "marked changes" to be sure I've marked all of packages for "complete removal" so none of the old configuration files get left behind.

Then before rebooting check ls /boot and uname -r again to be sure you have a working kernel left to boot. I've had no problem using this procedure but I've been using synaptic for ages. Something I didn't mention is the reload button does the same thing as apt update. Might also be a good idea to check for broken packages in synaptic as well as missing recommends to be sure there are no kernel bits in there. Hope I'm not leaving anything out :redface:

BTW the more people that mark that bug as effecting them too the better the chance gets of a developer/maintainer actually looking at it. I did a test install and filed a bug report specific to the failure of nvidia drivers to install. Hopefully tomorrow I'll have time to test a Focal daily image and maybe figure out a way to shoehorn a bug report into the works so I can list it on the QA Tracker. If so I'll find a way to mention this kernel issue in that bug report. Anything it takes to get a dev to look at it!

---

### Post by farlander762 on 2021-01-17
> "Important security updates" (tick)
"Recommended updates" (tick)
"Pre-released updates" (don't tick)
"Unsupported updates" (don't tick)

Now, if in your update manager you've selected one of the last two, you tend to run into trouble. And I have a feeling that some users having issues with 5.8.0 did just that.

I (with acknowledged limitations) manage several Ubuntu machines, all run the desktop LTS and all are set up for updates as above to make my life easier.  Of the 6 machines that have attempted the 5.8.0 (-34, -36, or -38) kernel, two have been knocked out.  The one I'm on now has NVIDIA graphics and updated without issue.  I think I only have two more machines to go and I'm intentionally delaying one of those until next weekend due to a church event that ended earlier.


Failed Machine 1                                           
NVIDIA                                                         
2x Xeon                                                        
BIOS                                                           
96 GB DDR3 RDIMM                                      
SuperMicro                                                    
RAID 1 and 5 (separate systems)                    
Wouldn't start at all                                        

Failed Machine 2
Integrated, probably Intel
1x Pentium
UEFI
4 GB probably DDR3
Dell 
Single HDD
Loaded normally then locked up when trying to do anything

I can't put a finger on any real hardware commonalities aside from that they both are running Ubuntu Desktop 64 bit 20.04.

---

