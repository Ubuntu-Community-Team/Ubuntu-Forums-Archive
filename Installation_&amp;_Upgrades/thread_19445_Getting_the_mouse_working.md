---
title: "Getting the mouse working"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by Simon211065 on 2005-03-11
I've managed to copy imwheel onto floppy via XP but can someone please tell me how I copy the files from floppy over to Ubuntu so I can use the command - 'sudo apt-get install imwheel' ?

---

### Post by az on 2005-03-11
sudo mount /dev/fd0 /media/floppy
dpkg -i /media/floppy/*.deb
sudo apt-get -f install (if neccessary)

---

### Post by Simon211065 on 2005-03-11
I can mount the floppy ok but when I type in dpkg -i /media/floppy/*.deb it says it doesn't recognise the file. So I'm stuck. I've got the unzipped imwheel file sitting on the floppy, the device is mounted - how do I get this file onto the system so I can use the apt get install command or install directly from the floppy? Very frustrating! I need some help please?

---

