---
title: "Removing Dual Boot"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by pabu on 2010-03-01
I am giving a computer away that I had ubunto loaded on with XP. The new owner did not want ubunto so I unistalled it but the dual boot option is still there. How do I remove the dual boot option with ubunto gone?

---

### Post by pastalavista on 2010-03-01
You'll need to boot a Windows CD or a restore partition and fixboot.

---

### Post by presence1960 on 2010-03-01
> **pabu said:**
> I am giving a computer away that I had ubunto loaded on with XP. The new owner did not want ubunto so I unistalled it but the dual boot option is still there. How do I remove the dual boot option with ubunto gone?

you must have had ubuntu installed via wubi, correct? If not you would get a grub error rather than a dual boot option. Boot into windows. Go Control Panel> System. Click the Advanced tab. Choose Startup and recovery options. Click the Edit button. this will bring up boot.ini in Notepad. Be very careful here! Remove ***_only the reference to wubi(ubuntu)_*** close the file and reboot. The machine should go right to windows without the dual boot option.

---

