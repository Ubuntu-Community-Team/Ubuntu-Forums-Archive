---
title: "Using fglrx leaves system unbootable (ATI  Mobility Radeon HD 3650)"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Brimjob on 2009-10-23
Hey all,

Did a clean install of the Karmic RC and installed the restricted fglrx driver for my HD 3650 using the System>Administration>Hardware Manager, and after rebooting when prompted by the installer I boot to nothing but a black screen.

To make sure it wasn't a fluke, I reinstalled Karmic and tried again with the same result. Same hardware set up gave me no trouble in Jaunty.

Has anyone else experienced this/any ideas for how to fix it?

---

### Post by TrueJournals on 2009-10-23
You'll need to boot into recovery mode and run the following two commands:
```
aticonfig --initial
aticonfig --acpi-servces=off
```

It should boot fine after that...  You might need to play with xorg.conf before aticonfig --initial will run.

---

### Post by momo971 on 2009-10-23
> **Brimjob said:**
> Hey all,

Did a clean install of the Karmic RC and installed the restricted fglrx driver for my HD 3650 using the System>Administration>Hardware Manager, and after rebooting when prompted by the installer I boot to nothing but a black screen.

To make sure it wasn't a fluke, I reinstalled Karmic and tried again with the same result. Same hardware set up gave me no trouble in Jaunty.

Has anyone else experienced this/any ideas for how to fix it?

Hello, 
Have you generated a xorg.conf file for the fglrx driver ?

```
sudo aticonfig --initial -f
```

---

### Post by Brimjob on 2009-10-25
Worked brilliantly, thanks guys!

---

### Post by markbuntu on 2009-10-25
It really surprises me that after all this time the package maintainers still neglect this critical step to getting fglrx operational.

---

