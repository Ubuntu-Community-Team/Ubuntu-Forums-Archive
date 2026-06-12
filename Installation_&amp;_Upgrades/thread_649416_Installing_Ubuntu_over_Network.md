---
title: "Installing Ubuntu over Network"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by unrlmth on 2007-12-24
I'm trying  to install ubuntu on my ppc iBook over a wired ethernet connection.  I have the disk image on my other computer, but don't have any CDs to burn it to.  I'm also on a dial-up connection so I would like to avoid downloading stuff.  Anyone have any suggestions for how to do this?  

Thanks, Ben.

---

### Post by K.Mandla on 2007-12-24
You could ...

[LIST=1]
[*]Copy the ISO onto a separate partition on the host machine, and tell Grub to boot to it. From there you should be able to install to a different partition.
[*]Read the [localnet installation method in the wiki]("https://help.ubuntu.com/community/Installation/LocalNet"), which I tried once a long long time ago when I was very green and didn't have much luck with. However, I blame that on my noobness.
[*]Pull the hard drive, install on a different machine, replace the hard drive and reconfigure.
[/LIST]
Are any of those options? By the way, I don't know if [this]("https://help.ubuntu.com/community/Installation/WithFloppies") would be an idea either.

---

