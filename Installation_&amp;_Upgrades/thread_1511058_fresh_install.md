---
title: "fresh install"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by cartesian on 2010-06-16
I have a laptop that dual boots vista and ubuntu with a grub menu at startup where I can choose either windows or linux.

I tried to install the ATI drivers for ubuntu but it has not gone to plan and now I have a linux partition I cannot use.  I've tried to fix it by posting messages in the forums but have not been successful.

I now think the best option is to do a clean, fresh install. I've copied off all the files I need

If I put a linux install disk in will it just overwrite the linux partition with a completely new linux install and not affect the windows partition as this is a different file system?

Can I resize the partitions at the same time?

Will it create a new grub menu for me?

Thanks for your help.

---

### Post by oldfred on 2010-06-16
To reuse partitions you have to use manual install and manually select which partiion is / (root) adn what format to use. It finds swap on its own. If you have a separate /home you select it but tell it NOT to reformat.

You can boot into the liveCD and use gparted to modify sizes before running the install.

As long as windows works the grub install will find the windows install and add it to the new grub menu. The new grub2 osprober even finds non working windows in many cases but then it still will not boot until repaired.

---

### Post by cartesian on 2010-06-16
Is there a way of telling which partition is the Linux /root without guessing by the size of the partitions?

Also what do you mean by a separate /home an why to NOT reformat?

Thanks

---

### Post by oldfred on 2010-06-16
You can see your partitions types with 
```
sudo fdisk -l
```

I label my partitions, so I know which is which. This shows UUIDs and labels:
```
sudo blkid
```

If you have a separate partition with /home you do not want to reformat it since it has all your data and settings. If your /home is part of root you need to back it up and besure to include the hidden settings.

If you want to fully document your system. I run this just to know what I have where and save it. You do not have to post unless you want help understanding it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by cartesian on 2010-06-18
I don't have a separate partition for /home so it will be part of root.

I am not worried about preserving any settings at all I just want to overwrite what was there so that I can use it again.

Thanks for the help and the links.

---

