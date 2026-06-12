---
title: "Linux-uvcvideo help??"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by cessusbangy on 2011-01-20
Hey all, I tried to reinstall my webcam drivers, as for some reason /dev/video0 got deleted?

I'm using this command from the forum archives:

[I][I]sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo cp -av /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae[/I][/I]
Although, it fails and says:
No repository found in 'svn://svn.berlios.de/linux-uvc/linux-uvc/trunk'

Any suggestions?

---

