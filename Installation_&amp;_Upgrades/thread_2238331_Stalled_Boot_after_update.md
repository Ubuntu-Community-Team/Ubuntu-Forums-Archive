---
title: "Stalled Boot after update"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by cathect2 on 2014-08-07
After the most recent update to 14.04, I now have a stalled boot after login. I enter my password and then I just get a blank system wallpaper. No icons. Nothing seeming to happenin within the machine at all. I am unable to get a terminal. It's just stuck.

Does anyone have any advice or suggestions?

Thanks!

---

### Post by oldfred on 2014-08-07
Can you boot recovery mode? Second line in grub menu.

From that you can get to terminal, run fsck, add Internet and update with terminal etc.
It does set it to read only initially, one of the options is to remount r/w. 

Sometimes just redoing update from terminal fixes things.

Houseclean, update & refresh dpkg
 sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get -f install
sudo dpkg-reconfigure -phigh -a

---

### Post by cathect2 on 2014-08-07
Hey, Oldfred. I have been able to boot into recovery mode. I selected fdisk and something begins (perhaps two lines of code regarding two HDs) then it just sits there eternally. Is that normal? How can I get a terminal from the recovery mode?

---

### Post by cathect2 on 2014-08-07
Ugh. Now for some reason I can't get into recovery mode. But recovery mode doesn't seem to be functioning properly anyway. Was GRUB recently updated? It always seems to break my machine.

---

### Post by oldfred on 2014-08-07
If you ran sudo fdisk -lu, it should just output list of drives & partitions & return to terminal input.

If fdisk hangs then that may say you have corruption in some partition. Then you should boot a live installer and run fsck on your Linux partitions. Or you have partition table corruption which may need testdisk or other fixes.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Daedal on 2014-08-07
Having the same problem.

Pretty sure it's a problem with the recent nvidia graphics driver update... That showed up in my updates. I saw it and knew better than to install it but the cuda and openCL updates that were with it along with my Blender usage got the best of me.

Unity doesn't load but the login manager does.  Though it's not displayed over the full screen. It has a black frame around it and my second monitor stays signalless.

---

### Post by cathect2 on 2014-08-07
UPDATED

Daedal: makes sense to me. I am also using dual monitors. Perhaps that is it? 

Anybody with a solution to downgrade the Nvidia driver? Not sure how to do that.

---

### Post by oldfred on 2014-08-07
I just rebooted into 14.04 and ran updates.
I have an older nVidia card 9600GT and am using nVidia updates version.

It did update a new driver nvidia-opencl-icd-331-updates, but on reboot system still works like normal.

---

### Post by cathect2 on 2014-08-07
Do you have dual monitors?

---

### Post by oldfred on 2014-08-07
No, just one old LCD that is 4:3 not wide screen like most users now have. Part of reason I prefer fallback/gnome-panel over Unity.

---

### Post by Daedal on 2014-08-07
Towards the end of my /var/log/syslog it's saying

Nvidia-persistanced: failed to query nvidia devices. Please ensure that the nvidia device files (/dev/nvidia*) exist and that user 116 has read and write permissions for those files.

Nvidia-persistanced: the daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistanced

The files are there so can anyone tell me how to add the permissions to that user from the terminal?

---

### Post by oldfred on 2014-08-07
How did you originally install nVidia. 
I only install from Ubuntu repository, but some install from ppa or directly from nVidia and then have these type of issues. If so you almost always have to purge & reinstall on major updates.
Installs from repository usually work, but even that sometimes has issues.

---

### Post by Daedal on 2014-08-07
I'm pretty sure that I installed from the Ubuntu repos.

I used to have to deal with issues on every major update 'cause I had an amd workstation card and Ubuntu doesn't (or didn't) keep any of the official and drivers for workstation cards. Ended up swapping to a nvidia gaming card because amd seems to be dragging around with opencl stuff in their drivers according to the Blender guys which has pretty much caused GPU rendering to be nvidia only for blender's cycles render engine.

I can't remember for sure that I didn't install from a ppa or directly from an nvidia download but I remember thinking how nice it was not to have to do that when I swapped to the nvidia card.

---

### Post by Daedal on 2014-08-07
Got it fixed.
Purged the old drivers, rebooted and it loaded unity 2d or fallback mode or whatever that's called these days... Then just reinstalled the drivers with the additional drivers tab in the software and updates settings.

Hopefully it will work for you too cathect2.
To get to the terminal I was letting it get to the login screen and pressing Ctrl+alt+f1

Gotta log in there then 
Sudo apt-get purge nvidia*

Then sudo reboot. And install the drivers like it's the first time any are being installed.

Also, i'm no expert by any means so any tips about if any of that would be better done some other way would be helpful. (And why... Reasoning helps me remember)

---

### Post by cathect2 on 2014-08-07
I did the same thing. I chrooted into my installation then purged nividia*. I'm now using Nouveau drivers.

Daedal, are you back using Nvidia? Which one is working for you? I don't want to go through this again!

---

### Post by oldfred on 2014-08-07
the purge is often an important step that many forget to do. Different versions of nVidia conflict otherwise.

I have old card and just install current updates version. screenshot attached.
Unless you have a bleeding edge or very new nVidia card the current or current updates should work.

---

### Post by Daedal on 2014-08-07
using 331.38 from nvidia-331-updates. same as what oldfred posted a screenshot for.

---

