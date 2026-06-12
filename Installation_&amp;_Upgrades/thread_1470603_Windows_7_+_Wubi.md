---
title: "Windows 7 + Wubi"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by grndnl on 2010-05-03
I wanted to install the new ubuntu 10.04 while dual booting it with windows 7, so i went for the wubi. as soon as i start the wubi however, i get an error message "there is no disk in the drive. Please insert a disk into drive \device\harddisk1\DR1." I have no idea what that means, and that is making me think that I should not dual boot with windows 7. How can i solve this problem? And should i dual boot with 7? because i could not find it anywhere that it is compatible...
thanks in advance

---

### Post by buster on 2010-05-04
This might help:

"Found the reason here. Turns out because Wubi is a port to python in windows, it doesn't like many empty storage devices. They should really fix that.

[https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

My system has a lot of them having a card reader, extra fake optical drive because of daemon tools, etc. The workaround is to keep clicking continue repeatedly. I had to do it about 20 times or so and eventually it gives up and loads the installer. I ended up having to do it again during the install. It's grabbing the torrent sand saying 10 hours left now but I'm sure that'll pick up Cheesy"

You can see the whole thread here: 

[http://www.plugintolinux.ca/smf/index.php?topic=888.0](http://www.plugintolinux.ca/smf/index.php?topic=888.0)

---

### Post by grndnl on 2010-05-05
thanks alot

---

