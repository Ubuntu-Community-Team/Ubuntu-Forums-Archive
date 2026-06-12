---
title: "mini ISO booting"
date: 2018-10-31
forum: Installation &amp; Upgrades
---

### Post by mechanic on 2018-10-31
Now how come the downloaded version of Xubuntu18.04 recognises the EFI setup properly and can boot in UEFI mode, whereas the mini iso tool will only boot in legacy, and installs a system in legacy rather than Uefi mode? What is going on?

---

### Post by oldfred on 2018-10-31
I know that was how it always was. Did not know if they yet updated it to include UEFI.

If you want a minimal with UEFI, install the server version. At end of install it asks what you want to install and you can select nothing or whatever your want.

       Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel
sudo apt install ubuntu-server
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by mechanic on 2018-11-01
Well its about time the responsible devs for the mini ISO woke up to the UEFI booting system we've had in place for nearly ten years. Maybe they need to go on a course. The other irritating factor is that the mini installer still ends up with north of 4GB of files in the installed system. Not much improvement on the full installer for Xubunto 18.04.1. Maybe there are just too  many dependencies listed on some packages (why install ruby to run vim?).

There seems a lot of problem reports and other traffic on this part of the Ubuntu forums these days - under-resourced at xubuntu?

Thanks for the hint to install the server edition, I think I'm going for the full edition and purging out some of the nonsense after a verified install.

---

