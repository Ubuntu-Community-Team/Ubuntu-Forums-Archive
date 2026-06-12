---
title: "Ubuntu won't start up after 12.04 to 12.10 upgrade"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by sammorin on 2013-08-20
When the upgrade was finished it told me to restart and I did. When the computer started up it was just at a blank screen for about 10 min. So I turned it of and back on and the bios with the computer brand/logo screen shows and then the screen shows the ubuntu color but no ubuntu logo and then the screen turns black and just sits. The third time I tried, I left it for 25 min and it still does nothing. I tried unpluging it and holding the power button with no battery and then restarted it. Still nothing! Every once and awhile I can hear the fan spinning and then stop and spin again and stop. I have tried restarting it 6 times now and no luck. I'm so frustrated.

---

### Post by deadflowr on 2013-08-20
There are several things that might be going on, but mainly a graphics card problem.

First, try do this.
when you turn on the PC, right after(And I mean right when the screen goes blank) the BIOS screen hold own the shift key until the screen says grub something, then let go and hopefully you'll see a screen with listings for Ubuntu and other things.
Then hit enter and look for the line that ends with quiet splash.
try anding the word nomodeset to the end of that line.
Then save and exit.
And then in the menu screen, hit enter.(You should be back on the same line as before, usually the top line)

If by chance you can't get into the grub menu screen, then let the system load as before, and wait a minute.
Then press these three keys
```
ctrl + alt + F1
```
if F1 causes problems then try F2, or F3.
Hopefully this will get a terminal like screen with a login prompt, login as usual.
Then run
```
sudo nano /etc/default/grub
```
Which will open up the file that loads what was in the grub menu options(e)
Again, look for the line that says "quiet splash" and change it to say "quiet splash nomodeset"
Then press ctrl + x and then hit y for yes and then press enter.
Then try running 
```
sudo reboot
```
And see if that helps.

If not, then try loading into the F1, or F2 screen again, and run
```
lspci | grep VGA
```
and tells us what card it says.
Chances are that the drivers broke, and a purge and reinstall might be necessary.

---

