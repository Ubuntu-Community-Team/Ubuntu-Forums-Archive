---
title: "After Upgrade, Won't login"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-05-29
Alright i updated recently, and i installed Virtualbox (through Synaptic because i had a slight problem in Add and remove problems) and i restarted and it booted up perfectly but when i logged in, it would show my screen then just for no reason go back to the log in screen. i tried the failsafe Gnome and it had no top or bottom bars, i was able to run the synaptic though command line and removed virtualbox and rebooted but nothing changed.

---

### Post by iaculallad on 2008-05-29
> **melenor said:**
> Alright i updated recently, and i installed Virtualbox (through Synaptic because i had a slight problem in Add and remove problems) and i restarted and it booted up perfectly but when i logged in, it would show my screen then just for no reason go back to the log in screen. i tried the failsafe Gnome and it had no top or bottom bars, i was able to run the synaptic though command line and removed virtualbox and rebooted but nothing changed.

What about purging and reinstalling your gdm?

Purge:

```
sudo apt-get remove --purge gdm
```

Reinstall:

```
sudo apt-get install gdm
```

---

### Post by melenor on 2008-05-29
alright i will try that i will also try to boot with a different kernal.

Different Kernal the other didn't i did an uninstall of the new kernal then re-install it and it worked.

---

