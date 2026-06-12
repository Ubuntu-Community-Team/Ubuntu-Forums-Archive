---
title: "grub shows 10 ubuntu os and one windows os"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by Blue-Fox on 2011-09-06
My computer works great in both windows and ubuntu 10.04.3 LTS, however i was wondering why when loading grub shows 10 ubuntu os (plus the restore version)  and one windows os. 

There should only be one operating system for ubuntu and one for windows.

Just wondering why?

---

### Post by dino99 on 2011-09-06
its a good idea to have at least 2 different good kernels (or the latest + 1 good) in case one fail. You have to uninstall the ones you dont want/need (3 packages for each version: 2 headers + 1 image), using synaptic and update grub ( should be done automatically)

---

### Post by drs305 on 2011-09-06
I highly recommend using Ubuntu Tweak to remove the extra kernels you don't need. Removing them from the system will also remove them from your Grub 2 menu. As *dino99* suggested, keep at least one older kernel you know works.

You can use the "Rm-Kernel" link in my signature line to learn more about removing extra kernels and there is also a link there for Ubuntu Tweak.

Note for the future: In later versions of Grub 2 from the one you are using, extra kernels are hidden in submenus so they don't clutter up the main menu. It's a nice feature.

---

### Post by Blue-Fox on 2011-09-06
Hi Dino99, Thanks for the reply.  I am still learning a lot about ubuntu and enjoying it. 
I do have another question about another computer. Its a Dell laptop. I tried installing ubuntu 10.04 lts on it with a windows dual boot. However when I boot to ubuntu without the live cd all i get is a white screen. With the live cd in the dirve it works. Got any ideas why?

---

### Post by Blue-Fox on 2011-09-06
drs305, Thank you for the information. I will tweak it.

---

### Post by SaintDanBert on 2011-09-06
> **drs305 said:**
> ...
Note for the future: In later versions of Grub 2 from the one you are using, extra kernels are hidden in submenus so they don't clutter up the main menu. It's a nice feature.

Grub2, update-manager or similar software features that (a)mark a configuration with SUCCESSFUL_BOOT vs. FAILED_BOOT, (b)mark failed configurations so they are obvious in any boot-time menu, (c)arrange details so that fallback can be mostly automatic, (d)captures current configuration files into a "snapshot" archive, and (e) cleans away stale editions of any software would be what I consider to be "nice" features.

While it may be "nice" to avoid clutter in any menu, and I applaud use of a sub-menu for extra kernel editions, from where I sit, that is two boot options:
[list=1]
[*]boot the latest kernel
[*]boot the fallback kernel
[/list]
The "fallback" option might do anything reasonable that makes sense
to end-users (vs. kernel savvy folks).

I believe that the typical power-user or end-user will only care about:
[list]
[*]the kernel and parts from the most recent update
[*]the kernel and parts they were using previously -- it worked
[*]features to support "fail soft" and "fallback" when the most recent
kernel update has problems
[/list]
Options for update-grub that say, "keep N previous kernel editions" used to work, but I have not seen them work lately.
"Failsoft" and "fallback" options that are not arcane incantations are rare beasts through most of linux.

In aeons past on software not *nix, what we know as the "system root file system" was a folder-tree with a symbolic name SYS$SYSROOT. Each "update" cloned the current tree and made a fresh copy. Changes were applied to the copy. If there were problems during system start, a mostly automatic fallback would select the previous folder tree and mark the new folder tree as troubled. The intrepid sysadmin would resolve the problems and eventually use the new folder tree.

Today's Linux file systems, modular kernals, and dynamic libraries enable multiple editions of files to live among each other -- a good thing -- but they are nearly impossible to find and ferret out the updates with the same ease as the olde ways (simply diff the listing of folder contents watching dates and file "version" details).

One Man's Opinion,
~~~ 0;-Dan

---

