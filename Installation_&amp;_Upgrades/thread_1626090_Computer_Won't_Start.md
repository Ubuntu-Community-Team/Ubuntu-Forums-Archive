---
title: "Computer Won't Start"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by bridabom73 on 2010-11-19
Today, the update manager loaded as it always does, and I installed any updates that were available, and it said I had to restart my computer, so I clicked restart now. I left to go do other things while it was restarting, and I came back to find a black screen and nothing happening. I turned my computer off and back on again, but then after a few seconds it turned off and turned back on. Every time, it was just a black screen and nothing happened. Sometimes, it would come up with the usual Compaq logo, but then it would just go back to the same black screen. Other times, after the Compaq logo, it would go to the white underscore at the top left of the screen like it does while it's loading, but then it doesn't do anything after that. I went into the settings to see if it was loading from the hard drive and not some non-existing source, but all of the settings were fine. I really don't understand what is happening, and now I don't have a good computer to use. My computer is a Compaq Presario F500 laptop running Ubuntu 10.04. The only update that I remember seeing was a Flash update, and I don't see how that could do this to my computer. Has anyone else had such a strange problem? Do you know what could be wrong with it or how to fix it? Any help is appreciated. Thanks.

---

### Post by neo1786 on 2010-11-19
> **bridabom73 said:**
> Today, the update manager loaded as it always does, and I installed any updates that were available, and it said I had to restart my computer, so I clicked restart now. I left to go do other things while it was restarting, and I came back to find a black screen and nothing happening. I turned my computer off and back on again, but then after a few seconds it turned off and turned back on. Every time, it was just a black screen and nothing happened. Sometimes, it would come up with the usual Compaq logo, but then it would just go back to the same black screen. Other times, after the Compaq logo, it would go to the white underscore at the top left of the screen like it does while it's loading, but then it doesn't do anything after that. I went into the settings to see if it was loading from the hard drive and not some non-existing source, but all of the settings were fine. I really don't understand what is happening, and now I don't have a good computer to use. My computer is a Compaq Presario F500 laptop running Ubuntu 10.04. The only update that I remember seeing was a Flash update, and I don't see how that could do this to my computer. Has anyone else had such a strange problem? Do you know what could be wrong with it or how to fix it? Any help is appreciated. Thanks.

is ubuntu the only OS on ur machine??
try booting from a live CD and run a boot_info_script
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
remember to paste the contents of results.txt in CODE tags

---

### Post by drs305 on 2010-11-19
One possibility is a video problem. That would be the blinking cursor at the top left of the screen. (If you can get to any normal prompt (not a grub prompt) try typing *startx* )

If you can get to your Grub2 menu (if you don't see it, try holding down the SHIFT key during boot):
Try another kernel, if you have one.
If not, try the recovery mode and select the option that deals with video problems.

If that doesn't work, with Ubuntu highlighted in the menu, press "e" to edit the menuentry.
Cursor to the end of the "linux" line. Remove *quiet splash* and add *nomodeset*
Press CTRL-x to boot.

Another option instead of "nomodeset" is to delete "quiet splash" and add "single" if you weren't able to get to the recovery mode earlier.

If you get to the Desktop by any of these means, reinstall your video drivers via System, Hardware Drivers.

---

### Post by garvinrick4 on 2010-11-19
IF your problem starting during upgrades has a good chance of working:
Each command mounts something that is needed, no short cuts does not take long
to copy and paste in terminal: (USE YOUR OWN SDA#) to mount.
```
Put in a Live Cd (install cd) and Choose try ubuntu open a terminal and copy and paste
these: They are to mount your / and make it possible to get into root (with chroot command) and try to clean up the updates and upgrades you just did. 
Okay use: The first is to find what your sda# is I will use sda5 for this use your own.
Get your internet connection working in Live cd:
[CODE]sudo fdisk -l
``` (lower case L)
Now I will run the commands:
                       ```
sudo mount /dev/sda5 /mnt
```                  ```
sudo mount -o bind /dev /mnt/dev
```                        ```
sudo mount -o bind /dev/pts /mnt/dev/pts
```                       ```
sudo mount -o bind /proc /mnt/proc
```                      ```
sudo mount -o bind /sys /mnt/sys
```                      ```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```                       ```
sudo chroot /mnt
```                  ```
dpkg --configure -a
``````
apt-get update
``````
apt-get upgrade
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev                      
```   ```
sudo umount /mnt/proc
``````
sudo umount /mnt/sys
``````
sudo umount /mnt
``````
sudo reboot
```Now hopefully that fixed install

[/code]

---

### Post by bridabom73 on 2010-11-19
Well, I can't get to anything, not even the grub menu. And the blinking underscore always showed up when it was loading. After that, the log in screen would show up, but now it doesn't. And I tried a live CD, but it got to a keyboard icon next to an accessabilities icon at the bottom of the screen, and I pressed enter, but then the screen went blank and my computer restarted. I really don't know what to do. It didn't even get to the live CD loading screen until after many restarts, and it still didn't work. Electronics seem to hate me so much for some reason. :(

EDIT: Well, I left it with the battery out overnight and today until I got home, and now it works with no problems. Such a strange problem. Oh well. I'm happy now. :)

---

