---
title: "Beta 2 fails to boot after running update manager"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by busydoingnothing on 2010-04-16
I installed 10.04 beta 2 on a Gateway Centrino laptop without issue. I ran Update Manager to get all the latest updates. They installed successfully, then it rebooted. When the system boots, I see the Ubuntu screen with the 5 or 6 dots for a few seconds, then the screen goes black and the hard drive stops reading. The laptop is still on, but doesn't respond to any keystrokes (can't switch to alternate terminals) or CTRL+ALT+DEL. 

How can I diagnose this?

---

### Post by JoeWheeler on 2010-04-16
I've just updated my system and am also getting this

Edit: If anyone is struggling to get on then if you hold shift when booting it'll load grub I accidentally booted the old kernel AND started recovery mode > logged on > "sudo start gdm"

So one or both of those should et you back in

---

### Post by busydoingnothing on 2010-04-16
I tried a different boot option at the GRUB loader and was able to boot kernel 2.6.32-19-generic, and it seems to be working fine. Kernel 2.6.32-21-generic is failing to load.

---

### Post by cariboo on 2010-04-16
Remove quiet splash from the boot line in Grub2 to see where the process stops. or start in recovery mode to see if you can start the desktop from the prompt, hit resume, when you get to the menu.

---

### Post by busydoingnothing on 2010-04-16
> **cariboo907 said:**
> Remove quiet splash from the boot line in Grub2 to see where the process stops. or start in recovery mode to see if you can start the desktop from the prompt, hit resume, when you get to the menu.

I tried what you suggested. The last thing I can see before my screen goes black is the "Checking Battery State" message.

---

### Post by mrcsft on 2010-04-16
The same for me, can't boot using 2.6.32-21. I can boot successfully my laptop (Dell Latitude D505) using previous kernel version (2.6.32-20 is ok).

One note: whatever kernel version I use, I have to set the output video to X Window without Xv (running gstreamer-properties from command line) otherwise (using default output) xorg crashes. My system is based on an Intel 855GM

---

