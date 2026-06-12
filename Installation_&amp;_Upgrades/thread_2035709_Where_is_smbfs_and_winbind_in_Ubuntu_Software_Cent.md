---
title: "Where is smbfs and winbind in Ubuntu Software Center"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by silverrope on 2012-07-31
Yesterday, I installed 12.04 on my Thinkpad A20m. In order to access Windows shares using hostnames, I installed smbfs, samba, and winbind using Ubuntu Software Center. Everything worked, but somehow I messed my system while doing some other maintenance tasks. So I reinstalled 12.04 from scratch again today. However, when I tried looking for smbfs and winbind using the Software Center, I could no longer find them! I then installed synaptic package manager and the two packages were found and installed.

Questions:
What happened to smbfs and winbind in the Software Center?
What are the differences between Software Center and synaptic and why is there a difference in the listing of packages?
Which package manager is preferable?

Thanks for any advice.

---

### Post by dino99 on 2012-07-31
winbind is into the archive, but smbfs is replaced by libpam for security reasons (and has been removed from archives way back).

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

[http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu](http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu)

synaptic : old & strong tool still very usefull even if its not installed by default now (as canonical has made the choice to build & install rooky tools)

---

### Post by silverrope on 2012-08-01
OK,thanks. For some reason, the two packages have reappeared in the Software Center so it is either something I did wrong or something transient on the server side.

I think I will stick with synaptic from now on!

---

