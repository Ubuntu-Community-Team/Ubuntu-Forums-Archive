---
title: "One or more packages failed to install"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by will3 on 2005-07-23
I'm on my fourth attempt to install Ubuntu and I'm about to give up. I received a few Ubuntu 5.04 CDs in the mail and have tried installing from different CDs. The machine should be fine since I've run both RH Fedora and Mandrake Linux on it. The installation goes through about 20 - 30 minutes unpacking and installing and then gets a bunch of dependency problems. I end up on a Ubuntu Configuration screen that says "There was a problem install the selected software. One or more packages failed to install". It seems there were problems installing several packages and now I have broken installation without xwindows or perl. I'm now wading through errors messages like "Processing was halted because there were too many errors." I found Fedora and Mandriva installs were much smoother.  I had no problem running from the live CD on this machine. Any suggestions where to begin?

---

### Post by Xian on 2005-07-23
Is there any chance that you did not have the installer format the mountpoint(s) of the Ubuntu partitions? Perhaps the best suggestion would be to select the manual partition option in the install process and do that step yourself. I'm only mentioning this since it would seem that if apt is having dep issues there might be some legacy pkgs laying around.

---

### Post by will3 on 2005-07-23
I've tried with and without formatting my two disks and end up with the same results. Thanks for trying to help.

---

### Post by Vietman on 2006-02-26
I've tried many times to get Ubuntu working properly on my system. I just updated the BIOS, which solved the problem with Ubuntu's GRUB not booting my installation. The problem is, it just doesn't finish the install. I downloaded the final release of the breezy DVD and it boots up into the livecd (although mozilla firefox doesn't load, even after manually configuring a static ip). But the installer craps out on this:

"One or more packages failed to install" on the base configuration. It stopped on a package called gstreamer0.8-jpeg.

I am really underwhelmed by the progress Ubuntu has made in the desktop linux scene...or the desktop linux scene for that matter. They should have better error-correction to prevent countless cds from becoming useless coasters that don't even install the OS you want to try out.

But maybe it's just a big issue downloading DVDs on multi-threaded downloaders.

Anyways, trying Breezy this time...gonna check that MD5 Hash before I burn.

---

### Post by Vietman on 2006-02-26
Hallelujah! I got a working installation of Ubuntu going - finally.

In retrospect, the things that did it for me were:

1. Update motherboard bios (needed extensive searching as it is an old mobo)

2. Give up trying to install Dapper and just get the regular Breezy

3. Download the install DVD via bittorrent instead of a download manager (seems they have poor error-correction using multi-threads)

4. Burn the install DVD at only 2 speed

5. Edit etc/fstab to allow mounting of my windows partitions

6. Install automatix software bundle (a script)

7. Edit some of the menu entries to have permissions for read by user to allow the menu editor to start

8. Change default font size (in browsers and desktop) and resolution

I also installed the Alacarte Menu Editor and am looking for a replacement for Beagle. 

I am almost there to having a 100% usable system. :)

---

