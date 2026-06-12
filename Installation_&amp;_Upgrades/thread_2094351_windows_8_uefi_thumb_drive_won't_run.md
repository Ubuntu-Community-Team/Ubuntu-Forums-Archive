---
title: "windows 8 uefi thumb drive won't run"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by bergeo on 2012-12-13
I just bought a new HP computer with Windows 8.  I installed an ssd as a second drive, and I want to install Ubuntu onto the new drive so I can dual boot.

I created a bootable thumb drive with 64-bit Ubuntu 12.10.  I verified it works by using it to boot into Ubuntu on an old Windows XP box.

When I try to bootstrap from the thumb drive on my new Windows 8 box I get the grub menu okay, but when I select either 'run Ubuntu' or 'install Ubuntu', the screen turns black and then nothing happens.

Any suggestions?  I'm a novice at this stuff so please don't assume much knowledge on my part.

---

### Post by randommanaki on 2012-12-13
An obvious question, i'm sure, but did you make sure you are booting the USB drive in UEFI mode?

---

### Post by bergeo on 2012-12-13
Not obvious to me! :)

I assume though that it's booting in UEFI mode, based on how I got there.  I held down the shift key and selected 'restart' from Windows 8.  It then offered me a choice of devices to boot from.  The one I selected said "UEFI: KingstonDT 101 G2 100".  (The thumb drive is made by Kingston.)

---

### Post by bergeo on 2012-12-13
I got Ubuntu to come up.  I disabled secure boot as described here: [http://distrowatch.com/weekly.php?issue=20121126#qa](http://distrowatch.com/weekly.php?issue=20121126#qa)

Then when I rebooted and selected 'Try Ubuntu without installing', it came up instead of just hanging.  I next need to install it and see if I can dual boot, but at least I'm past the dead black screen now.

---

