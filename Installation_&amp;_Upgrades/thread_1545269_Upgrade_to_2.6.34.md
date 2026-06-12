---
title: "Upgrade to 2.6.34"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by BBaumer on 2010-08-03
I'm running BackTrack 4 and am trying to upgrade the kernal to 2.6.34. I've tried two different ways and both fail. I'm very new to Linux, so troubleshooting this is kicking my butt.  I first tried using Synaptic Package Manager to run the update. It says /lib/modules/2.6.34/kernal already exists. Whether I choose to stop the installation or not, I end up getting a failed error stating E:/var/cache/apt/archives/linux-image.2.6.34_2.6.34-10.00.Custom-bt8_i386.deb: subprocess pre-installation script returned error exit status 1. After I hit close, the update shows as broken. I've tried it a couple times with the same result.  The second method I tried was the steps post at [http://www.offensive-security.com/backtrack/how-to-update-backtrack-2-6-34/](http://www.offensive-security.com/backtrack/how-to-update-backtrack-2-6-34/). On that page, I got to the point where you enter the following command:  cp /boot/config-2.6.34 .config  That file does not exit. Since they "don't do basic Linux", I'm turning to Ubuntu Forums for assistance. How do I resolve either of these issues and complete the upgrade? My installation is a dual-boot (Windows XP) on a Dell Latitude D410.

---

### Post by ahbart on 2010-08-03
I'm not sure, but sound like you have to remove the 2.6.34 packages completely (purge). 
Have you downloaded these 2.6.34, or have you added some kind op repository?

---

### Post by BBaumer on 2010-08-04
I haven't manually added any kind of repository. I simply ran the Synaptic Package Manager to get the pacakge. After rebooting the machine overnight, I night have issues running "startx" afterlogging into the machine under the original install.

---

### Post by davidmohammed on 2010-08-04
2.6.34 isnt in the lucid repository - are you running maverick?

---

### Post by JBAlaska on 2010-08-04
2.6.34 is default on BackTrack 4 R1 BlackHat Edition.

If you didn't get one in Vegas, Here's how you upgrade:
[Link](http://www.offensive-security.com/backtrack/backtrack-kernel-upgrade-2-6-34/)

---

### Post by BBaumer on 2010-08-04
> **JBAlaska said:**
> 2.6.34 is default on BackTrack 4 R1 BlackHat Edition.
 
If you didn't get one in Vegas, Here's how you upgrade:
[Link]("http://www.offensive-security.com/backtrack/backtrack-kernel-upgrade-2-6-34/")
 
I was able to snag a copy at BH. I think my disk is hosed though. When I boot to it, I get the following:
 
SQUASHF error: Unable to read page, block 15d2aad, size 8263
SQUASHF error: Unable to read fragment cache entry [15d2aad]
SQUASHF error: squashfs_read_data failed to read block 0x15d2aad
Kernal panic - not syncing: Attempted to kill init!
 
The first three lines are repeated numerous times before the last line appears. At that point, all I can do is power cycle the computer. :confused:
 
I'm working through the steps on the link you provided. I'm hung up on the part where you move the bt4-final.iso to the new ISO folder. I don't know where the ISO is?

---

### Post by JBAlaska on 2010-08-05
> **BBaumer said:**
> I was able to snag a copy at BH. I think my disk is hosed though. When I boot to it, I get the following:
 
SQUASHF error: Unable to read page, block 15d2aad, size 8263
SQUASHF error: Unable to read fragment cache entry [15d2aad]
SQUASHF error: squashfs_read_data failed to read block 0x15d2aad
Kernal panic - not syncing: Attempted to kill init!
 
The first three lines are repeated numerous times before the last line appears. At that point, all I can do is power cycle the computer. :confused:
 
I'm working through the steps on the link you provided. **I'm hung up on the part where you move the bt4-final.iso to the new ISO folder. I don't know where the ISO is?**

Try adding ```
all_generic_ide
``` to your grub install line to try and install the BH edition. If that does not work, you can re-download the BT4 iso from [Here](http://www.backtrack-linux.org/downloads/) 

Or you can do a search for bt4-final.iso on the box you originally downloaded it on.

---

