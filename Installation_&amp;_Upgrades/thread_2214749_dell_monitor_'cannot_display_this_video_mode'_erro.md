---
title: "dell monitor 'cannot display this video mode' error after Ubuntu install"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by dirty_ass_shoes on 2014-04-02
hi. i tried installing ubuntu 12.04 32-bit on a Dell Inspiron 531 desktop, as a dual-boot scenario with Windows Vista already installed.

The installation process seemed to go smoothly, and after a reboot, i see the boot screen (telling me i am using Dell hardware) and after that goes away, where i am expecting the option to boot into windows or ubuntu, i get a black screen with the following error on my monitor:

1: Auto Detect (Analog Input)
Cannot Display This Video Mode
Optimum resolution 1440x900 60Hz

If I press the enter key, the Ubuntu stock background comes up, then a screen with various shades of orange and black that is definitely not supposed to be there.

Any help would be appreciated, thanks.

---

### Post by papibe on 2014-04-02
Hi dirty_ass_shoes. Welcome to the forum ):P

Wait about 20-30 seconds after that message and press Ctrl+Alt+F1

You should get into a login screen in text mode. Login as you, and then:

Edit the grub file:
```
sudo nano /etc/default/grub
```
Look for a like that looks like this:
```
#GRUB_GFXMODE=640x480
```
Remove the '#' so it looks like this:
```
GRUB_GFXMODE=640x480
```
Alternative you may change the resolution for one that your monitor supports like 800x600, 1024x768 or 1280x1024.

Save the file. And update grub:
```
sudo update-grub
```
Reboot:
```
sudo reboot
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by dirty_ass_shoes on 2014-04-03
hi, thanks for the fast reply!

it took a few tries to reach the text mode screen, i suppose i just had to get my timing right or something, but i WAS able to follow your instructions.

after following your directions, the computer rebooted and i chose Ubuntu, with Linux 3.11.0-15-generic, and it seemed to load as it should.

however, i was going to show my dad the grub menu so he could log into windows in the morning, so i restarted the computer using the gear in the upper right of the desktop.
it rebooted, dell logo then grub, and when i chose ubuntu again, i'm having the same issue where there is a flashing line as if for text for several seconds at the top left of the screen, and then the ubuntu with dots under it splash screen, then a black screen with the mouse cursor, then the stock background for just a moment, and then the orange & black broken screen again.

---

### Post by papibe on 2014-04-03
Hold the key SHIFT while booting to stop at the grub menu.

Regards.

---

