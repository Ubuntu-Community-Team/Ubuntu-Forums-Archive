---
title: "HP Pavilion a6750t Desktop won't load Ubuntu 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by tomreid on 2010-09-05
Hi

I tried to do a clean install of 10.04 on the above desktop. It was previously running 9.10 fine.

I booted with a 10.04 live CD, used Gparted to delete the previous partition that 9.10 was in. Installed 10.04 and chose the option to install in the largest continuous free disc space.

The installation seemed to go fine, but when I re-start the system, GRUB loads, I select Linux, then I get a flashing cursor and the monitor goes to sleep as it shows like it is getting no signal.

When I boot Vista on the same system it works fine.

From the sound of the hard drive, I am guessing that it is not loading the Ubuntu OS, I don't think this is a video driver problem.

cheers

---

### Post by sharathcshekhar on 2010-09-05
Looks like something has gone wrong with the installation. Anyways, can you try and log into recovery mood and post the boot up message?

---

### Post by tomreid on 2010-09-05
Hi

when I boot into recovery mode, there's a lot of text that runs up the screen. I took a picture when the text finished. The monitor then cuts out like it does when I try to boot it normally. 

Don't know if this text will be meaningful to you?

cheers

---

### Post by tomreid on 2010-09-07
anyone?

---

### Post by sharathcshekhar on 2010-09-10
The boot up message is very little and not very clear.. I am suspecting the boot time parameters though. In your Grub menu, if you press "e", it will go to the edit mode. Can you check if the parameters to the kernel, like the kernel version and rootfs are as you expected them to be?
Btw, youu can press 'Esc' to return to the Grun menu from the edit menu.

---

