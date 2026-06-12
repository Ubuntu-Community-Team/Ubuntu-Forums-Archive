---
title: "Upgrade from 7.04 to 8.10 has me in a pickle..."
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by xdemoerin on 2008-11-24
Happily accepted to upgrade a stable system (64bit AMD) running 7.04 for 3 users and...
Halfway through the upgrade the installer crashed
Reboot and I get "Ubuntu is running in low graphics mode"... then a login which hangs after username & password.
So I figured to install 8.10 from a CD - during which I was asked if I want to migrate the existing accounts - duly agreed but still no joy (accounts did not migrate?)

Not being a guru in Linux means I'm a bit stuck.

Can anyone advise how to do any of the following:
- get the 7.04 >> 8.10 upgrade to complete properly with the existing accounts
- import the accounts into the 8.10 version now running on a new partition
- repair or roll back to 7.04 so I can start again.

FYI - trying to run the 7.04 version from the boot (GRUB?) menu with restore option seems to work - but doesn't change anything.

---

### Post by pytheas22 on 2008-11-24
Yes, 7.04 to 8.10 is a big upgrade (sort of like Windows 95 to XP); I'm surprised you got along as well as you did.

If I were you, since you say you have 8.10 installed and working on a different partition, I'd probably just try to import the existing user accounts there.  To do so, you'd first want to use System>Administration>Users and Groups to create the three accounts in 8.10.

After the three users exist on the new system, you can simply copy the contents of the /home directory on the 7.04 install to replace that of the 8.10 install.  Since all user data and settings are saved in /home, this should effectively give you three users with identical settings to what they had in 7.04.

The easiest way to copy everything would be to boot to the 8.10 system and launch the file browser by typing:
```

sudo nautilus
```

Then browse to the location of the 7.04 partition (I'm assuming it's being mounted by Ubuntu automatically; if it's not and you can't figure out how to mount it, let me know).  Find the /home folder there--the full path to it will probably be something like '/media/sda1/home' ('sda1' could be 'sda2' or 'sda3' or something different)--and just drag and drop that folder so that it overwrites the /home directory of the 8.10 system (the full path to this directory will be just '/home').

You may need to adjust permissions on the individual users' /home folders after you make the move; to do that, just right-click on the files in question, select 'Properties', then click the 'Permissions' tab.  Also, it's possible that some other things may not work (don't be shocked if you can't log into Gnome because you get a message about a bad .dmrc file, for instance), but if you google for the error messages that come up, you should be able to figure out how to fix the problems.  If not, let me know.

I know this might be confusing if you don't have tons of Linux experience and it probably won't be a 100% smooth process, but I think it's the best way to achieve the results you want.  Please let me know if you run into problems.

---

