---
title: "Ubuntu won't install on Core 2 Duo at all."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by eran- on 2006-10-27
I've encountered this same problem as mentioned in [here]("http://www.ubuntuforums.org/showthread.php?t=285683"):-?
Except the X does not freeze for me. 

Though, my Ubuntu is able to do even better than previous attempts of installation on IC2D-platforms: Ubuntu Dapper Drake won't even boot up from the CD, as it freezed when loading kernel. ](*,) 

Edgy Eft managed to boot itself without problems and installed successfully. But problems revealed themselves after installation.
Edgy Eft freezes completely when I choose to load it from GRUB menu with following error which I wrote down:

```

Starting up...
[17179572.944000] PCI: JMB36x: Enabling dual function on 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 0 of devices 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 1 of devices 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 2 of devices 0000:02:00.0
[17179572.964000] PCI: Cannot allocate resource region 3 of devices 0000:02:00.0
[17179572.964000] PCI: Error while updating region 0000:02:00.0/0 (0000b000 != 00000000)

[17179572.964000] PCI: Error while updating region 0000:02:00.0/2 (0000b000 != 00000000)

```

After various reboots I noticed, that the six-digit number in the beginning (17179572.xxxxxx) is different in each reboot. I'm not sure if it is important information, but just to mention it...

Platform:
MSI Neo-F P965
Intel Core 2 Duo E6400
Club3D nVIdia GeForce 7950GT 512mb
Corsair 1024 DDR2

I surely hope this is a problem to be fixed...! Ubuntu is my favourite distribution and I've got my count on it. :)

---

### Post by the kaz on 2006-10-30
> **eran- said:**
> Edgy Eft managed to boot itself without problems and installed successfully. But problems revealed themselves after installation.
Edgy Eft freezes completely when I choose to load it from GRUB menu with following error which I wrote down:
```

Starting up...
[17179572.944000] PCI: JMB36x: Enabling dual function on 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 0 of devices 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 1 of devices 0000:02:00.0
[17179572.960000] PCI: Cannot allocate resource region 2 of devices 0000:02:00.0
[17179572.964000] PCI: Cannot allocate resource region 3 of devices 0000:02:00.0
[17179572.964000] PCI: Error while updating region 0000:02:00.0/0 (0000b000 != 00000000)
[17179572.964000] PCI: Error while updating region 0000:02:00.0/2 (0000b000 != 00000000)

```

Have you tried disabling USB legacy support (for both keyboard and mouse, if there can be set independently from each other) in the MSI BIOS? I don't have a MSI mainboard, but on several different P965 boards, including mine, this seemed to do the trick to get past the JMicron error messages shown above. 

If you can get the system to boot that way, it'd be nice if you could check whether to get any random system freezes (as described in [this]("http://www.ubuntuforums.org/showthread.php?t=285683") topic). 

Greetings, kaz.

---

