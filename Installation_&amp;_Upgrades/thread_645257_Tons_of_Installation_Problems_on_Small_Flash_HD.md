---
title: "Tons of Installation Problems on Small Flash HD"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by manekineko2 on 2007-12-19
I'm trying to install Linux for the first time, onto my laptop as a dual boot with Vista, which came preloaded on it.

My Vista install is on my true hard drive, and works perfectly.  I got a 2GB CompactFlash card that I inserted into my laptop's second drive bay using a CF -> SATA adapter.  Detected and works fine in Vista as a removable drive.  I switched the CF drive into the primary bay, with the intention of using GRUB in order to be able to choose to boot Ubuntu loaded on the CF drive in bay 1, or Vista on the true hard drive in bay 2.

I first got 7.10 standard, and booted it.  When installing I chose to use the entire disk option on the CF drive, noting that the Ubiquity installer stated that it needed 2GB.  Perfect I thought, but it failed without a graceful exit.  The only error was a pop-up balloon stating the drive was full.  This bug is documented here:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/88208]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/88208")

I then did an install with a manual partition install using 7.10, choosing to use no swap file so that I could have the entire 2GB for the OS.  This too failed, which I found inexplicable given that the installer stated it needs 2GB and I had a 2GB CF card.  A similar bug on Feisty is documented here, but the solution doesn't work for me on 7.10:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/112516]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/112516")

On previous versions it was reported you can type the following in order to get it to install on smaller drives so it doesn't copy a cache onto the install drive while installing:
linux archive-copier/copy=false
I can't figure out where to put this in 7.10.

On the advice of a friend, I downloaded 7.10 server.  I installed both with and without network connection (in order to prevent downloads filling up the drive), both with and without manually partitioning and choosing entire disk.  The result is the same however, it states that install is complete but when I reboot I am getting this error on startup:
"Grub Loading stage 1.5Read error"

In order to rule out possible problems, I then installed GRUB onto a normal USB key.   My company boots up fine on the USB key, and I can load Vista in bay 2 perfectly fine with that.

I'm really befuddled, can anyone help?

---

### Post by manekineko2 on 2007-12-20
After all the hours I've put into this, I really can't get it working, can anyone help?  Any ideas on what I can try next?

---

### Post by manekineko2 on 2007-12-24
Anything at all?  Please?

---

### Post by manekineko2 on 2007-12-24
Would it be possible for me to install Ubuntu by manually installing GRUB and then simply copying all the relevant files into place using the copy command?

---

