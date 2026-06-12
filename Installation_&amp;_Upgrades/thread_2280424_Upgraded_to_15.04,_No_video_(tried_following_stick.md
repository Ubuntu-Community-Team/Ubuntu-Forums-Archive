---
title: "Upgraded to 15.04, No video (tried following sticky)"
date: 2015-05-30
forum: Installation &amp; Upgrades
---

### Post by bryan50 on 2015-05-30
Hello everyone!

I hope someone can assist me. I am a total ubuntu noob so please bare with me! I also tried following the sticky thread but dear god... so complicated. 

-Just upgraded to 15.04 -I pick Ubuntu from GRUB -Purple screen with Ubuntu logo appears but right after, the screen goes  completely black. Not blank as in the screen is on showing a black  screen but the screen completely turns off although I hear the classic  ubuntu sound.


  lspci | grep VGA  shows:
  00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)


  If I hit e on GRUB and change silent splash (i think thats what it says) to nomodeset I get video!  I went to software  and checked for drivers but only the network card appears, I see nothing for intel. I also tried installing the Intel Linux Graphics Installer but it said my version was not supported. I then tried installing **i965-va-driver  **but they were already installed so now Im lost. I usually get by with google but this time, not so much.

Dell Inspiron 1520

 
I appreciate any assistance!



EDIT:

Looking at system details, its shows the following:

Graphics: Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)

Followed #18:
--
Manual fix, create /etc/X11/xorg.conf and write the following into it:
 Section "Device"
        Identifier      "My device"
        Driver          "intel"
EndSection

--

 as per [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779) per [http://ubuntuforums.org/showthread.php?t=2278628](http://ubuntuforums.org/showthread.php?t=2278628) but no good

---

### Post by xartion on 2015-06-04
Please let me know if you ever find a fix for this. I have the same GPU (GM965/GL960) and have the same exact problem. I have literally tried probably 30 different kernel combinations and I have found that the last working kernel on which I can run 15.04 on the GM965 without a black screen on boot and at full speed -- i.e. without nomodeset hacks -- is 3.18.14 (which thankfully is LTS), available at:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.14-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.14-vivid/)

Anything newer, which starts with 3.19.*, simply does not work. I have tried the kernels listed in this bug report which supposedly fix what I think is a similar issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1455852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1455852) to no avail. So to summarize, the only way I could get 15.04 to work on GM965/GL960 is:

1) Use kernel 3.18.14 at the link posted above, OR:
2) Boot with 'nomodeset' which has horrible performance and is not acceptable for daily use

I am settling for 3.18.14 for now, but I fear that this is only somewhat of a temporary solution as I cannot stay on that kernel version forever

---

