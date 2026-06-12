---
title: "How to remove this old SP?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by kyqinqiqin on 2010-01-20
Like this title.
When I updates available, it is disappear a new name to like "ubuntu 2.6.31.6-166.fc12.i386" and " ubuntu 2.6.31.5-127.fc12.i386". When I enter the ubuntu while my must select one. And I found my local-disc has added used byte when I after updates the 9.10.
I meaning is I hope I can made it more and more to smallest. Because I don't think to choose, and I think to release more and more the disc-space. 
And you can help me. Tell me how to do.
Thanks all for your help.

---

### Post by x33a on 2010-01-20
If you intend to remove the older kernel, take a look here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
```

Too Many Kernels? Kernels removed via Synaptic or with "apt-get remove" will automatically update grub.cfg and no user action is required.
[LIST]
[*]
[LIST]
[*]In Synaptic, type the kernel number in the search window at the upper right (for example - 2.6.28-11).
[*]Find the "linux-image" and "linux-headers" files for the applicable kernel (example - linux-image-2.6.26-11 or "linux-image-2.6.26-11-generic).
[*]Right click and select "Mark for Complete Removal" and then press the Apply main menu button.
[*]The kernels will be removed from your system and from the Grub menu.
[*] If you are not sure of the kernel you are currently using, in a terminal type "uname -r".
[*]Many users keep one previous kernel on the machine which previously ran without problems.
[/LIST]
 
[*]Other Operating Systems which have been removed from the computer will also be removed from the menu once "update-grub2" is run as root.
[*] To prevent one of the /etc/init.d files from running, remove the "executable" bit.
[LIST]
[*] Example: If you don't want to see the "Memtest86+" entries, run this command:
     Code:
     sudo chmod -x /etc/grub.d/20_memtest86+
[*]Run the update-grub command to allow the changes to be incorporated in grub.cfg
[/LIST]
 
[/LIST]


```

---

