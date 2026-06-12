---
title: "NVidia card problems"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by oneadvent on 2007-10-02
I was trying to install Ubuntu 7.04 on my friends laptop. He has an Nvidia 8600 GS, and the installer goes all bonkers, and does not let me install. 

How do I install it...? I know that is not a lot of info, but it is not right in front of me, and its really just bugging me.

Thx in advance

---

### Post by Pumalite on 2007-10-02
Is your friend's laptop a dv9000?

---

### Post by oneadvent on 2007-10-03
no it is f3sv

---

### Post by oneadvent on 2007-10-03
sorry for huge delay, i forgot to subscribe to thread...

---

### Post by dabl on 2007-10-03
What do you mean by "does not let me"?

Where does it stop?  What is the last thing that seems to work correctly?

---

### Post by oneadvent on 2007-10-03
it asks what you want to do at start up, select start or install ubuntu and it does the boot up screen, with the bar going back and forth, then it says, cant access tty job control turned off
(initramfs)  [<- that is a  prompt]

in safe graphics mode it goes to the boot screen, bar back and forth, then same thing.

oh, and on that text screen it is using the ash shell. not bash..

---

### Post by dabl on 2007-10-03
OK.  Your friend's 8600 is not going to be auto-detected by the xserver configuration routine, and a compounding problem is that it may be gagging on the *buntu splash screen.  Kind of a double-whammy.  :(

First, I recommend the Alternate Install CD, rather than Live CD. It is "character mode" and will run the whole installation with VGA graphics, so at least you can get it installed.

Upon reboot, you'll get a black screen.  Just follow this to get past it and get a GUI:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)   (it's the same for Ubuntu as Kubuntu)

Once you've got a GUI login working, then you can follow this to install an Nvidia proprietary driver:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

Personally, I'd ignore the "Restricted Drivers Manager" -- it does not help you.

Finally, you've got a problem with the splash screen.  Edit the kernel boot line of /boot/grub/menu.lst and add the option "nosplash=y" at the end of it, so it looks approximately like this:

```
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=b1869c3e-b13a-4772-914c-bcc6db718967 ro quiet nosplash=y
```

That should get you going.  :guitar:

---

### Post by oneadvent on 2007-10-03
ok, that is a weekend thing....being that i need to download alternate, so i will get back if it works

---

### Post by neuralmer on 2007-10-07
I recently purchased an ASUS F3SV and upgraded the memory to 4GB.  Given my multiple failed attempts to get Ubuntu installed with accelerated graphics, I figured my experiences might be of use, and I will recount my attempts here.  I am trying to install Ubuntu 7.04/Feisty Fawn via Alternate Install method, and I am using envy to install the nVidia video driver (version 100.14.19).

After following the instructions in this thread I still was not able to get the nvidia driver to run.  The laptop would black screen (back light still on) and lock up hard (caps lock key does not toggle light, Alt+SysRq+b does not reboot, nothing).  Looking at X logfile I noticed that the video card was reporting to have 512MB of ram (? the vendor's add clearly indicated 256MB dedicated video ram).  This got me to thinking.  If the kernel already already has 4GB of memory to map, it will be problematic for it to map in any additional memory.  The default kernel config is set to map up to 4GB of ram, but there is a 64GB limit option.

Following the procedures from the Master Kernel Thread in the forums, I installed the latest kernel 2.6.22.9 and enabled the 64GB limit option and used envy to install the video driver.  This appeared to work.  Unfortunately, it only sorta worked - once X started, the login screen had a psychodelic color scheme it looked like the image was indexed and that the palette had been corrupted.  I restarted with only a 24bit color screen mode in the list of available screen modes with no change.

I wanted to make sure that it was the main memory that was causing a problem.  I tried installing after removing one of the memory sticks, and surprise! the installation worked beautifully.  No obvious problems using the nvidia driver.

I tried to install 64-bit Ubuntu via alternate install.  This worked, and envy ran successfully installing the new driver.  On reboot the splash screen was causing problems, so I disabled it from grub with nosplash=y on the boot line.  X still black screened/hard lock up when trying to use the nvidia driver.

It was time to start lying to the kernel.  I reinstalled 32-bit Ubuntu, used envy to install the video driver, and told the kernel that it only had 2.5GB of main memory, despite what the bios was telling it with mem=0xA0000000 in the boot parameters.  This finally did appease the beast.  I was able to run UT2004 smoothly.

Even with this setup, the system is not stable.  As part of gaming or moving some files around, clearly something became tainted with the video card.  I rebooted, and the screen locked up hard again (even with the memory restriction).  Setting xorg.conf to use the vesa driver at 1280x800 and restarting seemed to clear this problem as I was able to switch back to the nvidia driver with 1680x1050 resolution.

Any suggestions on what to do to be able to use 4GB of main memory _and_ use the video card for what it was designed to do?  Has anyone else with ASUS F3SV model had more success with the 64-bit version of Ubuntu and nvidia driver?  Anyone else expect to find 256MB of video ram, but X Windows log file reports 512MB?  Is this 256MB dedicated + 256MB shared?

---

### Post by neuralmer on 2008-02-08
Problem has been resolved with recent version of bios, v207.  Flashed bios, now video card works with 32-bit Ubuntu (without explicit 2.5GB memory restriction) and 32-bit Windows XP with 4GB ram installed.  Linux and XP report slightly more than 3GB of RAM.  Thanks, _maydayjay_.

---

