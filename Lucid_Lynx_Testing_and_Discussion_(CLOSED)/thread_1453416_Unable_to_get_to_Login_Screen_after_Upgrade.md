---
title: "Unable to get to Login Screen after Upgrade"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pjaikins on 2010-04-13
I was on 9.10 and performed an update to 10.04. The upgrade proceeded fine and then restarted X to present the new environment. There was some problem with the display showing a sort of split screen (I have Nvidia), but I issued the nvidia-xconfig command as requested. I then rebooted and selected the kernel in grub (2.6.31-20) but it is reporting that it cannot mount mountall: mount /dev/.static/dev [989] terminated with status 32 then a bunch of Network Unreachable errors when mounting my NAS drive volumes. It then just sits at the splash screen for ever. Any help please?

[update]
Just saw on console 1 an error xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
xc2028 2-0061: Error on line 1135: -6

---

