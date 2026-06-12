---
title: "Reinstalling Windows XP after setting up Ubuntu: What to do?"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Kamakazie! on 2007-05-28
Heya all, i've been using Ubuntu for a few months now and am really liking it. I've got a dual boot setup because i play game regularly.

My XP partition could really do with a format because i migrated after 6 months of using XP solely and so it has a lot of rubbish lying around from old programs.

I want to format the partition and reinstall XP but i understand that installing XP after installing Ubuntu can cause problems with GRUB. How can i make sure that my boot sequence in GRUB is maintained and not overwritten by the new XP installation?

Thanks

---

### Post by NooBeee on 2007-05-28
Grub will almost certainly be erased.
You can simply *reinstall* grub after installing windows. see [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
(Just don't format the Ubuntu partition!)

(personally, I used this method:
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit". 

8. Restart the system. Remove the bootable CD. )

---

### Post by Kamakazie! on 2007-05-28
Fantastic thanks for that.

---

