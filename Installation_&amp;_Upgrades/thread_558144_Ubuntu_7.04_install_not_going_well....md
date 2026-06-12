---
title: "Ubuntu 7.04 install not going well..."
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by Dorkmaster Flek on 2007-09-23
New linux convert here, trying to install the latest Ubuntu.  I'm able to boot the live CD just fine, and I can install Ubuntu.  I'm getting a blank screen with a blinking cursor in the top left when trying to boot from the HD however.  I'm running an E6600 and an 8800 GTS.  I've read about display problems with new installs and the 8000 series of video cards, and I've found the /boot/grub/menu.lst solution already.

I booted the Live CD, mounted my drive and opened the file, and added a vga=xxx flag to it.  My monitor is a Samsung SycnMaster 204B, native resolution is 1600x1200.  I found a table of valid VGA values in [this post]("http://ubuntuforums.org/showpost.php?p=2509903&postcount=13") and tried several.  I tried vga=792 since that's what was floating around, nothing.  I tried 0x31E since that was what my monitor is, I tried 0x317 since the Live CD always boots to 1024x768 for some reason.  No change at all when booting from the HD.  You can't even hit Ctrl+Alt+F1 to get a terminal, it just doesn't respond to anything except Ctrl+Alt+Del which reboots the machine.

I was running Windows XP on one HD and decided to get a second HD to install Ubuntu and migrate my files/settings.  I've disconnected the Windows drive now that it's installed, but could that have caused some kind of conflict when doing the initial install?  I made sure I selected the complete disk option and the new HD I just bought when going through the install wizard.

I don't know if having both HDs during the install did something weird.  I think it's probably due to my video card, but I've tried different VGA options in the menu.lst file with no luck.  What else am I missing here?  Thanks.

---

### Post by Pumalite on 2007-09-23
Your video. Gutsy will support that card in October. I'm writing to you from Gutsy Tribe 5. Cannot recommend it to anybody depending on their OS for a living. It's in testing. Stable comes out in October. Recognizes more, newer hardware. OTOH, you could try this:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by Dorkmaster Flek on 2007-09-23
Well on a whim, I decided to disconnect my Windows HD and reinstall Ubuntu with just the new HD I bought and no migrating data/settings from Windows.  I added the VGA flag again like before and this time it worked. :P  I don't know what the issue was with the other HD.  I'm going to try reconnecting it after dinner, but at least I'm up and running now.  Ready to sail the linux seas. :)

---

### Post by Pumalite on 2007-09-23
Glad you have it working!

---

