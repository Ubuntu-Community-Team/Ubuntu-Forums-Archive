---
title: "Problems after upgrade"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by gbarron on 2010-07-10
Hi Guys,

I received a message saying that the new version of Ubuntu (10) was available and happily clicked the upgrade button.  All seemed well, but after a reboot I discovered 3 problems.  

1. The sound card is lost after every reboot.  I install the 4Front drivers and sound is there.  I reboot and no sound.

2. Every time I start Ubuntu I have to run metacity --replace.  I have been through all the tutorials I can find to fix this, but none have worked.  My windows still have no decoration.

3. Most serious due to work requirements.  After the upgrade I can still see my windows 7 in the boot list, but when I select it nothing happens.  I just get a blank screen with a flashing cursor.

Any help gratefully received especially on the Windows boot as work is piling up.

Regards

---

### Post by ajgreeny on 2010-07-10
For the windows boot problem, try ```
sudo update-grub
``` if you have not already done so.

For the metacity --replace problem, go to system -preferences -appearance and set none in the Visual effects tab.

For window decoration problem with compiz, install compizconfig-settings-manager and enable the window decoration plugin.

---

### Post by gbarron on 2010-07-10
Hi,

The visual effects were already set to none and I checked that the window decoration was on within the Compiz manager, which it was.

I also tried the grub update.  The update was successful, but it had no affect on booting.  I still cannot boot in to Windows.

Regards

---

