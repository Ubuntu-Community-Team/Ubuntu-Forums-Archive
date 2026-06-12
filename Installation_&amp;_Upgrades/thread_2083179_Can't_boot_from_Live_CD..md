---
title: "Can't boot from Live CD."
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by naruki on 2012-11-11
I can't boot from Live CD at all (running dual boot Windows 7/Ubuntu). Not even after setting the boot priorities on my BIOS.

What happened was I messed up my previous 12.04 64-bit installation (I think I accidentally purge Unity 2D or something). After that, whenever I tried boot from the Live CD to do a clean install, the Live CD doesn't boot, no matter the boot priorities in the BIOS. It just goes straight to GRUB. So fine, I repaired Windows MBR and completely reformat the partition Ubuntu is in. So now Windows works fine and there's an empty partition in my harddisk to reinstall Ubuntu.

But Live CD still won't boot. It just keeps skipping right to the Windows 7 startup animation. Any help?

---

### Post by naruki on 2012-11-11
Solved. My BIOS is just acting weird. There were 2 different options to set boot priorities and I don't know what happened but even when I set Live CD (booted from USB) to be the first priority, it is still set as second priority under which drive to boot from first.

Anyways, got a question. How do I remove "previous versions" from GRUB? Also two memory test options showed up on GRUB, haven't seen that before. Previously I installed 12.04 64-bit. Now I just installed the 32-bit version.

---

### Post by offgridguy on 2012-11-11
Since you have marked this as solved i recommend starting a new thread with
the questions you are asking here. :)

---

