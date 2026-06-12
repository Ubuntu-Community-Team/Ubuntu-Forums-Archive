---
title: "manually force checking root files"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by talon 2 on 2008-03-30
my system goes into a automatic force check during start up, but fails.Then says can not find bash: groups, bash:lesspipe, bash dircolors. Then says to force check manually. Any suggestion as what to do in this situation. This is kind of over my head.

---

### Post by Pumalite on 2008-03-30
Is this booting Windows?

---

### Post by talon 2 on 2008-03-30
no. I am trying to boot ubuntu 6.06

---

### Post by Pumalite on 2008-03-30
Try to boot it with Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Knoppix and Mint 4 come with a burner. I'm not sure Ubuntu Lice CD does.
The command:
sudo ckdsk /dev/xxx

---

