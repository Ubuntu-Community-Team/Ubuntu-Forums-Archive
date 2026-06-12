---
title: "Had a problem booting up Karmic after install. Help??"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by JohneG on 2009-11-25
I have a few computers running Jaunty with no problems. I recently installed Karmic onto one of my machines to check it out. The live disc worked no problems so i didn't forsee any problems. The install seemed to go perfectly. Then when i went to boot up it wouldn't boot up. I can't remember the message i got as i have reinstalled Jaunty back on it since. 

I am only just after reading about Upstart. I am wondering is this why it wouldn't boot up? From what i remember it was a grub message. Wasn't very long and didn't really tell me much, which is why i don't really remember what it said. My computer is a few years old, Pentium 4 @ 2 Ghz, 1 GB Ram, etc. Could it be that the Upstart is what caused it not to boot up? Has anyone else had problems with this and has it been resolved as i would love to try out Karmic properly

---

### Post by oldfred on 2009-11-25
If it is not a grub2 error and is the only operating system on your computer it will bypass the menu and go straight to booting Ubuntu. Hold down the shift key to get the menu and use the recovery mode to boot. Recovery mode is without quiet & splash so it should show each step of the boot process and what device may be causing a problem.

---

