---
title: "Grub2 set to 0 sec, how to bypass?"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by pedroso on 2011-04-27
I wanted to avoid the countdown in Grub, so I set it to 0 sec.

It worked all to well - it is 0 sec. Which means that I now boot directly into my default system, which is Windows. 

How do I get back to the Grub menu, or just into Ubuntu so I can reset the countdown?

I have tried pressing all sorts of keys, including the left Shift key and Escape. Nothing works.

Do I really have to reinstall Grub??? If I do, can I use the version from my Ubuntu 10.10 installation disk, even if I am running 11.04? The reason is that I have no cd burner program in Windows, and no administrative rights to install one.

---

### Post by shwallace on 2011-04-27
boot from a Linux cd and reset your grub menu to the default.

---

### Post by lmarmisa on 2011-04-27
Open up a terminal and type this command:

```

sudo gedit /etc/default/grub

```

Then modify parameter GRUB_TIMEOUT:

```

GRUB_TIMEOUT=5

```

Save and exit.

Finally type this command:

```

sudo update-grub

```

---

### Post by pedroso on 2011-04-27
Thanks, that worked. I had to search a little to find grub.cfg, but it was easy enough.

---

### Post by dino99 on 2011-04-27
dont tweak grub.cfg

sudo gedit /etc/default/grub

then 
sudo update-grub

---

