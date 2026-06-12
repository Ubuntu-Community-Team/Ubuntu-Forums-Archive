---
title: "Wubi problem"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by IanBraby on 2010-11-25
I have Wubi and Ubuntu 10.04 installed on both my desktop and laptop and it's great - I'm almost sold!

Today, on my desktop, update manager reported and installed 37 updates and requested a reboot. After the reboot, I tried to select Ubuntu but was greeted with:
error: unknown command 'loadfont'
error: file not found
... and the computer restarted again (and again and again).

I can't even get to the normal Ubuntu boot menu and select recovery mode so can anyone tell me what has gone wrong and how to fix it without a fresh install which will lose all my printer and scanner settings? Alternatively, which files could I copy from my laptop to get me back into the desktop file?

Hoping for help...

Ian

---

### Post by bcbc on 2010-11-25
What has gone wrong is grub... 
see this link for a proposed workaround: [http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

After editing the grub.cfg as suggested it should boot again after which you should run "sudo update-grub". 

Please report back on what works as this helps others in the same situation.

PS the same thing happened in July/August with 10.04.1 grub updates and that worked to resolve it.

---

