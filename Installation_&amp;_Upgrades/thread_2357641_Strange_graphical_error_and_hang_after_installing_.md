---
title: "Strange graphical error and hang after installing nvidia drivers"
date: 2017-04-04
forum: Installation &amp; Upgrades
---

### Post by deanium on 2017-04-04
Hi,

It's been a while since I played around with Linux but opted to try sticking Ubuntu Gnome 16.10 on a spare hard drive on my desktop. It installs and boots fine, however once I install the nvidia display driver I get a strange graphical issue and a hang.
[IMG]http://i.imgur.com/ck4Xy5Q.jpg[/IMG]

Also at this time the system does nothing. I hear my gpu fan spin up then down. This repeats for as long as I leave it. CTRL+ALT+DEL still restarts the machine.

I have tried booting with "nosplash --verbose text" however I still get the same issue. I've also tried "nouveau.modeset=0"- all get me the same thing.

The rig:
MSI Z170M Mortar
Intel i7 6700
Corsair Vengeance LPX
Gigabyte GTX 980TI

As I've said the system ran fine post-install (and live) so this surely has to be an nvidia driver issue, but then I don't want to be running my rig without my gpu doing what it can do. Are there known compatibility issues with the nvidia drivers (375) on 16.10?

Any help would be greatly appreciated.

Cheers,
Dean

---

### Post by oldfred on 2017-04-04
Did  you install nVidia from Ubuntu repository or from ppa?

Can you boot with recovery mode, under advanced options in grub menu?

If you un-install one nVidia driver to install another be sure to totally purge first or you will get conflicts.

---

### Post by deanium on 2017-04-04
I tried this a few months back where I installed from the ubuntu software gui, however this time I installed from ppa (same issue both times). Recovery mode appears to hang at loading initial ramdisk. During this time numlock does not respond, however CTRL+ALT+DEL still reboots the machine. How long is considered normal for recovery mode to boot?

This is all based on a fresh install- so no conflicting nvidia drivers should be present.

---

### Post by oldfred on 2017-04-04
Should boot right away unless very old system.

Should not normally use CTRL+ALT+DEL but use REISUB: 
 Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/) 

Some older MSI motherboards needed fast boot off to work.

 MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
[http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot](http://askubuntu.com/questions/705796/msi-z170a-gaming-m5-with-linux-dual-boot)
MSI-Z97/Intel's Core i7 5775C Broadwell Is Running Well On Ubuntu 15.10 Iris Pro 6200
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1510-bdw&num=1)
MSI Z170
[http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095](http://askubuntu.com/questions/801841/dual-boot-ubuntulatest-and-windows-10-on-msi-h170m-pro-vdh-using-msi-click-bio/802095#802095)

---

### Post by deanium on 2017-04-04
Hmmm...

I've tried recovery mode on two different kernels that are listed, and both hang at ramdisk load.
The system isn't old by any stretch.
I have fast boot disabled (as I tend to do when trying to install / configure new OSes). It just doesn't make sense... I suppose I'm left with the option to reformat and reinstall Ubuntu and try a different nvidia driver. It was a fresh install so I wont be losing any data, just time.

Maybe it's just not meant to be.

---

### Post by oldfred on 2017-04-04
While I know you want nVidia driver.
Can you disconnect either in UEFI or physically and boot.

I have seem a few install using the Intel driver, install nVidia driver & reconnect nVidia card.

While a different motherboard, you may have similar settings since z170.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
Go to the BIOS, Peripherals > "Initial Display Output": set it to IGFX (basically, this tells your computer to use your motherboard to display graphics)
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648)

---

### Post by deanium on 2017-04-06
So I tried that- set primary display output to integrated graphics, was able to boot (albeit with some flickering). Purged nvidia driver, rebooted. Then installed latest nvidia, restarted and re-enabled the discrete graphics. Booted again and same as before- hangs with glitched out display.

That's 375 and 378 drivers causing this. I could repeat the steps to purge and install yet another nvidia driver but I'm not optimistic.

---

### Post by oldfred on 2017-04-06
A few  laptop users had better luck with 16.04. Not sure why?

---

### Post by deanium on 2017-04-06
Worth a shot- will give it a whirl. Thanks for your help.

---

### Post by deanium on 2017-04-07
Strangely enough I've installed 16.04 and all seems fine. Not sure why 16.10 had issues with my rig, but at least I'm running. Now to try to get sound working.

---

