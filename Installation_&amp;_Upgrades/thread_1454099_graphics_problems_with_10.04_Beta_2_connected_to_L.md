---
title: "graphics problems with 10.04 Beta 2 connected to LG HDTV"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by jejones3141 on 2010-04-14
I have a computer that I want to connect to my LG HDTV. I installed 10.04 Beta 1 and connected it via HDMI. Graphics was OK. modulo overscan issues. nvidia-settings took care of that for the login session, though the gdm screen was still prey to it. However, I couldn't get audio to work over the HDMI connection, so I fell back to VGA and analog audio.

Updates were available, so I installed them and rebooted...and found that the TV refused to display the screen; a wandering window showing, I think, "Invalid Input" appeared instead, reminiscent of the old days when a monitor was being handed a scan rate it couldn't handle.

I decided to start over, and made a partition on a flash drive with a bootable partition with the Beta 2 Live CD on it. Same thing happened, but I was able to boot up and see the display with the vga= option suggested on one of the help screens. That let me install... but now when it boots, I get the "invalid input" again after the splash screen. I will have to look up the character one should type to catch grub and let one change the boot options; I thought it was ESC or F1, but either it's not or I'm not quick enough on the draw--but even if I do that, I fear that once I install the proprietary driver I'll be back to the "invalid input" again. Has anyone else seen this?

---

