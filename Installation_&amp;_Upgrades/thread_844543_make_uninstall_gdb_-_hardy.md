---
title: "make uninstall gdb - hardy"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by glok_twen on 2008-06-29
hi. i just pretty much finished my hardy upgrade. i am having trouble getting the new version of gdb to run correctly. see i had used make install to build from source and install 6.7.1 in the previous version. so i searched on how to remove it and most places say you need to rely on the builder having implemented a "make uninstall" label in the Makefile. well it turns out they didn't do so with gdb 6.7.1 built from source.

so i just deleted the directories and the bin file.

but now when i type gdb, it still looks for the gdb bin in /usr/local/bin where it had put the 6.7.1 bin. (instead of in /usr/bin where the new 6.8 from hardy is). do you know how i tell it to stop looking for the old image? i didn't find a way with sudo update-alternatives, or looking in .bashrc/bash.bashrc.

thanks,
gt

---

### Post by kirilp on 2012-02-02
probably not the proper way of doing it but you can just move the executable from /usr/bin to /usr/local/bin 

sudo mv /usr/bin/gdb /usr/local/bin/

---

### Post by oldos2er on 2012-02-02
Closed, necromancy.

---

