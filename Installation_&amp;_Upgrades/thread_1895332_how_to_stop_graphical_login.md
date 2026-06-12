---
title: "how to stop graphical login"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by littleknowledge on 2011-12-14
Good day to you,  I recently installed ubuntu 10.04 to a dell gx260. It installed properly and on first login i went to update manager to download all updates. Now the computer boots properly all the way to the ubuntu (gnome) login screen and hangs (nothing responds, not even ctrl+alt+Fx keys) when showing the possible users to login with. 

Gx260 has an intel graphics card and I know they have given trouble in the past... so I figure the problem is related to the graphics part of the bootup. 

i would like to know if anyone knows how to stop the ubuntu boot process from going straight into graphical mode and choose a non graphical boot process.... currently the computer boots straight into ubuntu, no grub 10 sec options or anything like that show up.

I am thankful for any help.

---

### Post by MAFoElffen on 2011-12-14
> **littleknowledge said:**
> Good day to you,  I recently installed ubuntu 10.04 to a dell gx260. It installed properly and on first login i went to update manager to download all updates. Now the computer boots properly all the way to the ubuntu (gnome) login screen and hangs (nothing responds, not even ctrl+alt+Fx keys) when showing the possible users to login with. 

Gx260 has an intel graphics card and I know they have given trouble in the past... so I figure the problem is related to the graphics part of the bootup. 

i would like to know if anyone knows how to stop the ubuntu boot process from going straight into graphical mode and choose a non graphical boot process.... currently the computer boots straight into ubuntu, no grub 10 sec options or anything like that show up.

I am thankful for any help.
With 10.04 (pre-11.10), copy the first menu entry from /boot/grub/grub.cfg and paste it after the existing lines in /etc/grub.d/40_custom... 

Go down to the kernel boot line (starts wit "linux") and delete quiet splash.  Insert in it's place "text". Save and exit. Use update grub to pick up the changes.

Is that enough info? Or do you need detailed instructions?

Use this for reference... Read posts 1-3:
 			**[B]Sticky:**[/B] [COLOR=#008C00]**[all variants] **[/COLOR][Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

