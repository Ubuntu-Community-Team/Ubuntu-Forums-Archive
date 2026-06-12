---
title: "Dual screen doesn't work in 13.04"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by Lutz_NL on 2013-07-07
I had first a Windows 7 installation wherein I used the old way of booting via the MBR. Then I added Ubuntu, at that time 12.04. The installation was then twice upgraded to 12.10 and 13.04. I then upgraded to additonally a second screen, and it nether worked perfectly. Thereafter I decided to install Ubuntu fresh from the DVD and to format my root partition / and not to format my /home partition. I have a built in graphics card based on an Intel chipset.

Thereas the liveDVD worked with both screens in mirrored mode, after a installation no screen was working. The left screen complained "out of range", the right one missed some parts of the screen, and the mouse couldn't click anything. I first patch was to add "nomodeset" to grub. The result is that I have now two mirrored screens working in 1280x1024 mode, whereas the right screen is supposed to run in fullHD mode.

I already tried to configure xrandr:

Uitslag van xrandr --query:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 

These are the configuration parameters of the left screen, the right screen doesn't show up at all.

To summary: no "nomodeset" in grub leaves the screens useless. With nomodeset both screens work in mirrored mode, but only one screen is discovered. Having an Intel chipset means no proprietary drivers are required.

How can I solve this? In Windows 7, both screens run in their native resolution and I can boot the computer with only the left screen powered up, or only the right screen powered up, or both screens powered up.

---

### Post by ohnonot on 2013-07-09
the first part of your post sounds confusing.
do you have only ubuntu on your computer now?
or ubuntu on a separate partition (dual boot with windows)?
or are you running ubuntu inside windows?

if you have only ubuntu i would recommend to make a fresh automatic default install, without the external monitor, without any changes to the install process, always choose the default option.
only after that attach the external monitor and set it up.
i'm sure unity has its own ways of doing this, but you can alway install arandr and use that. it's a gui frontend for xrandr. 

tell us how you get along, there's more help coming!

ps: are you sure you need the 13.04 version? i'd rather recommend the LTS.

---

### Post by Lutz_NL on 2013-07-09
I have a clue what went wrong. I always kept my /home partition and only installed the / partition freshly. If I log on with my previous user name, then the screens go crazy. If I log in as guest, both screens run smoothly. What I could do now is: I could reinstall again and keep the /home partition. But for the reinstallation I could use another user name, e.g. Lutz2.
If I do that, I have to take care that I can migrate my mail archive in Thunderbird from the old username to the new username. I think I know how to handle my firefox bookmarks and how to handle my picture collection.

So my question is: could it be so simple that my desktop settings fail nowadays with the old username, but if I create a new username then it works?

---

### Post by ohnonot on 2013-07-09
try it! there's no harm in it.
of course, even if it helps, it would be good to know what caused the trouble.

btw, i have several linux installations on my computer, but they all got hteir own /home. each is installed on a 10GB partition, plenty for even a fullblown unity install.
usually it's just a few folders that take a lot of space, like pictures, videos, downloads... i have those on a separate partition and link them to where they should show up in the home folder (e.g., on a new install i delete the folder "Downloads" and place a link to my downloads on the separate data partition and name it "Downloads"). works like a charm, even for thunderbird & firefox. if you are using the same versions of thunderbird and firefox!
i tried the seperate /home partition once but it takes much more work to smooth the edges manually, esp. if one's using different distros.

---

### Post by Lutz_NL on 2013-07-15
Finally I worked out the cause of my installation problems. Ubuntu cannot handle at installation time different screens with different resolution. So I unplugged the second screen and reinstalled Ubuntu (also formatted my /home partition). Ater a restart I plugged in the second screen, and after 3 more restarts both screens were running in their native resolution. I have to thank a friend from the open-suse community who came up with the idea of unplugging the second screen during installation.

---

