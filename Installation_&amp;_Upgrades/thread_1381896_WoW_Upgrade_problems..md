---
title: "WoW Upgrade problems."
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by JfaSho on 2010-01-15
Hi,
Fairly new to ubuntu, still working out the kinks but Im having an issue with world of warcraft, I cannot update it with the patches ive downloaded.

------
jriehle87@jriehle87-desktop:~$ fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
jriehle87@jriehle87-desktop:~$ fixme:ole:OleCreateStaticFromData (not shown), stub!

-----
is what i get when i execute the the patch file.

Any help with this id appreciate it, im also recieving a problem with frostwire, it doesnt play mp3s and when i double click a song it starts shuffling through the Queue at the bottom. I can play mp3s just not in frost-wire.

---

### Post by JfaSho on 2010-01-15
The update could not be applied.
 The file "C:\Program Files\World of Warcraft\Battle.net.dll.temp" could not be created. If this problem persists, you may be able to solve it by uninstalling and then reinstalling the game. If you are unable to correct this problem, please contact Blizzard Technical Support. (InstallerFile::Create)


Ive highlighted whats in the box and this is what it says.

---

### Post by ptn107 on 2010-01-15
Check the permissions on the WoW folder (type this in a terminal).

```
sudo chown -R jriehle87:jriehle87 /home/jriehle87/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
```

If your still having problems you may want to delete the patch files again and let WoW re-download them.

*On a side note I've noticed WoW will not update or play when running on the ext4 filesystem.  I've had to change it back to ext3 in the past to fix it.

---

### Post by JfaSho on 2010-01-15
Thanks for a speedy response, yea i was tinkering and i figured it out :)

Thanks!

---

