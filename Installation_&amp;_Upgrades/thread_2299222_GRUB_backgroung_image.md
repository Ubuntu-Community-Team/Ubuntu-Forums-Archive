---
title: "GRUB backgroung image"
date: 2015-10-16
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2015-10-16
I'm running Ubuntu 14.10 

I have the following line in /etc/default/grub:
GRUB_BACKGROUND=”/home/reuven/Documents/MyData/Pictures/SarahReuvenAtWeddingMarquetteJune282015.png”

But I do not get the image.  I ran
sudo update-grub

I am getting the other changes i made (the beep for instance), but no image.

Are there size limits or other restrictions?

---

### Post by deadflowr on 2015-10-16
I haven't used that method in years.
Instead I simply copy the image into the /boot/grub folder, and then run the update-grub command.
The output always shows a line: Found background image: some file name here.

I'm not sure about size restrictions.
Never had any problems regarding those, either extra small or extra large.
(the smaller sizes just look bad, if i remember correctly as they need to fit the screen and tend to get super pixel-ed.)

Also, sidenote that 14.10 is no longer supported.

---

### Post by ajgreeny on 2015-10-16
I never see the grub menu but all the info you need to add a background image is in section 8 of the first post of [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275).

---

