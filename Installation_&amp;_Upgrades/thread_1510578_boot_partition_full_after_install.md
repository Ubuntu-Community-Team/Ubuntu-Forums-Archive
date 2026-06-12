---
title: "boot partition full after install"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by klinger4077 on 2010-06-15
I am a Ubuntu newbie, so apologies if this is a silly question...

Today, I upgraded from 8.04 LTS to 10.04 LTS, my first upgrade.   I had the problem (shown in the upgrade documentation) with nVidea driver not working.   I clicked continue and everything seemed OK

At the end of the install, the upgrade GUI said it was not able to install certain components (it did not say, I presume the nVidea driver) and then it closed.    It never did the "cleaning up" section of the upgrade.

 I manually rebooted...    and now it says the /boot partition is full  (and it is)

Is there a way to manually kick off the cleanup process?   I don't really know what I am doing, so don't want to manually delete files if I can avoid it

Thanks

---

### Post by pastalavista on 2010-06-15
> 
I manually rebooted... and now it says the /boot partition is full (and it isMore info... does it boot? what says /boot is full? If it boots, my advice is to run in terminal ```
sudo apt-get install -f && sudo apt-get autoclean autoremove
```

---

### Post by klinger4077 on 2010-06-15
yes, it rebooted fine -- and all appears well except an error message popped up saying /boot was full  (it is 150Mb in size)

Many of the files on /boot are  initrd.img....generic.bak

I presume those bak files are no longer needed but not sure

---

### Post by klinger4077 on 2010-06-15
BTW,  I tried   sudo apt-get autoclean autoremove

a number of things were cleaned up -- but nothing on /boot

I think several of the images are from much earlier versions of ubuntu
initrd.img-2.6.20-16-generic  (and same with .bak)
initrd.img-2.6.22-14-generic  (and same with .bak)
   and
quite a few with 
initrd.img-2.6.24-##-generic  (various versions ...)

---

### Post by klinger4077 on 2010-06-15
Hopefully, the full boot partition was my only other issue (besides the known nvidia problem)

If anyone has this problem going forward, I recommend this post
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

its old, but still applicable

---

### Post by melon73 on 2011-11-15
I have come across this post when consulting a friend with the same problem i.e. a full /boot partition. He tried to clean out the old kernel files and delete them using nautilus not using rm in terminal. But the boot partition was still full in spite of him having emptied the trash can via the icon.

The problem is simple:

(1) He started nautilus from the launcher menu and, thus was running it not as root. So I told him to go to a terminal and type

```
sudo nautilus
```

He could then go to delete some of the oldest kernel files like abi-2.6.35-2x-generic, config-2.6.35-25-generic, initrd.img-2.6.35-25-generic, System.map-2.6.35-25-generic, vmcoreinfo-2.6.35-25-generic, vmlinuz-2.6.35-25-generic and launch gedit from the context to edit /boot/grub/grub.cfg and remove the lines referring to that old kernel version.

Still he didn't get freed up the space.

The reason was that he thought it would show in the trash bin icon on the task bar (bottom left) in the old gnome 2 desktop. But files deleted don't show there. They are in a hidden directory. So you have to first click CTRL+H to see the .Trash-0 directory.

(2) Navigate into this directory and subdirectory /files and you will find your deleted kernel packages there. Just select them and press SHIFT+DEL.

Et voila.

So this is an easy way to do it and actually all the apt-get cleaning etc. doesn't help to remove old kernel files automatically anyway. Only distribution upgrades offer you to remove some - if with restrictions.

---

