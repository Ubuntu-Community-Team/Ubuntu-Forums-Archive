---
title: "Problem booting after upgrading to Ubuntu 11.04 and updating packages"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by crimius on 2011-07-11
Booted my laptop up for the first time in a while and ran
```
sudo apt-get upgrade
```
to get updates for my packages.  After installing I needed a reboot since I was on kernel 2.6.35-28.  Post-reboot, I get stuck on a black screen with random artifacts after the purple screen after Grub, regardless of kernel (back to 2.6.35-22 is the oldest I have) with exception to the recovery mode options.  Pressing the power button will shutdown the system in what seems to be the usual manner.  The screen changes to the purple with ubuntu in the middle and the dot loading bar and shuts down.

I booted into recovery mode and opted to repair packages and rebooted but to no avail.  I can get into a terminal by editing the boot options in Grub swapping out " quiet splash vt.handoff=7 " with "--verbose".  Currently have a terminal on kernel 2.6.38-10 Ubuntu 11.04 32-bit.  Win 7 partition also boots fine.

This feels like a driver issue, but I'm not sure.  Boot log (/var/log/boot.log) looks fine except for these lines:

```
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2 /dev/sda3: clean, 262541/8560640 files, 2310841/36228480 blocks
init: ureadahead-other main process (723) terminated with status 4
```

The first 2 shouldn't be affecting my Ubuntu boot in this manner (other than failing to automatically mount my NTFS partition, which is a different problem), however the last one worries me.  Doing some research on the termination status 4 of ureadahead-other I came across this page [here]("http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04"), but am wary to just go around willy-nilly deleting things I don't know much about.  It wouldn't be a great loss to simply blow the disk away and restart, but I'd rather salvage what's there if I can.  Any help is appreciated.

---

### Post by Quackers on 2011-07-11
It could be a graphics problem. Try a boot option like nomodeset or similar.

---

### Post by crimius on 2011-07-12
booting with nomodeset doesn't help, get the same behaviour. I'm going through some other logs to see if maybe something went wrong while updating that's causing this.

---

### Post by crimius on 2011-07-12
checking in Xorg.n.log I see the following lines
```
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(II) Unloading nvidia
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available

Fatal server error:
no screens found
```
These seem to be problems (fatal ones at that).  Just taking a guess, I probably need to grab some nvidia drivers.  Thanks Quackers!

---

### Post by crimius on 2011-07-12
after installing nvidia-current and running nvidia-xconfig I was 1 step closer, got past the blank purple screen and got the purple logo loading screen, but hung there.  Checked through logs again and was still getting the same nvidia errors in my xorg logs.  Thought that was wierd, so checked into the different xorg.confs in /etc/X11/ and then tried booting with failsafe X.  Got some errors that flashed too quickly and checked the failsafe log, which showed issues with xinit.  I had already repaired packages so that was very strange.

I tried removing xorg, but there was no such package installed. -.-
reinstalled xorg and a regular boot went through perfectly.  Thanks!

---

