---
title: "How does Grub Rescue work?"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2012-01-13
I wanted to make a backup of my OS so I used dd to copy the entire partition to another drive, when I tried to boot, it didn't boot because the UUID was different from what is in the /boot/grub/grub.cfg of the original drive. This makes sense to me, and I do understand that in order to fix it I could simply edit the grub.cfg from a liveCD or another OS and give it the proper UUID, however, I am making this post for educational purposes and not to troubleshoot a pending problem. 

I wish to know if it is possible to issue a command at the grub rescue prompt to manually boot into the OS, I imagine this should be possible, but perhaps not. Perhaps the grub rescue is for something else entirely. 

If anyone can enlighten me on this matter and what commands are possible at the grub rescue I would be most grateful, thanks!

---

### Post by Herman on 2012-01-14
[Rescue Mode (''grub rescue>'') Booting]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting")

---

### Post by mikewhatever on 2012-01-14
Check out the Grub2 howto: [https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)

As for UUID, you can change the UUID of the file system to want it was with 'sudo tune2ts -U _UUID_ /dev/sdXY'.

---

### Post by davethewave83 on 2012-01-14
Awesome, thanks for the resources guys.

---

