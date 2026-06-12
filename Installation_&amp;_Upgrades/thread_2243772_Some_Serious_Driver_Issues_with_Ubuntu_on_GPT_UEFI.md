---
title: "Some Serious Driver Issues with Ubuntu on GPT UEFI laptop?"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by ramo2 on 2014-09-11
Ok, I've spent the last 10 hours learning all that I could about installing and partitioning, yet I have been unable to solve the problem. The caveat is that I know now a lot about linux installation. Please bear with me, this post might be a little long but I want to be clear what I've already tried.

Lets start from the beginning:  I have a Dell Inspiron i3531-1200BK, a cheap laptop from amazon that I wanted to dualboot ubuntu and windows 8.1. 
The laptop is GPT with UEFI and SecureBoot enabled. I disabled fast start up and the liveusb boots up fine: **although the screen flickers which may be a clue to my problems.**

I have many partitions for windows 8.1. For ubuntu, /home is at sda9, swap is on sda8, and / is on sda7.
So, I installed ubuntu and didn't really test it. Finally, I noticed that the brightness keys did not work. I followed this link's advice:
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)
and also changed the grub to add acpi_backlight=vendor.  For the record, the command ls /sys/class/backlight shows: acpi_video0 intel_backlight

After rebooting, I was getting black screens or the right-half of the screen was purple while the left side showed the desktop. I played around with changing grub w/ changing 20-intel.conf and vice versa.

Eventually, I was left with a black screen after logging in. There,** I noticed that I can't even access the virtual consoles tty1-7, I used ctrl-alt f1-7 and nothing. for some reason only f4 worked and then I was stuck in it. I got mad and hit some keys and "fn+windows+f7" got me back to the gui(before logging in with the black screen). **
Interesting thing to mention, the key for f2 for instance is internet, when I press ctrl alt f2, internet is disconnected. 

I have never had virtual consoles not work with any distribution of linux ever. So I am really confused. I reinstalled ubuntu twice and same problem. Wiped Ubuntu and deleted the grub. From there, I tried Manjaro and that was probably 1000X worse. X server failed to load, grub wouldn't start,etc. Some of the problems were very similar(with black screens and flickering). So I assume it has something to do with drivers. 

Previously Ubuntu shared the same efi partition as the windows bootloader and I used grub. Right now, windows is the only os on my computer. I am using ubuntu liveusb and all the problems are there. 

The confusing output to  " ps a" is :
  PID TTY      STAT   TIME COMMAND
 1566 tty4     Ss     0:00 /bin/login -f       
 1570 tty5     Ss     0:00 /bin/login -f       
 1591 tty2     Ss     0:00 /bin/login -f       
 1598 tty3     Ss     0:00 /bin/login -f       
 1620 tty6     Ss     0:00 /bin/login -f       
 1810 tty4     S+     0:00 -bash
 1854 tty2     S+     0:00 -bash
 1865 tty5     S+     0:00 -bash
 1912 tty3     S+     0:00 -bash
 1957 tty6     S+     0:00 -bash
 1995 tty1     Ss     0:00 /bin/login -f       
 2003 tty7     Ssl+   0:16 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightd
 2093 tty1     S+     0:00 -bash
 3979 pts/3    Ss     0:00 bash
 4048 pts/3    R+     0:00 ps a




Thank you,
Ramo

---

### Post by fantab on 2014-09-11
What graphics do you have in there?
If you have any GPU that uses 'proprietory' drivers then perhaps loading 'open-source' generic video driver at boot may help.
Try booting Ubuntu after appending '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option.

We can install an appropriate driver later....

---

### Post by oldfred on 2014-09-11
While this is on high end Dell's it says some of the setting may apply to all Intel (or all Intel Dells?).
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


 Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)


 Dell 15Z video settings with 13.10 gnome
[http://ubuntuforums.org/showthread.php?t=2194162](http://ubuntuforums.org/showthread.php?t=2194162)

---

### Post by ramo2 on 2014-09-11
**To Fantab:**
  I am using the liveusb and booted up with nomodeset added to the grub. Same problems (no brightness) and can't access tty1-6 with the exception of 4 which works. But tty4 gets stuck. 

According to Windows 8.1, I am using an Intel (R) HD graphics, found this under Display Adapters. 

According to Ubuntu liveusb, I am using "Gallium 0.4 on llvmpipe(LLVM 3.4, 128 bits). I went to details and graphics.

Very confusing and the screen is so dark.

**To oldfred:**
   I did not understand this part of the link. If I install Ubuntu without efi, then I wouldn't be able to boot windows.

Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.

---

### Post by ramo2 on 2014-09-11
I tried this:


install xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf

from this site: [https://01.org/linuxgraphics/node/316](https://01.org/linuxgraphics/node/316)

No change

---

### Post by oldfred on 2014-09-11
On the "legacy Option Rom" setting, I am also confused. I do not have Dell and have understood that UEFI & CSM/BIOS are totally separate. But it seemed that there must be some crossover with Dell and you need that on even if actually booting with UEFI. Some systems do let you have both UEFI & CSM on and system first looks to efi partition then to MBR for booting.

See ubfan1's boot options. Many Intel chips need settings, some several of them.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

This user said it worked with all these settings. I think some may conflict, but you could try them.

 [http://ubuntuforums.org/showthread.php?t=2191814](http://ubuntuforums.org/showthread.php?t=2191814)
acpi_backlight=vendor dell_laptop.backlight=0 pcie_aspm=force i915.i915_enable_rc6=1 drm.vblankoffdelay=1 i915.semaphores=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 vt.handoff=7 quiet splash elevator=deadline acpi_osi=linux

---

### Post by ramo2 on 2014-09-11
I ran those commands with all the grub settings and no change. I ran it legacy and no change. 

I am really stuck

---

### Post by oldfred on 2014-09-12
When you use boot parameters are you still leaving quiet splash? Better to leave those out so you can see progress of boot process. And while it often stops at battery state, the actual error is usually several lines above that messge.

---

### Post by ramo2 on 2014-09-12
Without the quiet splash screen the last thing it says is : initializing i915..... 0. I assume the 0 means success. 

I have intel(r) hd graphics on a celeron processor.
Ubuntu says gallium. 

Weird thing is that is can't access tty with Ctrl alt f keys. With the exception of f4. Then fn key and windows keys and f keys let me switch between virtual consoles. 

Another thing is that the virtual consoles only seem to recognize 2/3 of the screen then it cuts off and makes a new line. The GUI does this too but it adjusts.

---

### Post by oldfred on 2014-09-12
You need one or more of the Intel boot options in place of quiet splash. 
The boot options that work seem to vary by model of Intel video chip/version even though all use the same i915 driver.

0 usually means no error and each number then means some different type of error. Never seen list of what codes may mean though.

I still think it is related to video issues.
       Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by ramo2 on 2014-09-13
ok, i want to tackle this one problem at a time. First off when booting i get this: 
[http://tinypic.com/view.php?pic=24qju2o&s=8#.VBPKma24G00](http://tinypic.com/view.php?pic=24qju2o&s=8#.VBPKma24G00)
[http://tinypic.com/view.php?pic=212vho0&s=8#.VBPKuq24G00](http://tinypic.com/view.php?pic=212vho0&s=8#.VBPKuq24G00)
[http://tinypic.com/view.php?pic=5nn1xz&s=8#.VBPK4a24G00](http://tinypic.com/view.php?pic=5nn1xz&s=8#.VBPK4a24G00)

you see how it cuts off.

---

### Post by ramo2 on 2014-09-13
the way the tty console cuts off is especially weird, at least to me.

---

### Post by oldfred on 2014-09-13
Your second post is a normal log in. Your third post looks like a terminal login with a book on one of your keys causing it to repeat. (one user did admit that was an issue once. :)  )

When booting I do get a terminal login for just a second then it goes to video mode and I log in.

---

### Post by ramo2 on 2014-09-13
I don't think my question was clear. If you look at the picture you can see that the Ubuntu desktop does not take the entire laptop LCD screen. The right half is black or purple. 

Also there isn't a book on the keys. I repeated the letter to show how the terminal typing does not reach the end of the monitor. It cuts off 1/3 of the screen like the monitor is only 12 in instead of 15 inches

---

### Post by oldfred on 2014-09-13
Are you able to boot into gui but with wrong graphics X by Y dimensions.
Then you may need gfxmode setting for grub and the Intel boot parameter on the Linux line to set correct dimensions. See post #6 and link to settings by ubfan1.

Often one of these, but change to your exact monitor size, not 1280x1024.
i915.i915_enable_rc6=1
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

---

