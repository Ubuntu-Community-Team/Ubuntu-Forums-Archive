---
title: "Minor fglrx issue: boot splash and tty framebuffer resolution"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hojjan on 2010-04-22
So it seems that when I install fglrx, my boot splash and framebuffer tty default into 640x480, as opposed to the native resolution of my monitor which was the case with the default radeonhd drivers.

Any ideas on how to mend or change this?

---

### Post by BrokeMahPC on 2010-04-22
As far as I know that's how it is for the time being with fglrx. It's known as "ugly plymouth" in these parts. Look at the "What's up with Plymouth" thread, it's long! Search this forum for Plymouth.
There is a fix detailed at the bottom of:
```
gedit /usr/share/doc/plymouth/README.Debian
```
As it explains this can cause suspend/resume issues if you use that. The alternative is to see if the radeon or radeon HD open source drivers work for you but that isn't easy and there are bugs due to KMS on certain cards particularly Radeon HD.

Some have solved those by booting Grub with the "nomodeset" option.

IMHO wait and put up with it until it's fixed - as long as the main part of the OS works what does the splash matter? It's a little disappointing - I agree.

---

