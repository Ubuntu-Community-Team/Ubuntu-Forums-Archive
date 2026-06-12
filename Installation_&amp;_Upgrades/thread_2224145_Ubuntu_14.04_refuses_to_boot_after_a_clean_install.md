---
title: "Ubuntu 14.04 refuses to boot after a clean installation"
date: 2014-05-14
forum: Installation &amp; Upgrades
---

### Post by dottore2 on 2014-05-14
Please help as I'm at my wits end and am ready to give up on Ubuntu altogether :/ 

I have a Toshiba c55-a-1m7 laptop onto which I've installed Ubuntu 14.04 in UEFI mode (CSM mode was giving me a MACHINE CHECK ERROR). Everything went fine with the installation but when I turn off the laptop and turn it back on, it says that I should insert a Boot Media or something similar even though I have the boot order set to HDD first.

I've done the boot-repair recommended repair and it didn't fix anything but instead gave me this output: [http://paste.ubuntu.com/7464628/](http://paste.ubuntu.com/7464628/)

I've tried doing the 
```

sudo mount /dev/sda2 /mnt
sudo grub-install (etc.)

```

routine but it gave me errors about GPT and blocklists.

Can anyone assess this and help me? Thanks!!!

---

### Post by oldfred on 2014-05-15
Similar to this?
[http://ubuntuforums.org/showthread.php?t=2224131](http://ubuntuforums.org/showthread.php?t=2224131)

  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

