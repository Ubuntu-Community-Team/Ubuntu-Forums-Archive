---
title: "No full screen for VirtualBox, guest additions fail"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2010-07-11
So, I'm trying to test 10.04 Lucid 32-bit within 9.10 using VirtualBox.  Guest additions aren't working fully--I can copy and paste text, but my mouse pointer still gets captured.  No indications of any problems during installation.  Also, I get the "Ubuntu is running in low-graphics mode" error message starting up, indicating Ubuntu can't detect the hardware properly.  Screen size is stuck at 800x600.

I've tried reinstalling Guest Additions, increasing Video Ram to 128MB, and putting screen resolution and vbox device data into xorg.conf.  Nothing changes.  Actually, there is no xorg.conf on the system, only an xorg.conf.failsafe.  I modified that, no effect--though the file gets overwritten on boot up to be what it was originally.  I also tried adding my own xorg.conf.  That doesn't get overwritten, but also has no effect.

Anyone have any thoughts?

---

### Post by RamiroS on 2010-07-12
I installed Guest Additions and it worked... however after some updates it returned to a fixed smaller resolution. Here is how I fixed it:

Stop the virtual machine, go to Settings and Uncheck the Full Screen / Seamless mode.

Turn on your virtual machine and you should see the full version of the "Machine" menu. Check Auto Resize Guest Display... that will do the trick.

---

