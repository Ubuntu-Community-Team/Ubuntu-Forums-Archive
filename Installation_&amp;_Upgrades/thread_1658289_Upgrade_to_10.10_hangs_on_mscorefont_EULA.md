---
title: "Upgrade to 10.10 hangs on mscorefont EULA"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by bob12564 on 2011-01-02
I'm in the middle of an upgrade from 10.4 to 10.10.  The EULA for mscorefonts installer is behind the upgrade window and I can't respond to the EULA to continue the install.  I can click the checkbox to accept the EULA but that's all.  I can't move the window to expose the rest of the EULA box and I can't move the upgrade window either.  I'm afraid that I just hosed my computer.

Does anyone know how to respond to the EULA to continue the upgrade?  I've tried hitting enter and "O" (for OK) and "Y" (for yes) and tab+enter.  I've also tried unchecking the box and also hitting ESC.

Help!

Thanks.

---

### Post by bapoumba on 2011-01-02
I think the Tab key will get you to accepting the license item.

---

### Post by bapoumba on 2011-01-02
I think the Tab key will get you to accept the license. I sort of remember doing that once :)

---

### Post by bob12564 on 2011-01-02
I tried tab and then hitting enter.  Nothing.

I now made it worse.  I tried to open Firefox and it did open but I can't close it.  It's covering everything else on the screen.  I tried some keyboard commands but I suspect that the window manager is disabled during the update process.

I can still get to the shutdown menu but I'm afraid the machine will not boot.  Does anyone know what will happen?  Can I recover somehow?

---

### Post by ajgreeny on 2011-01-02
Either open a terminal and use command ```
killall firefox
``` to kill that or for future reference just the command  ```
xkill
``` move the cross cursor that appears to the misbehaving app and click; app gone.

I'm not sure what to suggest for your mscorefont problem, so will have to leave that to others.

---

### Post by bob12564 on 2011-01-02
Thanks for those commands but I couldn't use them.  Apparently all the Gnome windows functions are disabled during an upgrade.  I was able to use the mouse to access the Ubuntu menu at the top and that's how I opened Firefox.  But it opened over the Ubuntu menu and the only thing that was exposed was the shutdown menu.  I tried a restart but the system was broken.

The fix was to reboot and hold the shift key which brings up the grub menu.  If you have a non-partitioned drive with only Ubuntu on it, you don't get the grub menu automatically.  Once you have the grub menu you can select recovery and then select the option to fix broken packages.  That seems to restart the upgrade in command mode and installs the new packages.  I even got the same EULA that started this mess but this time I was able to respond to it.  After a restart all seems to be well (I hope).

I've been doing upgrades since 7.10 and this is the first time I had a problem.  I see that some others fell into this trap and I hope this thread helps someone else.

Thanks to all who replied.

---

### Post by sunnyd47 on 2011-01-16
Bob - 

I tried your fix but my install STILL gets stuck on the eula agreement screen, the screen is half size and to the top left of the screen. I cannot make the screen take my <OK> response. Anyone got any other tips/tricks to get round this?

EDIT-

Just seen the short  post above and "TAB" worked just fine for me.

---

