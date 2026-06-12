---
title: "Anyone using the new 2.6.32-16 with Guest Additions yet?"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by grubdude on 2010-03-08
Just upgraded today and now Virtualbox Guest Additions no longer properly sizes screen and the Seamless Mode is greyed out. I have them installed from the previous -15 kernel and they worked fine. Now my display only fill at most 3/4 of the display.

I tried this on 32 bit and x64 and both have the same problem...Reinstalling guest additions causes kernel panic at boot....

Sure hope they are aware of this after filing bug report and fix it soon. Very annoying if using a virtual machine.

---

### Post by grubdude on 2010-03-08
Update: This may be partially a user issue. I just upgraded the kernel on my 9.10 install and the Guest Additions did the same thing. So, I am assuming that I need to reinstall the guest additions on the new kernel.
 
However, when I tried that before it hosed my 10.04 install. Anyone have any experience with this and the proper way to deal with kernel upgrades?
 
Just reinstalled Guest Additions on my 9.10. It is running fine now with new kernel. Tried it on 10.04 and it says only able to run in low resolution mode...

---

### Post by appultaart on 2010-03-08
Perhaps related? : I have a problem to compile another kernel module (Nvidia, in my case) in 2.6.32-16... I get a complaint that kernel is not built against my system's gcc or, or kernel sources are missing (if i recall right). 

Does virtualbox not also need to build a module before running under a new kernel? 

Just a guess: perhaps 10.04's 2.6.32-16-generic (64bit) is built with different parameters, which makes module compilation invalid?

---

### Post by rockyjones on 2010-03-09
Does the same thing for me too.  I changed the /etc/default/grub file to boot the -15 kernel and it works fine again with it (other than seamless mouse action - that has never worked for me with Lucid).  I think I'll keep it booting the previous kernel for a bit until the next kernel update (or fix comes along).

---

### Post by myoldhouse on 2010-03-09
Ditto for me. Virtualbox 3.1.4 and Lucid with the 2.6.32-16 kernel (64 bit) as a guest and the Guest Additions don't install. Like 'rockyjones' above, I modified /etc/default/grub to use the "saved" option so that I boot into the 2.6.32-15 kernel that works OK. Maybe it will be fixed by the first Beta? I guess that is why it is an Alpha release. 8)

---

### Post by grubdude on 2010-03-09
So, are you guys saying that you did all the current updates but are just booting into -15 for now? I assume that you just chose to run in low resolution mode and then changed the grub?

Right now I am using a fresh install and have not applied any updates since the install but the update list is growing. Would it be best to just update everything and then modify the grub to boot into -15, or just keep running as is with no updates for now?

How will we know when there is a fix, when -17 is released? Thanks.

What is the best/easiest way to modify the grub to boot into -15 then back later to -17 or whatever fixes this?

---

### Post by myoldhouse on 2010-03-09
Yep. But the Guest Additions install and work fine with the -15 kernel so I'm not running in low resolution (currently using 1440x900). Mouse integration works fine as well. The only other problem I have with Lucid is with the Plymouth package but that has nothing to do with the kernel version and I have a work around for it anyway. If you need a tutorial on modifying the GRUB2 menu, see this forum link: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by grubdude on 2010-03-09
Since I rarely reboot, couldn't I in theory just do:  **grub-reboot "Ubuntu, Linux 2.6.32-15-generic"  **to accomplish this on a temporary basis?Also when the new kernel with a fix arrives would I want to boot into -16 and then upgrade, or just do it through the -15 boot? Thanks

---

### Post by grubdude on 2010-03-09
By the way, I assume that if I boot back into -15 until guest additions is fixed in a newer kernel, it makes no sense to run update manager for updates, yes?

---

### Post by Keyper7 on 2010-03-09
> **grubdude said:**
> By the way, I assume that if I boot back into -15 until guest additions is fixed in a newer kernel, it makes no sense to run update manager for updates, yes?

No. Keep updating.

Most of the updates are completely independent of the kernel.

The only updates from which you won't benefit are driver updates. And even those can installed with no harm.

Just continue with the good old updating routine.

---

### Post by grubdude on 2010-03-09
Okay, thanks...Will using the temporary command that I posted work?

---

### Post by Keyper7 on 2010-03-09
I have no idea, I never used grub-reboot myself.

However, as a temporary solution, editing GRUB_DEFAULT in /etc/default/grub and running update-grub could also work.

---

### Post by grubdude on 2010-03-09
okay so just insert **"Ubuntu, Linux 2.6.32-15-generic"** after the GRUB_DEFAULT versus 0?

---

### Post by rockyjones on 2010-03-09
Grubdude... do this in a terminal window

sudo gedit /etc/default/grub

then change the first line that says GRUB_DEFAULT=0
to GRUB_DEFAULT=2

Click on save then run
sudo update-grub2

reboot and this will then boot whatever is on the third line of your grub.cfg file.  Assuming you have two or more images in grub, it will boot the second one.  You might want to look at the contents of /boot/grub/grub.cfg to make sure you actually have two images listed as this will leave you hanging if you don't.

---

### Post by myoldhouse on 2010-03-10
I think a slightly better way to modify /etc/default/grub is to do the following:

Boot and hold the shift key until the grub menu displays. Select the -15 kernel from the boot menu and boot normally. Then edit the /etc/default/grub file as follows:

gksu gedit /etc/default/grub

Change the first line that says GRUB_DEFAULT=0
to GRUB_DEFAULT=saved

Save the edited grub file and run the following from a terminal window:

sudo update-grub2

Now, every time you boot, Grub2 will always select as default the last kernel that you booted into regardless of its position in the grub menu list. In this case, since you booted into -15 kernel last, it will default to that one, even if you add more kernels. If you purposely change to another kernel by manual selection from the grub boot menu then that kernel will become the new default. This is a neat feature of Grub2.

---

### Post by grubdude on 2010-03-10
Thanks to you both. Unfortunately, I tried the first approach before seeing your suggestion. However, it is booting fine into -15 now and I just reinstalled Guest additions so it is working fine.

I just updated everything, so I am good to go, I guess. Now if they can just fix what they broke in -16, I will be a happy camper!  Thanks.

---

### Post by FakeOutdoorsman on 2010-03-29
Looks like this was fixed upstream in version 3.1.6:
[Ticket 5737: Guest Additions: No seamless, no Shared Folders - Ubuntu Lucid Lynx alpha1](http://www.virtualbox.org/ticket/5737)

---

