---
title: "Problem passing wubi install to usb hd"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Marlonsm on 2012-11-25
Hello,

I have a wubi install I'd like to use from an external HD.
I've found some tutorials online, but they ask me to edit the menu.lst file but it isn't present in my install.

This is what I folowed: [http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/](http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/)

What I've tried so far:
Try to boot from the external hd anyway. It got to grub, but couldn't find the ubunutu install.

I edited grub options before trying to load ubuntu and changed the root=LABEL=USB part, but still got the same error.

I followed this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) using the recomended settings, booting from my live usb drive. My external hd was the only one on that computer at the momment.


Thanks.

---

### Post by YannBuntu on 2012-11-26
Hello

I recommend you:
1) backup your Wubi documents and settings (hidden folders located into /home/your_login )

2) install Ubuntu the standard way: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

3) then copy your documents and settings from your backup to your new Ubuntu.

---

### Post by Marlonsm on 2012-11-26
Thanks, I thought of doing that but the problem is that I have some programs installed and I'd have to install and configure them again. Is there a way to also copy my programs? Even if some of the are not in the repositories?

But I think it might be the best way to do, even if it takes me some time...

Thanks

---

### Post by YannBuntu on 2012-11-26
> **Marlonsm said:**
> Is there a way to also copy my programs?

Probably, but better reinstalling them, it will avoid some problems.

---

### Post by oldfred on 2012-11-26
Your link says it is obsolete as it uses grub legacy, but they also link to a newer version.

I also suggest a full install, if you have a larger flash drive.

I do not really recommend this, but it is from the author of the bootinfoscript who really understands the details of systems. I think it was more to prove it could be done.
       See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

    
You can list all your packages:
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
But if you downloaded and installed others not from repositories, and only if installing exactly the same version you may be able to copy the .debs, if you have not housecleaned.
       Location of downloaded debs
/var/cache/apt/archives/

---

