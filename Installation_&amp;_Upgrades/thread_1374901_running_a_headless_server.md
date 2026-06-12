---
title: "running a headless server"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by lunatech on 2010-01-07
This is for someone who needs to run a headless (i.e. no monitor) box
for their needs.  After making these changes, you can disconnect your
monitor from your server and put the server in a corner.  This post
does not cover how to do an Ubuntu install without any monitor.

[LIST]
[*] You will need to disable the GDM.  To disable your GDM, open file /etc/X11/default-display-manager in an editor and remove any entries in that file.  
[*] Open /etc/default/grub and change the option GRUB_CMDLINE_LINUX_DEFAULT in that file to ```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
``` .  After doing this change, run ```
sudo update-grub
```. This change is required to work around this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474930]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474930")
[/LIST]


I am running this setup on my home server which acts as a file server.

---

### Post by Mighty_Joe on 2010-01-07
Or install Ubuntu Server. . .

---

