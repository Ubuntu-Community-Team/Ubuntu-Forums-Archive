---
title: "[SOLVED] Bootscreen"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by rockstarrem on 2008-07-21
Hello,

I frequently (hopefully not anymore) reinstall Windows and it overwrites the boot screen. I'd like to keep Ubuntu on the machine without needing to reinstall JUST for the bootscreen. Is there a way to make it permanent? 

Thanks!

---

### Post by Rocket2DMn on 2008-07-21
Moved to Installation & Upgrades

Yes, when you install Windows, it overwrites the MBR.  There are a couple of methods to restore GRUB.  Have a look at [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]
You can also use the Super Grub Disk - [http://supergrubdisk.org/](http://supergrubdisk.org/)

---

### Post by rockstarrem on 2008-07-21
Thank you so much! Don't know why I couldn't find it anywhere else.

---

### Post by falcon61102 on 2008-07-21
You don't need to completely reinstall Ubuntu, you just need to reset your GRUB.  

I'm guessing that once you reinstall WinXP you can't get back into Ubuntu.  If you can, great, otherwise just boot up with a LiveCD and you can work on your GRUB from there.

Once in Ubuntu, open up a terminal and start with:
```
sudo grub
```

Once the grub loads, you want to find where your boot information is:
```
find /boot/grub/stage1
```

That should give you an output similar to hd(0,1) which is GRUB's way of identifying which partition holds your GRUB info.  Use what that in the next line, so for instance:
```
root hd(0,1)
```

That is telling GRUB where your root partition is.  Finally, setup up the GRUB with:
```
setup hd(0)
```

Those hd options may be slightly different for you, but just remember for the root option, use the output of the last command.  For the setup command, you want to just direct it to the hard drive and not to a particular partition so just use the first number.  

When you run the setup command you should get about 6 lines of output back and if completed successfully there will be no lines that end in "Failed."

---

### Post by rockstarrem on 2008-07-21
Thanks again for the reply, I'll print this for future reference.

---

