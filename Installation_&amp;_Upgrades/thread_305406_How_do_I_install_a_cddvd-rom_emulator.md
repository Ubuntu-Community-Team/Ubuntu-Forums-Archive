---
title: "How do I install a cd/dvd-rom emulator?"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by xenoalien on 2006-11-23
How do I install a cd/dvd-rom emulator?

---

### Post by streeto on 2006-11-23
If I am understandig you right, you have a .ISO file, and want it mounted.

sudo mkdir /mnt/image
sudo mount file.iso -o loop /mnt/image

Sorry, I don't know any graphical tool for this sort of thing.

Hope this help.

---

### Post by xenoalien on 2006-11-23
Okay, how would I type it into the terminal if the directory was:
/home/me/Desktop/Doom 3 Linux

And the image was
doom3-CD1.iso

---

### Post by streeto on 2006-11-23
sudo mkdir /mnt/image
sudo mount '/home/me/Desktop/Doom 3 Linux/doom3-CD1.iso' -o loop /mnt/image

Then access /mnt/image in your favorite file manager.

Just a note. If you are willing to use shell commands, I recommend you not to use spaces at file names. This avoids the need of quotes (') aroud them.

---

