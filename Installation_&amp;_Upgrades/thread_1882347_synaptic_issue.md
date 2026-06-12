---
title: "synaptic issue"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by Einstein86 on 2011-11-17
After installation Ubuntu 11.04 I've tried to reinstall some applications from Synaptic. I got only 'Remove' and 'Completely Remove' options. Does anyone know why is that and can I somehow turn on and the other options?

[[COLOR=#d40000]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075"), it works. thanks mate :)

---

### Post by mörgæs on 2011-11-17
If you boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

and try again, what happens?

---

### Post by subehsharma on 2011-11-17
As a workaround, do "remove" and not "completely remove" as the latter will even erase the .deb file of the app. If you just use "remove" and then install it then no new files frm internet gets downloaded.

---

### Post by mörgæs on 2011-11-17
Another difference is that the normal remove keeps user settings. If original poster wants a complete reinstall, these settings should also be erased (that is, with 'completely remove').

---

### Post by oldos2er on 2011-11-17
> **subehsharma said:**
> As a workaround, do "remove" and not "completely remove" as the latter will even erase the .deb file of the app. 

No it won't. 'Completely remove' removes any system configuration files, it doesn't touch the APT cache.

---

### Post by Einstein86 on 2011-11-21
thanks mate. it's work as you say

---

### Post by mörgæs on 2011-11-21
You're welcome :-)

---

