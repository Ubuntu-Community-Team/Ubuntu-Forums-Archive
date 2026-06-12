---
title: "Permission problems after upgrade 13.04 -&gt; 13.10"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by arnd-scheel on 2013-11-10
After upgrade, I am having difficulties with the panel in kubuntu. I suspect they're all related, having to do with some permission problem. 

1)When I insert SD card or USB device, panel detects and offers to open, but then fails, "lacking permissions"
2)When I get a notification of system updates, everything works fine with update manager in the panel until I actually initiate the update, at which point I get the message "lacking permissions". 

Both of those can be fixed with tedious workarounds, like mounting via sudo su dolphin... Or updating via synaptic. Have not found a workaround for :

3)Networking: when I open connection editor, the list of connections is empty. I can add a connection but the connection is immediately forgotten. I can in fact not add new networks. Clicking on a wireless network that is detected, will not actually initiate a connection. 

Any suggestions where I should look? I've been using Kubuntu for a while, without digging into it much, though. 

Help is appreciated

---

### Post by deadflowr on 2013-11-10
Post the output for
```
id username
```
replace username with your username.

This will show the list of groups you belong to.
Not being able to do several of the things you've listed makes it seem like you've lost a few groups.

---

### Post by arnd-scheel on 2013-11-10
id scheeluid=1000(scheel) gid=1000(scheel) groups=1000(scheel),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(sambashare)

---

### Post by deadflowr on 2013-11-10
The good news is you didn't lose any groups.

But then that means something else broke:confused:

You could try making a new user to test and see if the problems are system-wide( for all users) or if it is isolated to the current user.

---

