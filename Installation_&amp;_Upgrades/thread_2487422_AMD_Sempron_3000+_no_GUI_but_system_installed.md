---
title: "AMD Sempron 3000+ no GUI but system installed"
date: 2023-06-04
forum: Installation &amp; Upgrades
---

### Post by roger_moore on 2023-06-04
Hey

I need some help from the experts. I've got an AMD Sempron 3000+ build. I don't like to waste tech and so I'm trying to use it as a samba server. I help people fix their PC's for free so I needed a place to store software as well as do temporary backups while repairing the PC's. The bios is a bit ancient and a pain however, I've figured out some of the quirks. The processor is 64 bit and works with most distros LiveCD. Ram is 2GB and has 2x500GB sata drives attached.

One issue I have is that the latest 22.04 installs on the PC but locks up the bios upon reboot. I've dumped into Gparted to see the partitions and there's a UEFI partition and the partitions are flagged as "boot esp" and "bios grub" if I remember correctly. Also Grub2 is installed so I don't know which one the bios doesn't like. Anyway, a work around I've found is if I install 20.04 and do do-release-upgrade the PC upgrades itself to 22.04. 

The problem with this arises when the PC reboots it goes to a screen with just a blinking cursor. So I switch to console and login and it tells me the PC has successfully upgraded to 22.04 even though it's not displaying a desktop GUI. 

My suspicion is that it's either XFCE or the driver for the GPU is not correct. Please note that I've tried it with XFCE Mint as well and the result is the same.

A (potato) picture of the Xrandr -q and lspci output. I don't have direct console in just a screen. Previous 20.04 GPU driver worked fine so I don't know what changed.

Please help. This is where I am stuck.

---

### Post by QIII on 2023-06-04
Please use the default font and color in your posts.

---

### Post by roger_moore on 2023-06-04
> **QIII said:**
> Please use the default font and color in your posts.

Thanks for the edit.

---

### Post by Bashing-om on 2023-06-04
Hey roger_moore -

Oh Boy Sis graphics - The vendor is rather short in offering us a lot of support. Depending on the card there is "some".

Please see:
[https://easylinuxtipsproject.blogspot.com/p/sis.html](https://easylinuxtipsproject.blogspot.com/p/sis.html)
[http://ubuntuforums.org/showthread.php?t=2252413&page=2&p=13198482#post13198482](http://ubuntuforums.org/showthread.php?t=2252413&page=2&p=13198482#post13198482) post #15
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)
[http://ubuntuforums.org/showthread.php?t=2144455](http://ubuntuforums.org/showthread.php?t=2144455)

-Good Luck-

---

### Post by roger_moore on 2023-06-06
> **Bashing-om said:**
> Hey roger_moore -

Oh Boy Sis graphics - The vendor is rather short in offering us a lot of support. Depending on the card there is "some".

Please see:
[https://easylinuxtipsproject.blogspot.com/p/sis.html](https://easylinuxtipsproject.blogspot.com/p/sis.html)
[http://ubuntuforums.org/showthread.php?t=2252413&page=2&p=13198482#post13198482](http://ubuntuforums.org/showthread.php?t=2252413&page=2&p=13198482#post13198482) post #15
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)
[http://ubuntuforums.org/showthread.php?t=2144455](http://ubuntuforums.org/showthread.php?t=2144455)

-Good Luck-

Thank you for pointing me in the right direction. My system said that I already had the latest vesa driver so I ended up using the thread below:

[https://ubuntuforums.org/showthread.php?t=1311537](https://ubuntuforums.org/showthread.php?t=1311537) 

I had miss read it on my phone and only saw the code below. I had created a new /etc/X11/xorg.conf file as there wasn't one and pasted just that in and everything works now.

```

Section "Device"        
            Identifier      "Configured Device"
            Driver  "vesa"
EndSection

```

However, I have since discovered a mouse and keyboard problem. It appears after some delay. The mouse can move around on the screen but can't select anything and my keyboard can't type anything except if you jump to console and then back to GUI. In this case xfce4-screensaver was the problem (removed completely) and I've since replaced it with xscreensaver.

---

### Post by Bashing-om on 2023-06-06
roger_moore; :D

Outstanding that you have resolution - glad that I was of some benefit.

[INDENT]where there's a will there's a 'buntu[/INDENT]

---

