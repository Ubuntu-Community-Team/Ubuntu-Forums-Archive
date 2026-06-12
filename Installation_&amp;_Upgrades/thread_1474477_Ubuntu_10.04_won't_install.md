---
title: "Ubuntu 10.04 won't install"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by the_bob on 2010-05-06
Hey all. I have been trying to install Ubuntu on my second PC. It installs fine on my first.
On my second it won't boot into live and wubi installs in windows, but won't finish the install.

Both have the same issue. The splash screen pops up and a second after the mouse pops up. Then it freezes and caps and scroll lock flash on and off. I have the same issue in the RC and the final release. 
Specs
Intel Core2Duo E4300 1.8GHz
Cheap Biostar motherboard
3GBs of DDR2
Nvidia 9600gt
320GB hard drive partitioned for dual boot.

I had Ubuntu 9.04 on it and it ran fine. I have since wiped the drive when I installed windows 7 though.

I have looked around the forums and google, but not found my issue.

---

### Post by koanhead on 2010-05-06
Try hitting the Esc key as soon as the splash screen pops up. You should then be able to see the boot messages (imo this should be the default, because errors *will* happen).
Hopefully the last few messages that pop up will shed some light on what's causing the problem.

---

### Post by the_bob on 2010-05-07
Ok well now it is not even bringing up the splash screen. Throwing a bunch up and at the bottom Rebooting in 30 seconds. I did it a few times and wrote down as much as I could. Not all in the correct order btw.

RIP !INEXACT!
This is not a software problem
Machine check processor content corrupt
No human readable MCE decoding support on this CPU type
Run the message though 'mcelog --ascii' to decode.

I'll write more down if you need. These looked to be the important stuff.

---

### Post by dino99 on 2010-05-07
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14 

really dont understand you install linux into a windoz file  :lolflag:

you can either install it on hdd or into virtualbox

---

### Post by lechien73 on 2010-05-07
It could indicate a hardware fault, or it could indicate that Ubuntu just isn't capable of reading the MCE (Machine Check Exception) codes for your machine and is raising a false positive.

Try:

[LIST=1]
[*]In the Grub menu, highlight Ubuntu and press 'e' for editing mode.
[*]Use the arrow keys to get to the 'kernel' line and add **nomce** just before the words "quiet splash".
[*]Press CTRL-X to reboot
[/LIST]

---

### Post by the_bob on 2010-05-07
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14 

really dont understand you install linux into a windoz file  :lolflag:

you can either install it on hdd or into virtualbox

Windows does some thing very well. As does Linux. Now if that rumored Steam Client for Linux comes out I would cut that Windows partition in a heartbeat.

Edit: Tried your fix lechien73. Still gives the same errors.

---

