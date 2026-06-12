---
title: "[Ubuntu 10.10/Unity 2D] Security Updates not installing"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by WolvenSpectre on 2011-01-26
I am a casual user and I have a dual boot 10.04/10.10 machine and I have installed Unity 2D on the 10.10 install. I have been using 10.04 as my main so it has been a fair while since I logged into my 10.10 install. I went straight to updates and try to install them.

The 80+ updates won't install because it says I am trying to install from an insecure source (metacity/yadda yadda/and so on, I tried to copy it but it wouldn't work). I have tried changing my source server from Canada to Main and activating Canonical Partner Sources.

Nothing works. There is no "Install anyway, if it goes wrong its my own fool fault" option.

Am I out of luck and have to reinstall or can you guys help me?

---

### Post by gordintoronto on 2011-01-26
The "yadda yadda" is significant....

---

### Post by WolvenSpectre on 2011-01-28
Tarnation... I hoped it was a known issue....

Luckily the source that couldn't be copied could be cut then pasted into the text editor (Yay for kludge work arounds!:P) and this time it was slightly different and the source mentions Unity 2D right in it where last time it didn't.

libmetacity-private0 libqtbamf1 libqtdee1 libqtgconf1 libuqpanel0 metacity metacity-common unity-2d-default-settings unity-2d-launcher unity-2d-panel unity-2d-places unity-2d-spread unity-qt-default-settings unity-qt-launcher unity-qt-panel unity-qt-places unity-qt-spread

It tries to install, fails and resets again.

---

