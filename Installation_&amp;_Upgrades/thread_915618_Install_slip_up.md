---
title: "Install slip up"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Vinni3 on 2008-09-10
(I ordered my CD from Ship It) When I tried to install Kubuntu on my desktop, the CD turned out to be defective - but it already installed GRUB; I was thinking of creating a dualboot with Vista. I booted up the machine, it displays 'GRUB' after I had overwritten the mbr. Have you got some ideas to allow me to get rid of GRUB, and let me boot normally.

---

### Post by Partyboi2 on 2008-09-10
You can use [[COLOR=Blue]supergrub[/COLOR]]("http://supergrub.forjamari.linex.org/?section=download#more") to remove grub, or if you have the vista disk you can boot it and choose "repair" then when you get to the prompt type
```
Bootrec /FixMBR
``` then ```
exit
```

---

