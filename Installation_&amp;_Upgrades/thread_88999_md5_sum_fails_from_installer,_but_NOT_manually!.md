---
title: "md5 sum fails from installer, but NOT manually!"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by blazko on 2005-11-11
Hi,

So I want to install Breezy on my new AMD64, but it fails on checksumming the instaler files on CD, e.g. pool/main/l/linux-source-2.6.12/md_modules.......udeb and so on. It says that this file has a wrong MD5 checksum. So, I checked this very file manually on the same computer: sum okay!
Then I checked the entire CD on another computer an did a complete CD checksum using the rawread script I found here in these forums.

Badly, there is no boot option to disable MD5 (cos I think that the files are okay...). Any hints? I really want to install, waiting for months for my new sys...


Greetings and thanks,
Timo

---

### Post by blazko on 2005-11-11
Hey back,

Damn, this was annoying: it was the DVD drive! After checking manually MD5 against files that debootstrap complained, after the 100th check I finally got a much better hint from the system: i/o error! Before I tried with an older but guaranteed working Hoary 32bit CD, the system had similar errors - so it must be the hardware.

So it was pure luck, because the error was never replorducable with checking a faild file again manually...

What I did was to replace the DVD drive with a four years old one believed to be quite broken. However, it allows me to install!!!!!!!! FINALLY! :-)

Does one have an idea what might be the proble mwith the brandnew DVD writer? It is a BenQ dual layer burner with IDE. It came with no manual, stickers or imprints near the jumper fields, so may be a jumper setting the reason? You have to know that it does not share with any other devices; it is the only IDE drive, the other is a SATA one and I plugged the IDE burner to IDE Port 2 as master.

Thanks and regards,
Timo

---

