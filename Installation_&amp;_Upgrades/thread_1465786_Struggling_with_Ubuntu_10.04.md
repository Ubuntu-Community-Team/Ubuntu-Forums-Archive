---
title: "Struggling with Ubuntu 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by billiusmaximus on 2010-04-29
My desktop machine used to dual boot to Ubuntu 9.04 and Windows XP. I just did a fresh install of the new 10.04 - I specified that I wanted the partition with 9.04 to be formatted and the root to be installed there.

Now I cant boot XP - the grub menu doesn't even show as if Ubuntu is the only OS on my machine. I have not figured out how I am going to fix this yet.

Also, I was having problems installing the wireless drivers. I managed to get the firmware downloaded and the drivers appear to be installed, but when I click the pull down menu at the top right, it says the device is not ready.

If anyone can help, I would really appreciate it.

Thanks,
Billius

---

### Post by phillw on 2010-04-29
> **billiusmaximus said:**
> My desktop machine used to dual boot to Ubuntu 9.04 and Windows XP. I just did a fresh install of the new 10.04 - I specified that I wanted the partition with 9.04 to be formatted and the root to be installed there.

Now I cant boot XP - the grub menu doesn't even show as if Ubuntu is the only OS on my machine. I have not figured out how I am going to fix this yet.

Also, I was having problems installing the wireless drivers. I managed to get the firmware downloaded and the drivers appear to be installed, but when I click the pull down menu at the top right, it says the device is not ready.

If anyone can help, I would really appreciate it.

Thanks,
Billius

Hi, 

go into System --> Administration --> Update Mananger 
tell it to update your system (check for updates). It may take a while as the servers are getting hammered, if **any** update fails, tell it to try again until they are all in.

If it finds updates, let it install them, if it does not still do the following:

from terminal issue```
sudo update-grub
``` You're looking for it finding the Windows area, if it does simply re-boot. If it does not, then reboot and try the update-grub again.

Regards,

Phill.

---

### Post by Foster Grant on 2010-04-29
The GRUB problem is the big bug that held up 10.04 release for several hours today. A fix was released early this afternoon (my time).

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/570765)

Load up the Disk Utility in the System > Administration menu and see if it's there. You may have to manually (and VERY carefully and only after backing up) hack your GRUB settings in the file "menu.lst" to add the Windows partition.

KDE has a great GRUB editor -- which could make it too easy for people to edit their GRUB menus. Anybody know what that package's name is? I use GNOME but I'd love to have that KDE GRUB editor.

---

### Post by phillw on 2010-04-29
> **Foster Grant said:**
> The GRUB problem is the big bug that held up 10.04 release for several hours today. A fix was released early this afternoon (my time).


That is why I told the OP to do an update, that sorts it out. Only if you had managed to get a partial final would it affect you, and then only on a new installation.

Regards,

Phill.

---

### Post by billiusmaximus on 2010-04-29
Thank you, I really appreciate your support. I am going to give this another try tonight.

I should probably volunteer some more information though.

Internet service is provided with the rent in my apartment complex, and because the router is in another apartment, I don't have hardwire access to the internet.

My solution was to tether my android phone using a proxy app. Then I set up the ubuntu system to run through a proxy. It's slow, but I think it works well enough until I can get the wireless drivers working.

---

### Post by billiusmaximus on 2010-04-29
I tried running the update manager; it downloaded 42 packages, but didn't find any new updates. I also ran the command 'sudo update-grub' and it didn't list off a Windows partition.

Billius

---

