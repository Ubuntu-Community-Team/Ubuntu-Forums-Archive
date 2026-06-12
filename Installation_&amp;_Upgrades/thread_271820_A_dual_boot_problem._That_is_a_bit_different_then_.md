---
title: "A dual boot problem. That is a bit different then usual"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by asimons999 on 2006-10-05
Hello. Sorry if this has been resoloved somewhere.. but i have searched around and couldnt really find what i wanted..

ok here is the order of events.

1. Windows is only OS.
2. Installed ubuntu.
   ~spent a long time getting dual monitors and beryl running
3. everything going fairly well fine.
4. Formated and reinstalled windows.
windows has taken control of the boot setup.. so im assuming the boot program that deals with it has been replaced..

15 gig is missing so linux is still their somewhere.

All the solutions have been like.. windows and then installed linux..

well cause i reinstalled windows.. its replaced the boot config.. and i cant even choose linux.. it just goes strait into windows..

a little help? ive looked around.. i need to modify the boot.ini in windows i think.. but dont know what file needs to be on my c drive? and what line to add.. because i dont have access to linux to get some file i think windows may need.. to edit the boot.ini and have it working properly..

reinstalling ubuntu may work.. but i really dont want to do that since my mate spent a long time getting everything working with dual monitors and beryl.. because i am really new to linux..

so if you can help.. that would be great!

---

### Post by Kateikyoushi on 2006-10-05
You can restore grub which is a better solution than editing the boot ini.

[Restore grub after windows installation.]("http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation")

---

### Post by confused57 on 2006-10-05
You can also install grub using the live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by asimons999 on 2006-10-05
Thankyou.. that fixed it.. but i have some new problems.. fresh this morning..

[http://www.ubuntuforums.org/showthread.php?p=1585899#post1585899](http://www.ubuntuforums.org/showthread.php?p=1585899#post1585899)

---

