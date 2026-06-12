---
title: "Can't boot ubuntu in UEFI mode!"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by JaZZyCooL on 2013-07-02
hello guys,
    I just download ubuntu 12.04 and was trying to install on my pre-installed windows 8 lenovo y400 laptop, I downloaded 12.04 write it to the USB using pendrivelinux, booted in using UEFI mode selected try and install ubuntu, but the screen blacks out it is more than 15 mins nothing is showing up. Can you guys please help me out.

Your help is highly appreciated.

---

### Post by poscomp on 2013-07-02
As far as I know, Windows 8 takes over the machine and won't allow booting from another OS. I just got a Lenovo G580 and immediately removed the windows 8 drive, replaced it with a 750GB drive and loaded from DVD, Windows 7 and Ubuntu 12.04. They both work fine but after I did the 500+ file update for Ubuntu the wireless card will not attach to my router. Before the update it worked fine, now, nothing.

---

### Post by oldfred on 2013-07-02
Is this an UltraBook with dual video and a small SSD using Intel SRT (RAID)?

You may have to turn off one video mode or the other in UEFI/BIOS if you can.
If using nVidia you need nomodeset. 

If booting in UEFI mode you get grub menu, use e and scroll down to linux line and replace quiet splash with nomodeset.
Screen shots here for boot after install. BIOS mode has accessibility screens for live boot which are different but then after install first boot also uses grub and also needs nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
Some very new systems need other boot parameters also.

Have you made Windows recovery flash drive?
Have you fully backed up Windows?
See link in my signature.

Other Lenovo, may be similar even if different model.
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by BDNiner on 2013-08-15
I also have a Y400. I haven't gotten ubuntu to boot from USB drive yet. I will order a hard drive and try installing it to its own drive.

---

### Post by MikeCyber on 2013-08-16
after install I couldn't boot but boot repair did the trick.

---

