---
title: "Install Problems!!!! Help Please!!!"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by gurumac on 2006-04-06
Does anyone know what this message means?

E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

I keep getting it everytime I download trying to install anything.

Any assiatance would be greatly appreciated.

Thanks in advance 

Regards,

---

### Post by linear on 2006-04-06
Yes, I've seen this. There is a missing dependency in the LilyPond package. If I recall correctly, you need tetex-bin.

---

### Post by taurus on 2006-04-06
Try removing it from your system and see if apt-get will run again!
```

sudo rm "/var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb"
sudo apt-get update
sudo apt-get upgrade

```

---

