---
title: "Changing orders of boot options in grub"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by jeff.biggeek02 on 2010-12-29
I just want to confirm something before I mess with the bootloader.  It kind of scares me to rewrite my MBR. :)

It appears that the grub version that comes with Ubuntu 10.10 drives its menu generation from /etc/grub.d/* when you execute update-grub.  If I want to put windows first in the list, could I just rename "30_os-prober" to something like "09_os-prober" and run update-grub?  My reason for this is every time Ubuntu updates the kernel, it adds 2 new entries to grub's boot menu.  It's easy enough to remove these via the Synaptic Package Manager, but that means for at least 1 boot cycle, my default OS gets messed up (Windows).  I have to leave it as the default for others that use the computer, even though I prefer Ubuntu.

Is this a good long-term solution to that problem?  Thanks.

---

### Post by presence1960 on 2010-12-29
Install startupmanager, a GUI based option which will let you choose the default OS so every time GRUB loads that OS is highlighted- all you need to do is push enter.

You can install it through Synaptic Package manager or terminal by running ```
sudo apt-get install startupmanager
```

The other option is as you said, to rename.

---

### Post by Quackers on 2010-12-29
How did you get Windows to be the default boot option in grub? With Startup Manager?
Instead try looking at this thread under the heading
[COLOR="DarkRed"]/etc/default/grub[/COLOR]
at the GRUB_DEFAULT=0 part.

Ah, the link would be good :-)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jeff.biggeek02 on 2010-12-30
I haven't tried Startup Manager yet.  I have been adjusting GRUB_DEFAULT = 5, since Windows 7 is typically 5th in my list.  The problem with that are those boots where a new kernel has just been installed, and Windows 7 becomes the 7th option in the list.  The simplest way to get windows to always be number 'x' in the list seems to be putting it first, and setting GRUB_DEFAULT = 0.  Then, if Ubuntu adds new entries due to kernel updates, it doesn't affect what I boot by default.
 
Can Startup Manager handle that, or is it just a GUI for adjusting GRUB_DEFAULT?

---

### Post by presence1960 on 2010-12-30
> **jeff.biggeek02 said:**
> I haven't tried Startup Manager yet.  I have been adjusting GRUB_DEFAULT = 5, since Windows 7 is typically 5th in my list.  The problem with that are those boots where a new kernel has just been installed, and Windows 7 becomes the 7th option in the list.  The simplest way to get windows to always be number 'x' in the list seems to be putting it first, and setting GRUB_DEFAULT = 0.  Then, if Ubuntu adds new entries due to kernel updates, it doesn't affect what I boot by default.
 
Can Startup Manager handle that, or is it just a GUI for adjusting GRUB_DEFAULT?

Start up manager will not be affected by kernel updates. It is GUI and relies on the choice of OS you make. It does not alter the order of kernels and OSs, but rather has the OS you select highlighted at the GRUB menu. All you need to do is hit the Enter key to select the default OS.

---

### Post by mcduck on 2010-12-30
> **jeff.biggeek02 said:**
> I just want to confirm something before I mess with the bootloader.  It kind of scares me to rewrite my MBR. :)

It appears that the grub version that comes with Ubuntu 10.10 drives its menu generation from /etc/grub.d/* when you execute update-grub.  If I want to put windows first in the list, could I just rename "30_os-prober" to something like "09_os-prober" and run update-grub?  My reason for this is every time Ubuntu updates the kernel, it adds 2 new entries to grub's boot menu.  It's easy enough to remove these via the Synaptic Package Manager, but that means for at least 1 boot cycle, my default OS gets messed up (Windows).  I have to leave it as the default for others that use the computer, even though I prefer Ubuntu.

Is this a good long-term solution to that problem?  Thanks.

Yes, renaming the 30_os_prober to 09_os_prober would do exactly what you want, always placing the Windows entries above Ubuntu ones. (remember to run "sudo update-grub" afterwards..)

The old version of Grub was able to automatically adjust the default OS number as new entries were added to the menu (if you just enabled this feature in the menu.lst), but if Grub2 can do the same I haven't found any documentation about it.

---

### Post by jeff.biggeek02 on 2010-12-30
Ok, thanks everyone.

---

