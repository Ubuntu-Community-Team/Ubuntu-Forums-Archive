---
title: "Ubuntu Upgrade: Verify New Kernel associated with Boot Option in Menu.lst (before Re-"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Johnny M! on 2010-05-02
Upgrading an Existing version of Ubuntu?

Insure an appropriate (new) Kernel is associated with your new Ubuntu Install (in Menu.lst) before allowing your system to Re-Boot!
------------------------------------------------------------------------------------------------------------------------

Ubuntu Upgrade Problems caused by a failure to associate the (new) required kernel with the (new) Upgraded version of Ubuntu may cause your system not to Boot - leaving you with an inoperable computer and no easy way to recover.

Reference these two Install/Upgrade Forum Threads:

[http://ubuntuforums.org/showthread.php?t=1468156](http://ubuntuforums.org/showthread.php?t=1468156)
[http://ubuntuforums.org/showthread.php?t=146858](http://ubuntuforums.org/showthread.php?t=146858)

I have run into this problem on my last two upgrades:
- 9.04 to 9.10
and
-9.10 to 10.04

How does this Happen?

Because I don't let the system (Update Manager) automatically install a new Boot/GRUB/Menu.lst file.  I don't let this automatically happen because modifications to GRUB (on an earlier upgrade) had destroyed my ability to dual-Boot into Windows in the Past.   So I prefer to manually edit the Menu.lst file myself  

During the last phase of the Upgrade process, you encounter a few User Prompts:  What asked about new Boot options, I click "Forward" (keep the current configuration) at the User Prompt; thus retaining the old Menu.lst (and old Kernel).  But where you run into trouble is if the new Ubuntu Build Version is incompatible with a previous kernel (and requires a new kernel).  If (after Upgrade Download+Setup+Install) you allow the system to re-Boot before you insure a proper Kernel is associated with your Ubuntu boot option (in menu.lst); you could run into serious trouble like I did (see previous posts).

IMPORTANT:  

- Find out what the new Kernel should be before starting the Upgrade Process (that info will be in Support / Forums).

- Before allowing your Upgraded Ubuntu Build to Re-Boot; Verify the correct New Kernel is associated with your Boot Option listed in Menu/lst:

- Pathway:  Places - Computer - File System - boot/grub/menu.lst 

- If required, Edit the Boot Option with the following commwand (in Terminal):

sudo gedit /boot/grub/menu.lst

Save the File

Now (and not before) it is Safe to Re-Boot into your freshly minted New Ubuntu Build !!!!

Hope this can help someone avoid my previous pitfalls !

BVR
Johnny M!
:guitar:
Rock On !

---

### Post by Johnny M! on 2010-05-02
PS:  I forgot to mention where you can reference the latest and greatest Linux Kernels for your new version of Ubuntu:

Places - Computer - File System - Boot

The kernels are listed under boot and look something like this:

- vmlinuz-2.6.32-21-generic
- initrd.img-2.6.32-21-generic


And your Menu.lst text you want to edit 

Places - Computer - File System - Boot/Grub/menu.lst

looks like this:

title          Ubuntu 10.04
uuid        1f74fa33-b019-4fe7-ab93-44a43.........
kernel      /boot/vmlinuz-2.6.32-21-generic root=UUID=1f74fa33-b019-4fe7-ab93-44a43499c08a ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

-------------------------------------------------------------------------------------------------

:lolflag:

---

