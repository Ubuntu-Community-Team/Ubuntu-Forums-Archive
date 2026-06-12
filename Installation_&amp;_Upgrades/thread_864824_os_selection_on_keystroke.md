---
title: "os selection on keystroke?"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by addison3 on 2008-07-20
Is it possible to set grub to automatically boot into a specific OS, and to only show a list of operating systems to boot into if a certain key is pressed (say, F6, for example)? I want other users using my computer to be booted into a specified OS on startup without being confused by an OS selection screen, but I want to be able to see the OS selection screen and choose to boot into my other OS if I press a keystroke. Can grub make this happen?

---

### Post by Partyboi2 on 2008-07-20
You can change the "default   0" value in your /boot/grub/menu.lst to boot into the operating system of your choice. See [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc") how to do it. If you get stuck post your grub menu.lst
```
cat /boot/grub/menu.lst
```You should also be able to use the "hiddenmenu" option to boot straight into the operating system you have setup as default without seeing the grub menu at boot (unless you press esc)
See [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

---

### Post by addison3 on 2008-07-20
> **Partyboi2 said:**
> You should also be able to use the "hiddenmenu" option to boot straight into the operating system you have setup as default without seeing the grub menu at boot (unless you press esc)
See [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")

That sounds exactly like what I want to do, thanks!

---

