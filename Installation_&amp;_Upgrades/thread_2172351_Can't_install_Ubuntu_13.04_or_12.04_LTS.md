---
title: "Can't install Ubuntu 13.04 or 12.04 LTS"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by jeff24 on 2013-09-04
I tried installing both with the windows installer and burning them to DVDs but it won't work.
After the install process I reboot into the Ubuntu partition. I first see the loading screen and it says preparing for first time install, shortly after the screen goes black and random green lines are around the screen and nothing happens, I've looked at other posts and tried to ctrl+ tab +f1 and I get a screen full or errors. I'm lead to believe it is a graphics error but I don't know what to do about it. Help!

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Installation & Upgrades**.*

... but possibly should be in ***Mutimedia & Video***. 

Welcome. You will have more luck here, but to be truthful, there are not many Wubi gurus on the forums (and no Wubi sub-forum possibly as a consequence) as Wubi is intended for Windows users to 'try before you buy' and is *not* considered a permanent solution. Good luck, though. 

Solutions you might find that apply to a regular Ubuntu install or dual-boot (Windows and Ubuntu on separate partitions) will probably NOT apply to a Wubi install. That is something specific and totally different to Ubuntu installed to its own partition.

---

### Post by oldfred on 2013-09-04
Often a video issue.
What system, and what video card/chip?
New UEFI or older BIOS based system?

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Screen shots of both BIOS accessibility screen and UEFI grub menu screen to add nomodeset:

 [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by jeff24 on 2013-09-04
Thanks for the solutions but I have tried making a separate partition and got the same results :(

---

### Post by jeff24 on 2013-09-04
I've reattempt to try to install it through a USB stick. This error keeps popping up right away and occasionally the screen will get all glitchy looking. Does anyone know why this is happening?

[http://i.imgur.com/IkGs0PB.jpg](http://i.imgur.com/IkGs0PB.jpg)

This happens right away when I try to boot from the USB

---

### Post by Bucky Ball on 2013-09-04
Yep. Graphics. Refer post #3. Didn't help?

---

### Post by jeff24 on 2013-09-05
It did actually lol. It ended up being the issue. Thank you very much oldfred!

---

### Post by Bucky Ball on 2013-09-05
Great news. Please mark thread as solved from Thread Tools at top right of thread. Good luck and enjoy! ;)

---

