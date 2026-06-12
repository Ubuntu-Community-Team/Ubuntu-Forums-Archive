---
title: "Install windows 7 after Kubuntu already installed"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by joelmhall on 2011-10-13
I have Kubuntu 11.04 installed and just the way I like it. I don't want to have to reinstall everything again. I regret to say I would like to also have windows 7 alongside, but I am not sure if I have the procedure down. It seems the best way is to backup my system, install windows 7, install Kubuntu again and then restore from my backup. I think grub will need to be redone after the restore. I have backed up with tar (excluding certain directories) onto an external drive. I am not sure if after a new Kubuntu install (alongside windows) that the restore will put everything back the way I have it now. Right now, my harddrive is only Kubuntu. I am not seeing a grub chooser screen before the OS starts like in the usual dual-boot systems.

Thanks in advance for any and all advice!

---

### Post by mastablasta on 2011-10-13
have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and here: [http://ubuntuforums.org/showpost.php?p=9573188&postcount=4](http://ubuntuforums.org/showpost.php?p=9573188&postcount=4)
 
basically you need to recover grub (using LiveCD or LiveUSB) afetr the windows is installed.

---

### Post by joelmhall on 2011-10-15
Thanks, mastablasta. I tried the last link and it worked as advertised. Easy and quick.

I found though, that resizing my linux partition was slower than I expected. Maybe there is something different with linux partitions because I have shrunk ntfs partitions before and it seems quicker.

---

