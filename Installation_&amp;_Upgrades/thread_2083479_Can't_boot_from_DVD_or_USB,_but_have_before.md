---
title: "Can't boot from DVD or USB, but have before"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by catquarks on 2012-11-12
Hello there! I've been scouring the internet, and cannot figure out what's wrong. Basically, I screwed up something after upgrading to 12.10, and just want to do a clean install of Ubuntu Studio 12.04. I have booted from USB and DVD with this computer before, but it will not do it this time. I tried re-downloading the .iso file, and also using a different start-up disk just to see if it would work, but something is preventing it from happening.

I tried using F2 to change the boot order, and Esc to pick the device -- but the computer just doesn't actually boot from USB or disk.

The machine is a Sony VAIO.

Any other information you need about the computer? All help is appreciated, thanks!

More information: The USB image was created with the start-up disk creator on my Lubuntu netbook, and the DVD image was created using Windows 7 (which I only have access to at work). The computer in question does not always recognize DVDs/CDs in general, which is why I tried booting from USB first.

---

### Post by Mr_JMM on 2012-11-12
If the BIOS is set to boot from DVD drive but you're still not having any luck then we'll start with the obvious:

Have you confirmed the md5sum of the downloaded ISO and the DVD once burnt?

---

### Post by catquarks on 2012-11-12
Thanks for the response! I'm checking the md5sum for the .iso used for the USB drive right now... Okay it looks fine:

0dd6797c00bbae4fcb6382ac5f007305
ubuntustudio-12.04.1-dvd-i386.iso

Otherwise, I tested the USB drive with my netbook, and that machine booted from the USB drive immediately.

---

### Post by catquarks on 2012-11-12
I used the script on this page ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to check the USB drive, and this was the output:

hashusb.sh: 21: hashusb.sh: md5deep: not found
checksum for input image:
hashusb.sh: 25: hashusb.sh: md5deep: not found
checksum for output disk:
verification successful!

So... should I reinstall the USB drive, despite that it worked on my netbook?

---

### Post by catquarks on 2012-11-12
I used the script on this page ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to check the USB drive, and this was the output:

hashusb.sh: 21: hashusb.sh: md5deep: not found
checksum for input image:
hashusb.sh: 25: hashusb.sh: md5deep: not found
checksum for output disk:
verification successful!

So... should I re-burn the USB drive, despite that it worked on my netbook?

EDIT: sorry for the duplicate message; can't figure out how to delete it. Anyway, I'm re-burning the USB drive. But I think the problem's gotta be in the BIOS, since it worked fine on the other computer. I've just looked there so many times and am stumped.

---

### Post by catquarks on 2012-11-12
Update: after selecting my drive in the boot menu, I occasionally get sent to the GRUB menu. Is there anything here that I can do, or is none of it relevant once I've gotten past the BIOS screen?

---

### Post by catquarks on 2012-11-13
For anyone who might still be paying attention to this thread: After digging around, I found a live CD of Puppy Linux and, on a whim, tried to boot from it. It worked! Reflecting that I had already backed up all my files, I wiped the entire disk (as per [http://www.murga-linux.com/puppy/viewtopic.php?t=65509](http://www.murga-linux.com/puppy/viewtopic.php?t=65509)) and tried to boot from USB and DVD again...

I have tried 3 different USB drives, one SD card, and one DVD. It just says "Operating System not found," while the DVD drive briefly hums and then stops, or the USB drive either goes unacknowledged or briefly blinks before stopping. I'm totally stumped.

Anyone have a thought or opinion on this?

---

### Post by catquarks on 2012-11-13
Hoho!! I figured it out. For anyone who's interested in how this problem was solved: I dug around old forums, looking for other people who wiped their hard drives and were unable to boot from disc or USB, and, among other suggestions, one person was instructed to reformat his drive's partitions. I found another post somewhere saying that drives with unstable partitions sometimes have trouble booting off of external media.

So I used GParted in Puppy Linux to create a new partition table, then rebooted with the DVD, and it worked! I suspect that I've had unstable partitions for a while. Anyway, while I'm bummed that I spent 60+ hours beating a dead horse over this, it was a necessary learning experience.

---

### Post by mof920 on 2012-11-16
> **catquarks said:**
> Hoho!! I figured it out. For anyone who's interested in how this problem was solved: I dug around old forums, looking for other people who wiped their hard drives and were unable to boot from disc or USB, and, among other suggestions, one person was instructed to reformat his drive's partitions. I found another post somewhere saying that drives with unstable partitions sometimes have trouble booting off of external media.

So I used GParted in Puppy Linux to create a new partition table, then rebooted with the DVD, and it worked! I suspect that I've had unstable partitions for a while. Anyway, while I'm bummed that I spent 60+ hours beating a dead horse over this, it was a necessary learning experience.

I'm also on a VAIO. I'm having a lot of problem with the same issues. I'll try your solution and see where I get to from there. It's a new hard drive, but idiot me didn't format the hard drive.

---

