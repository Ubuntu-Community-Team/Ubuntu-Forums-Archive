---
title: "Ubuntu/XP dual-boot problem -- not booting"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by ProfesseurPotato on 2007-09-22
Greetings

Kind of a newbie here. Take it easy on me. ;)

Until about two hours ago, Ubuntu 7.04 and XP co-existed on my Dell Inspiron 6000. Now, I have nothing but a black screen with a flashing cursor.

1. Ubuntu/XP running fine. Time for regular XP clean-up/re-install anyways;
2. Format the primary partition with XP installed and re-install XP. Ubuntu happily running on its own little partition;
3. XP installs, reboot is attempted and nothing but a black screen appears after the dell/system start up screen;
4. No Ubuntu boot option. No XP boot option. Just blackness;
5. F2 (Setup) nor F10 (Boot menu) options also lead to the black screen of death.

Before this happened, grub was responsible for booting Ubuntu as the primary option. Pretty sure it's a boot menu problem; yet I just don't know how to fix it.

Any help would be greatly appreciated. 

Cheers,

W.

---

### Post by Pumalite on 2007-09-22
You have garbage in your drive. Use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then use Gparted;[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Make one large partition of your drive formatted ntfs. Install XP. Defrag several times. Boot from Gparted again, right click on XP partition; in menu choose 'resize partition', format to ext3 if you want. Then install Ubuntu; install grub to MBR(by default). Reboot. You will now have menu to boot either OS.

---

