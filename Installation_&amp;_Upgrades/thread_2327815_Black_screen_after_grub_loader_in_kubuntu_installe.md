---
title: "Black screen after grub loader in kubuntu installer"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by Patrick_Jeeves on 2016-06-14
As in the title. I had ubuntu installed on this machine before and did not run into any trouble, but having windows 10 installed in between seems to have caused the trouble. The screen is black as in black is being displayed, rather than no signal coming through the cable, given that the light on the monitor didn't turn orange. So far I've tried flashing the bios to the latest version and reseting the CMOS, both by bridging the pins and by removing the battery, but nothing.

Also setting 'splash quiet' to 'nomodeset' doesn't seem to help either.  And there is no secure boot option in the bios settings. ( Gigabyte F2A55M-HD2 Rev. 1)

I can successfully boot the rescue CD software from the same USB stick, so I don't think it's the GRUB loader...

---

### Post by Patrick_Jeeves on 2016-06-14
I rewrote the USB stick as a DD drive, instead of an ISO, and it worked. But I don't know what DD means.

---

### Post by yancek on 2016-06-14
Some info on the 'dd' command.  If you want to know what it does, just google it.  Thousands of sites with detailed explanations.

 [http://unix.stackexchange.com/questions/6804/what-does-dd-stand-for](http://unix.stackexchange.com/questions/6804/what-does-dd-stand-for)

---

