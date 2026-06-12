---
title: "Ubuntu 15.04, sound stopped working yesterday, please help!"
date: 2015-08-21
forum: Installation &amp; Upgrades
---

### Post by ken63 on 2015-08-21
Hi,

I suffered the "login loop" and was able to recover from that, by reinstalling, unfortunately several times -- each time I'd reinstall, it would come up to the login screen, I could log in, and then I'd set the proprietary driver for the AMD graphics card, reboot, and would be stuck in the "login loop" again.  Fortunately I tried NOT using fglrx (or fglrx-update), rebooted, and I got past that.  Note that I have no idea what I did to cause it; I hadn't rebooted in a while, so it may have been something installed or updated.

The sound, however, continues to refuse to work.

Then I tried (from a search) "sudo apt-get remove --purge alsa-utils" and then "sudo apt-get install alsa-utils" but it didn't fix the sound.  I checked the connections, everything seemed okay.

Then I booted the Ubuntu 15.04 live DVD, clicked "Try Ubuntu", and played a Youtube video and I heard sound.  Rebooted into the installation, sound again not working (not even the drums at the login screen or during login).

Please help, I'd like to get sound working again!  If you need any more details please let me know, I hope to be able to help others if they end up in this situation.

Thanks,
Ken

PS Also, if I type "alsamixer" at a command prompt, I get the error: "cannot open mixer: No such file or directory"; this error persisted through the apt-get remove/install above.

PPS Also, I no longer see the Proprietary Drivers entry in system settings!  So I can't enable the AMD drivers even if I wanted to.  Is that related?

---

### Post by ken63 on 2015-08-24
Fixed!

Randomly, I was helping someone else and needed a VM, so I installed VirtualBox, and then booted a 15.04 Live CD in a VM, and I heard the drums!  I thought, that's weird, I wonder if the sound only works in the VM, or if it was fixed generally?  So I went to [https://youtu.be/rHAR1O2cW1Q](https://youtu.be/rHAR1O2cW1Q) (a recent Phish concert that I wanted to watch), and got sound!

So there must have been some kernel module that VirtualBox inserted, which worked with the sound device?  I had had VirtualBox installed before I reinstalled, and it did tell me "some applications may need to be reinstalled" but it never said anything about sound would break as a result.

So: my issue is resolved.  However, developers might want to look into what VirtualBox does to the kernel modules, in order to provide better info to the user in this situation.

---

