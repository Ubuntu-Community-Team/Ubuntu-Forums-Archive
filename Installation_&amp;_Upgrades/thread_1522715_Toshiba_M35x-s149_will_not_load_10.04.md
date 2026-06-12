---
title: "Toshiba M35x-s149 will not load 10.04"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by windquest on 2010-07-02
I am doing a clean install of 10.04 from 9.10. The live CD quits soon after the Ubuntu logo appears....the screen displays a few color bars in the center and then goes blank with no drive (CD) activity.  I suspect the video card is the problem but I don't know what (if anything can be done) Here is what I have tried so far:

Up dated the Bios to the current version.

Tried the alternate CD - loads fine through out the entire installation BUT on reboot, the load only gets as far as the live CD did.

I have tried all the options under F6 with no improvement. I have re-installed 9.10 from a live CD, work perfectly.

I have NOT tried an upgrade from 9.10, but I suspect this would not make any improvement.

So, I suspect the video card is not compatible with 10.04 (intel stuff)....there is no information on the Toshiba web site....so any and all ideas would be greatly appreciated. Any many thanks to all on this wonderful forum.
Henry

---

### Post by davidmohammed on 2010-07-02
careful with the ISO burn - often burning with the slowest speed is the best to get a good install CD...

if you are convinced the CD is OK then try an install experiment

Press F6 - at the bottom of the screen you will see a line of characters that at first looks like gibberish! in there you'll see "quiet splash".

Add one of the options below suggested immediately before quiet splash before continuing with "try without installing"

i915.modeset=1
i915.modeset=0
nomodeset

e.g.  ... i915.modeset=1 quiet splash -- ...

---

### Post by windquest on 2010-07-02
I was sure that I had tried all of these steps, however i915.modeset=1 allowed for a complete installation.  Many thanks....all I can think of is that I may have made a typo.  Now then, at re-boot I cannot add this to the grub loader...actually I can't get to the loader using either the arrow keys or F2.  I did boot the live CD and tried to modify the file but update-grub fails using this method....so how do I make the i915 change to the boot loader?

Thanks....I can't believe how quick you responded....THANK YOU!!!!!!!
Henry

---

### Post by davidmohammed on 2010-07-02
press and hold down the shift key to display your grub.  Then press e to edit.  Find the line with quiet splash and add i915.modeset=1 immediately before this.

To fix it permanently

sudo nano /etc/default/grub

find the line

GRUB_CMDLINE_LINUX=""

change it to
GRUB_CMDLINE_LINUX="i915.modeset=1"

save

then run

sudo update-grub

---

### Post by windquest on 2010-07-02
thank you, Thank You, THANK YOU!  Either my brain is dead, or 10.04 is doing other things, but your solutions worked perfectly, up and running and booting correctly.  Maybe someday I will be able to help others...in the meantime, thank you again.

Henry

---

### Post by 2010NissanFrontierSEV6 on 2010-11-05
> **davidmohammed said:**
> press and hold down the shift key to display your grub.  Then press e to edit.  Find the line with quiet splash and add i915.modeset=1 immediately before this.

To fix it permanently

sudo nano /etc/default/grub

find the line

GRUB_CMDLINE_LINUX=""

change it to
GRUB_CMDLINE_LINUX="i915.modeset=1"

save

then run

sudo update-grub

Can someone please add information on how to save these changes? Simply saying save is not enough. There is no visible option to save anything, after changing the line. THANKS!!

The line to edit GRUB should read sudo gedit /etc/default/grub. Not sudo nano /etc/default/grub. By using gedit instead of nano another window opened to edit grub with the option to save any changes.

---

### Post by Handssolow on 2011-03-03
Thanks, after reading this thread I was able to install 10.04 Lucid on a Toshiba M35x-s114 Laptop by adding i915.modeset=1.
I'm now trying to sort out the how to play a DVD. Currently I need to reboot if I open VLC. I'm not sure if this is a related graphics issue.

---

