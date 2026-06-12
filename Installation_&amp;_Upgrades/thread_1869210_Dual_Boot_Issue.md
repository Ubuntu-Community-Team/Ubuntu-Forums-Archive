---
title: "Dual Boot Issue"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by moe19790 on 2011-10-25
Hi,

i`m facing a very strange issue, i`ve  installed "clean installation" windows 7 ad then after ubuntu 11.10. Every thing went smooth. the at starting menu i do have Ubuntu & win7 to select from. When i choose win7, the screen go blank "like restarting the gurp or something" and take be back again to the selecting menu, when i choose ubuntu it works fine, but never load win7 and no error msg.

thanks

---

### Post by drs305 on 2011-10-25
It sounds very much like you may have installed Grub to the Windows partition.

You have several options:

1. You can view the following link, which describes how to correct the problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

2. You can download and run the boot info script and post the contents of the RESULTS.txt file it generates. It shows the boot status of your system and help us troubleshoot. You can get to the script download page by clicking the "BIS" link in my signature line.

3. Or you can install the Boot Repair app. It may be able to help with this specific issue (I'm not sure if it can modify Windows installs) but at minimum it incorporates the Boot Info Script, which you can run from inside the app.
[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by satanselbow on 2011-10-25
If you have a "100MB" ntfs partition (marked as "system reserved" in gparted and typically sda1) and then your main windows partition you might find that grub is pointed at the 100MB partition and grub needs manual editing to point it at the main windows partition (sda2).

Grub 2 auto OS finder thingy gets caught out sometimes :(

---

### Post by Mark Phelps on 2011-10-25
If GRUB is pointing to the 100MB partition, then you have the problem that drs305 mentioned and you will have to do the repairs as well. You certainly do not want GRUB pointing at your Windows partition; you want it pointing at the appropriate Linux filesystem partition.

If you're getting a blank screen when selecting Win7, then it's likely, that if you used the Ubuntu installer to shrink the Win7 OS to install Ubuntu side-by-side, that it left the Win7 OS partition in an unusual state, and it won't boot now.

If that happened to you, you will have to repair the Win7 boot loader to get it working again. The step #3 in drs305 post might be able to fix that.

---

### Post by moe19790 on 2011-10-26
Thanks all for the help. Well i used the first option as suggested by DRS305. it seems the step deleted the boot loader and recovered the one used by windows "now only the system log directly to windows without waiting for selecting".

So, next step was to use the EasyBCD. to Manage "and install the boot loader". Things working gr8 now. thank you all.

Regards,

MOe!

---

