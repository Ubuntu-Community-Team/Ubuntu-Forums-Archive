---
title: "Windows won't boot on a dual boot setup"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by ataraxis84 on 2007-05-20
As far as im aware, when installed ubuntu (onto a seperate drive) it installed grub onto that drive and left the MBR alone for the windows drive. Using the bios to set boot priority to the Grub/ubuntu drive, i can choose windows media center/ubuntu etc, and after the initial install, it worked booting into windows. Now a couple of days later, I can only get into windows through safe mode, even if i set the boot priority back to the windows drive, when trying to boot into windows directly , i see the loading screen, then all goes blank and never returns?

Anyone got any ideas as to why this happened, or how to fix it.... ?

---

### Post by vedace on 2007-05-20
That sounds pretty crappy.  What happens if you boot into the Windows recovery console and run fixmbr and fixboot on your windows drive?  If grub never touched your windows drive, this shouldn't make any difference, but try it anyway.  I'm further inclined to think that this won't accomplish anything because Windows' bootloader technically kicks in, since you see the Windows boot screen, even if the process doesn't go to completion.  

I think your best bet is to google around for some combination of the words "windows" "loading" "screen" "goes blank" "black" "nothing happens" "loads", etc., without any mention of grub or ubuntu, because this problem could just be an instance of Windows being an idiot without any provocation from ubuntu, grub, or anything else.  Here's a Google search with several promising hits: [link]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=mGT&q=windows+loading+screen+blank&btnG=Search").

---

### Post by Ambimom on 2007-05-20
Try this.

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

---

