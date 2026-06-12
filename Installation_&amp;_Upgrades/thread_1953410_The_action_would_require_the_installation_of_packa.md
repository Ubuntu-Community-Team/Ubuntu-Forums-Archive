---
title: "The action would require the installation of packages from not authenticated sources"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by veggiefish on 2012-04-06
I have already tried all the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=1626757](http://ubuntuforums.org/showthread.php?t=1626757)

But my problem persists.

Has anyone else had this issue? In "details" of the error:

apport-hooks-medibuntu libavcodec-extra-53 libavutil-extra-51

---

### Post by dino99 on 2012-04-06
medibuntu is not needed now (dont have it on Precise at all)

---

### Post by oldos2er on 2012-04-06
Run ```
sudo apt-get install medibuntu-keyring && sudo apt-get update
``` to install Medibuntu's gpg key.

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by veggiefish on 2012-04-07
Thank you- adding the keyring worked. :)

---

