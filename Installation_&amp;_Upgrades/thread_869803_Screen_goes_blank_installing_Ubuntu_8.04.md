---
title: "Screen goes blank installing Ubuntu 8.04"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by BiscuitTin on 2008-07-25
Hi,

I'm trying to install Ubuntu 8.04 on my Sony VGX-TP1E media centre PC but I'm having difficulty with the display. I obtained the ISO from a recent PC Pro cover DVD and burned it to CD. I believe its the 32 bit version.

I initially tried to run Ubuntu from the CD (I was surprised that it fitted on one!) to get a feel for it. What happens is that once you get past the keymap and language bits, the system tries to load the GUI. At this point the screen just goes blank. I also tried the safe VGA option, but the problem persisted. Since on the TP1E there is a VGA and a HDMI video output (I'm forced to run the VGA one), I connected up the HDMI in case for some reason the display had switched to the other output, but the screen still remained blank.

Since prior to installing Ubuntu I need to repartition the drive, inclusding resizing the Vista partition, I had downloaded and burned to CD the Gparted ISO, which is also based on Ubuntu. Curiously, on boot up, exactly the same thing happened.

The problem does not occur when I boot from a Suse Linux 10.3 DVD, so I guess it might be a problem with the drivers included in the distribution.

Does anyone have any other ideas?

---

### Post by wpshooter on 2008-07-25
If you actually want to install to your hard drive, then try the ALTERNATE version instead of the Live CD.

---

### Post by BiscuitTin on 2008-07-25
> **wpshooter said:**
> If you actually want to install to your hard drive, then try the ALTERNATE version instead of the Live CD.

Didn't know there was one, but I've just been having a look in the download section of the Ubuntu website and it does indeed mention and alternate version CD.

Thanks, I will give this a go.

---

### Post by VPz on 2008-07-25
> **BiscuitTin said:**
> Hi,

I'm trying to install Ubuntu 8.04 on my Sony VGX-TP1E media centre PC but I'm having difficulty with the display. I obtained the ISO from a recent PC Pro cover DVD and burned it to CD. I believe its the 32 bit version.

I initially tried to run Ubuntu from the CD (I was surprised that it fitted on one!) to get a feel for it. What happens is that once you get past the keymap and language bits, the system tries to load the GUI. At this point the screen just goes blank. I also tried the safe VGA option, but the problem persisted. Since on the TP1E there is a VGA and a HDMI video output (I'm forced to run the VGA one), I connected up the HDMI in case for some reason the display had switched to the other output, but the screen still remained blank.

Since prior to installing Ubuntu I need to repartition the drive, inclusding resizing the Vista partition, I had downloaded and burned to CD the Gparted ISO, which is also based on Ubuntu. Curiously, on boot up, exactly the same thing happened.

The problem does not occur when I boot from a Suse Linux 10.3 DVD, so I guess it might be a problem with the drivers included in the distribution.

Does anyone have any other ideas?

Yes, I have had the same problem...when I turned my lan function off in my CMOS and tried to upload the OS from CD only, the screen turns blank when it starts to load the GUI. I then turned my lan function back on and reinstalled Ubuntu onto the computer and it loaded fine. I think it has something to do with some extra packages or something that it needs to update from the internet during the install process.:)

---

