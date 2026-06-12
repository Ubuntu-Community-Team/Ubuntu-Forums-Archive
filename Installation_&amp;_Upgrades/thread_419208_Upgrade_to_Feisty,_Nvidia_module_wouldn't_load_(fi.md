---
title: "Upgrade to Feisty, Nvidia module wouldn't load (fixed!)"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by ukyo050 on 2007-04-22
I wasted several hours researching and debugging an Nvidia problem preventing the 'nvidia' driver from loading.  I eventually fixed it, but not having seen the problem listed elsewhere, wanted to share the details here.

On the first reboot after running the upgrade from Edgy Eft, gdm failed to start and gave me a blue screen of death, with the option to view detailed log messages about the failure.  There was something in the message about "Incorrect kernel version for nvidia module" (as best I can remember).  This was my first clue, but I took it in the wrong direction.

I spent the next couple hours installing, purging, reinstalling, purging, the various Nvidia-glx-new, Nvidia-glx-legacy, and Nvidia-glx modules.  It wasn't until I started trying to compile the downloaded drivers from Nvidia's site that I finally figured out what was going on.

By chance I ran the command `uname -r` and realized that even though the 2.6.20-15 kernel was installed, my Grub confiuration had not been updated, and was still booting by default into the 2.6.17- kernel.  So step 1 was to manually select the 2.6.20-15 kernel boot option in Grub.

This got me back to the original "Incorrect version/API" error message.  After some trial and error I found that the nvidia-glx module was compiled against an older kernel or Xorg version.  The nvidia-glx driver version is 1.0-9631.  After remove-purging nvidia-glx and instead installing nvidia-glx-new, I found this driver, version 1.0-9755, was a match for the version/API that was causing a problem.

So I restarted gdm, and sure enough, my same old Edgy xorg.conf worked fine and X started up with Twinview enabled and everything!

**So to summarize :) **
If X fails to start after upgrading to Feisty Fawn, check what kernel you're running with `uname -r`.  If it's 2.6.20-15, make sure you've got nvidia-glx-new installed, as opposed to nvidia-glx.  If you're not on kernel 2.6.20-15, check your grub configuration or boot options, cause as best I can tell you *should* be on 2.6.20-15 if you've upgraded to Feisty.

Just ask if you need elaboration on installing/purging/etc.  Hope this saves someone else all the time I wasted figuring this out!

---

### Post by creamcheeze77 on 2007-04-22
i've been having this exact same problem! i installed nvidia-glx-new, but i didn't purge nvidia-glx. how do you do this? thanks for posting.

---

### Post by RawMustard on 2007-04-22
sudo apt-get --purge remove nvidia-glx
or from synaptic, find nvidia-glx and select mark for complete removal

---

### Post by Derspankster on 2007-04-23
Your post is of great interest to me because I saw a similar error message. However uname -r returns the right kernel for me. I just can't seem to get my 6200 card installed correctly. Right now I'm using the glx-new driver (9755) and it works with the exception that I have no mouse arrow. All I have is a fuzzy square. Beryl will start but with no controls, direct rendering is enabled and I get great fps with glxgears. If I had a mouse cursor I'd be golden.

---

### Post by Metz on 2007-04-23
I will try this when I get home this evening. I've had no end of problems getting Fiesty to work. I'm not running the wrong kernel, as this was a complete rebuild from the 7.04 Desktop CD. But I'm convinced my issue is to do with the various version of Nvidia drivers flying around in Restricted Driver Manager, Envy, etc. See [http://ubuntuforums.org/showthread.php?t=419011](http://ubuntuforums.org/showthread.php?t=419011)

So, I'll attemp a clean build again tonight, apply my patches for wireless to work, and then try to get the correct (nvidia-glx-new) installed as above.

This kind of post is very very important in this forum....

---

### Post by ACGilbert on 2007-04-23
Thanks so much ukyo050 ! ! !

My kernel was fine in grub -- just had to do the nvidia module thingy.

AC:)

---

### Post by sloopveedub on 2007-04-26
I was initially having this problem too.  I eventually realized that part of my problem is further complicated by having a triple boot system.  Windows 2k is installed on hda, Ubuntu on hdb1 and Opensuse on hdb2.  The O/S's were installed in that order too.  So, the grub that loads when the system is started is from Suse's partition -- no problems until I upgraded a few days ago (and rebooted after installing the nvidia driver).

So, I booted into Suse and edited grub's menu.lst file to point to the 2.6.20-15 kernel instead of the old 2.6.17 one per this thread's discussion.  Alas, it now tells me file is not found when I attempt to boot into Ubuntu!!  But I can see the .20-15 kernel in hdb1/boot (as well as the old .17-10 & .17-11 ones).  What's going on?!!  I need to get this fixed before I can even worry about the nvidia driver!!  :confused: 

From hdb2/boot/grub/menu.lst:
```
# Modified by YaST2. Last modification on Thu Apr 26 18:55:32 MDT 2007
default 0
timeout 8
gfxmenu (hd1,2)/boot/message

title Suse
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18.8-ccj45-default root=/dev/hdb3 vga=0x31a resume=/dev/hdb5 splash=silent showopts
    initrd /boot/initrd-2.6.18.8-ccj45-default

###Don't change this comment - YaST2 identifier: Original name: Ubuntu, kernel 2.6.17-11-generic (/dev/hdb1)###
title Ubuntu (Fiesty)
    kernel (hd1,0)/boot/vmlinuz-2.6.20-15-generic root=/dev/hdb1 ro quiet splash
    initrd (hd1,0)/boot/initrd-2.6.20-15-generic

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (hd0,0)
    chainloader (fd0)+1
```

---

### Post by John Jason Jordan on 2007-04-26
> **ukyo050 said:**
> This got me back to the original "Incorrect version/API" error message. After some trial and error I found that the nvidia-glx module was compiled against an older kernel or Xorg version. The nvidia-glx driver version is 1.0-9631. After remove-purging nvidia-glx and instead installing nvidia-glx-new, I found this driver, version 1.0-9755, was a match for the version/API that was causing a problem.
OK, I did this. It didn't work, but my situation may be different. 

I have had the nvidia-glx driver installed for a long time -- since Dapper -- although I have also used the nv driver a lot of the time. At the time I did the upgrade to Feisty the nVidia driver is what I was using. 

After the upgrade when it booted it dumped me to a command line and said that the video driver was wrong. I've been here several times in the past couple of years, so I just edited /etc/X11/xorg.conf and changed "nvidia" to "nv," then rebooted. This time the GUI came up and all was well. I didn't have the nVidia splash screen is all. 

I used it that way for a couple days while I fixed a couple of things that the upgrade to Feisty broke. Then I decided it was time to get the nVidia driver back. So I edited xorg.conf again and changed it back to "nvidia," then rebooted. This time the GUI came up just fine. However, there was no nVidia splash screen as before. Nevertheless, on the login window the characters were really fat -- a clear indication to me that I was using the nVidia driver. That was yesterday and it has been running fine ever since except for one small problem -- when I minimize an OpenOffice.org window I sometimes can't restore it to the desktop. So I decided to install the new driver that I just found out about here in this thread. Note that before I was using the old nvidia-glx driver with the new kernel and it worked OK with the possible exception of the OpenOffice problem.

So I opened Synaptic, marked nvidia-glx for a complete removal, and nvidia-glx-new for installation. After the process finished I opened the nVidia control panel and noticed that it said I still had the old driver. Well, of course -- I hadn't rebooted yet.

So I rebooted and, guess what? I got dumped to the command line -- wrong driver. So once again I edited xorg.conf back to "nv" and rebooted. Here I am now back running fine, but without the nVidia drivers.

So then I opened Synaptic and uninstalled the nvidia-glx-new driver and just left it at that. Neither driver is installed. And just to be sure it was OK I rebooted. No problem, everything is working fine. I just don't have the nVidia driver.

Then I decided to use Automatix2 instead of trying to do it manually. But Automatix2 said i already had the nVidia driver installed. Then it stopped displaying the nVidia driver in its list of programs to install.

I'm functioning fine but i'd like to get the nVidia driver back. What I don't understand is whether something else needs to be installed besides nvidia-glx or nvidia-glx-new. Also I don't understand why the old one worked for me with the 2.6.20-15-generic kernel when it wouldn't work for you, and vice-versa.

---

### Post by murrayjc on 2007-04-30
I'm in the exact same situation, it seems. I upgraded from edgy to feisty still using the nv drivers without 3D accel capability. I tried to enable Desktop Effects and it told me I needed to enable the nvidia driver with 3D accel capability. The restricted driver manager installed the nvidia-glx driver automatically and everything worked fine (wobbly windows, workspaces on a cube, etc...), albeit a little slow... So I thought I would give the nvidia-glx-new drivers a try. Why not, right? If it goes wrong, I'll just reinstall the nvidia-glx package and I'll have my old config back again, right? Nope.

This is what I did to apparently screw everything up: I disabled the nvidia-glx driver and completely removed it. I installed the glx-new driver, enabled it as suggested in the instructions (sudo nvidia-glx-config enable) and X failed to start on reboot. I then reverted to the safe xorg.conf file that calls out the nv driver. This still works, thank goodness. I then completely removed the nvidia-glx-new driver and reinstalled the nvidia-glx driver in the exact same manner as used when I upgraded to feisty. I fully expected this to give me back my previous working configuration, but no! X still fails to start on reboot. WTF? Apparently the install/enable process for the nvidia-glx-new driver changes something somewhere that cant be "unchanged" by completely removing the nvidia-glx-new driver and/or reinstalling the nvidia-glx driver. Stupid? Four out of five dentists say "yes". Anyone know what has been changed and how to "unchange" it? Thanks a bunch...

---

