---
title: "Grub Re-configuration"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2006-10-28
Is it possible to reconfigure/reinstall grub from inside Ubuntu?  In FC5 in Gnome there was just an option to customize the bootloader, and when you were done editing it the bootloader would be re-installed with the new settings.  Is there a way to do this inside Ubunu?

---

### Post by Aerandir on 2006-10-28
AFAIK, the only way to customize GRUB in Ubuntu is to manually edit the menu.lst file with a text editor:  ```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Herman on 2006-10-28
marcusdean.adams,
Yes, but you don't need to re-install Grub, the settings will take effect right away without any special effort.
To see more about what Aerandir is referring to, click on my Grub Page in my sig link (underneath this post). You can dop a few extra things with Grub when you do it the old fashioned way. :D

If you don't like editing Grub manually, here's a link to Tomosaur's script, for editing Grub the easy way.  [SCRIPT: GrubED - GUI Grub editing]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grub")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grub") [2]("http://www.ubuntuforums.org/showthread.php?t=228104&page=2&highlight=grub") [3]("http://www.ubuntuforums.org/showthread.php?t=228104&page=3&highlight=grub") ... [Last Page]("http://www.ubuntuforums.org/showthread.php?t=228104&page=10&highlight=grub")) Tomosaur's script is very popular.

Regards, Herman :D

---

