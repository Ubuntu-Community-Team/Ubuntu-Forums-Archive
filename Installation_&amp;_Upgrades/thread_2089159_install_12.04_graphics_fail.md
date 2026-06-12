---
title: "install 12.04 graphics fail"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by Carcharoth on 2012-11-28
Board: BIOSTAR Group N68S3+ 
on board video
NVIDIA GeForce 7025 / NVIDIA nForce 630a [Display adapter]
LG L1980U [Monitor] (19.1"vis, s/n 6364, March 2005)

trying to install along side Windows XP from USB
the graphics screen never works - it has come up scrambled, or if I wait patiently it will apparently make several attempts about 3 different drivers - but ends up with the original standard blank screen.

when I installed Ubuntu 11.10, on a different hard drive, I had to "fix" the graphics drivers. but how do I fix my drivers when I cannot read the screen?

would my best answer simply be to procure a video card? (and if so, suggestions solicited) but my first choice would be to simply make my present hardware work.

what I want MOST is to understand what is happening to me in this process, and any enlightenment appreciated.

---

### Post by haqking on 2012-11-28
You might try "nomodset" in grub line entry )reach grub by pressing shift if not already showing)

or boot to recovery console and drop to prompt and run the downloaded Nvidia.run file with (you can get it here [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

```
sh Nvidia.....x.x.x.x.x.x.x.x.run
```latest is 3.10

You may need to blacklist nouveau too but the .run file will do this for you or should anyways

Cheers

---

### Post by lincoln32 on 2012-11-28
[http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

this should work for yours also

---

### Post by John butler on 2012-11-28
Me too ! Clean install of 12.04 ( from CD )has produced a black screen with " cannot display this video mode ". I can go no further . " Shift" key does not help .

---

### Post by dannyboy79 on 2012-11-28
you can hit ctrl-alt-F1 to take you to terminal session 1. login to the textual environment using your username and password. What driver are you currently trying to use?
Issue the following command
```
dmesg | grep NVIDIA
```

---

### Post by 2F4U on 2012-11-28
> **John butler said:**
> Me too ! Clean install of 12.04 ( from CD )has produced a black screen with " cannot display this video mode ". I can go no further . " Shift" key does not help .

First of all, it would be a good idea to post your hardware specs, since they are most likely not the same as those of the OP.

Since you seem to have the system already installed, you can try to get to a console by pressing Ctrl-Alt-F1 simultaneously. Then edit /etc/default/grub (with sudo privileges) and add nomodeset. Save the file, execute sudo update-grub, reboot and see if it makes things working.

This was the very short form, more information is available in these threads:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by dannyboy79 on 2012-11-28
> **John butler said:**
> Me too ! Clean install of 12.04 ( from CD )has produced a black screen with " cannot display this video mode ". I can go no further . " Shift" key does not help .are you tapping the shift key directly after seeing the BIOS screen? This should take you to Grub boot menu where you can add the nomodeset option

---

