---
title: "Reinstalling Ubuntu/Installing Xubuntu"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by Not So Smart Guy on 2007-02-16
This is a result of my previous problem, which I've decided can only be resolved by trying a reinstall or switch to Xubuntu, for various reasons. To see my original thread, **_[click here](http://www.ubuntuforums.org/showthread.php?t=362374)_**. I believe it has to do with my NVIDIA graphics card and the problem others have been having with the X Server. I also believe I should be able to fix it by going to /etc/X11/xorg.conf and changing "nvidia" to "nv" (this is what I'm getting from reading other threads), but I when I enter the nano editor, I see nothing in the file, nada, blank. Anyway, read the thread for more info on how I probably screwed this up during install.

So as for the matter of reinstalling Ubuntu (5.10; see the thread for why I'm using an older release)... I've never quite done that before, I'm new to Linux as a whole and currently also running Windows XP on the same harddrive... can I simply reinstall Ubuntu over on the Linux partition or do I have to format the partition again? 

More importantly will any of this effect my ability to boot Windows? I have GRUB installed on the MBR, will removing Ubuntu screw with booting Windows? Moreover, will installing Xubuntu (and presumably placing GRUB on the MBR again) work smoothly? 

Please bear with me, as I said I'm new to this and these problems have been my first experiences with Linux, I'm sure you can understand how that can make a life long Windows user all the more apprehensive. Even though this should be simple, a nice tutorial or step-by-step instructions (or even a heads up on potential complications) would really help my piece of mind before doing this. Any help is much appreciated.

---

### Post by Kateikyoushi on 2007-02-16
The following command should reconfigure X for you saving you the intallation.
```
sudo dpkg-reconfigure xserver-xorg
```

If it works you can install xubuntu desktop to see what is it like.
```
sudo aptitude install xubuntu-desktop
```

Later you can remove ubuntu desktop with the following.
```
sudo aptitude remove ubuntu-desktop
```

---

