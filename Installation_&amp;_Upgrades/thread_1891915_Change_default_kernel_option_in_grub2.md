---
title: "Change default kernel option in grub2"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by altoiddealer on 2011-12-06
After d/l the latest kernel, I sometimes get a permanent black screen at boot.  I don't feel like trying to sort out the issue, but I have determined that this issue does not happen if I select "Use older kernel" each time I boot.

I do not want to have to navigate to "Use previous kernel" every time I boot Ubuntu, though.

I looked around the forums, and the common solution to "rolling back" to a previous kernel is to change your default boot option to older kernel.

My issue with this, however, is that Ubuntu is NOT my default boot option, and I do not want to set it as default OS. 


Thanks in advance!

---

### Post by drs305 on 2011-12-06
Grub Customizer (see signature link) might do what you want. 

Another option is to uninstall the problem kernel. Once it's removed, 'lock' the current kernel in Synaptic (via Package, Lock Version) and then update grub. That should move the older kernel back onto the main Grub menu page if it is the newest kernel on the system.

A second option is to create a custom menuentry by copying the desired menuentry to /etc/grub.d/40_custom. Then it will always appear at the bottom of the main menu.

---

### Post by altoiddealer on 2011-12-08
> **drs305 said:**
> Another option is to uninstall the problem kernel. Once it's removed, 'lock' the current kernel in Synaptic (via Package, Lock Version) and then update grub. That should move the older kernel back onto the main Grub menu page if it is the newest kernel on the system.

Well, my current kernel is the problem kernel!  From what I have been reading it seems like it is only recommended to remove older kernels and not the current one.  Is this true?  If not could you please tell me how to remove the current one and roll back to the previous one.

Otherwise, I suppose I'll check out that Grub customizer you mentioned.  Actually I think I'll check that out anyway :popcorn:

Thanks!

---

### Post by drs305 on 2011-12-08
> **altoiddealer said:**
> Well, my current kernel is the problem kernel!  From what I have been reading it seems like it is only recommended to remove older kernels and not the current one.  Is this true?  If not could you please tell me how to remove the current one and roll back to the previous one.

You are correct that you can't remove the current kernel. Don't you have the option of booting an older kernel - either on the main menu or perhaps 'hidden' under the 'Previous ...' submenu?

If there is no entry you can check for the presence of older kernels from the Grub menu and then edit the menuentry to boot an older kernel. 

Press 'c' to get to the grub prompt.

Type "ls (hdX,Y)/boot" to see the available kernels. (Substitute the correct drive and partition).

If you find one, press ESC then 'e' to edit the first menuentry. Use the cursors to navigate and edit the kernel and initrd.img numbers, then CTRL-x to boot.

Once you can boot into a good kernel, I'd recommend Ubuntu Tweak to remove the 'bad' kernel:
[HOWTO: Remove Older Kernels via GUI ]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by altoiddealer on 2011-12-08
Ahhhhhhh OK, I was confused :)  I was referring to the most updated kernel as the "current kernel". :lolflag:

So if I boot into the older one (the one I want) I can then remove the most up to date one. Got it.

Thank you! I will perform this task today and report back.

---

### Post by drs305 on 2011-12-08
> **altoiddealer said:**
> Ahhhhhhh OK, I was confused :)  I was referring to the most updated kernel as the "current kernel". :lolflag:

So if I boot into the older one (the one I want) I can then remove the most up to date one. Got it.

Thank you! I will perform this task today and report back.

One more thing...

Ubuntu may try to reinstall the newest kernel. You may want to try it again, but if not you will need to 'lock' your current kernel to prevent the updates.

See posts #2 and #4 of this thread:
[http://ubuntuforums.org/showthread.php?t=1887588]("http://ubuntuforums.org/showthread.php?t=1887588")
Apologies in advance since those posts will have you go to other posts.

---

### Post by altoiddealer on 2011-12-10
I tried using Ubuntu Tweak, but it is not listing any kernels at all!

In Synaptic, if I try to remove the latest (but not current) kernel, it marks "linux-generic" and "linux-image-generic" for removal.  This happens regardless of whether I "Lock" the version I want to keep or not.  That doesn't seem right so I'm leaving that alone for now

However, Grub Customizer was able to do what I want, which is bring the older (bug free) kernel to the main menu instead of a sub-menu. Very nifty program! :guitar:

Thanks!  If you can tell me how to remove the problem kernel that would be a nice bonus though :)

---

### Post by drs305 on 2011-12-11
> **altoiddealer said:**
>  That doesn't seem right so I'm leaving that alone for now

However, Grub Customizer was able to do what I want, which is bring the older (bug free) kernel to the main menu instead of a sub-menu. Very nifty program! :guitar:

Thanks!  If you can tell me how to remove the problem kernel that would be a nice bonus though :)

I'd leave things as they are (more later...). The advantage of keeping 'linux-image' is that if another kernel comes along it will be installed and you can see if it works.

Background. I wouldn't recommend doing this but I have lots of backups and tend to 'sacrifice' my system from time to time. I opened Synaptic and it did indeed allow me to uninstall 'linux-image' and 'linux-image-generic'. After to completed the task, it showed those two packages removed, but the actual latest kernel still installed. So may be possible to boot an older kernel, remove 'linux-image' and not be bothered with new updates. *But I don't know this and wouldn't want you to try it.*

I currently away from home but perhaps one day when I feel like breaking something I'll boot an older kernel and see what happens if I remove linux-image and reboot.

---

### Post by drs305 on 2011-12-11
"One day" came faster than I thought it would. After making my last post, I found an updated kernel awaiting installation. I removed "linux-image", "linux-image-generic" and "linux-headers-generic" and rebooted. The updated kernel no longer showed available for installation, the kernel I had been using (at that point the same as 'linux-image') still booted.

While I wouldn't perform this on a production machine which I couldn't afford to break (i.e. a looming deadline, no backup, etc), it does appear that removing 'linux-image' will not hurt the machine, even if using the latest kernel.

---

### Post by altoiddealer on 2011-12-12
Above and beyond, sir!  Thank you very much!

And of course just when I thought my problems were over, it turns out that I am still experiencing the same issue even with the previous kernel... although it seems like the problem occurs less frequently.

I am going to make a new thread and see if someone can help me figure out why it sometimes freezes with black screen at boot

Thanks again!

---

