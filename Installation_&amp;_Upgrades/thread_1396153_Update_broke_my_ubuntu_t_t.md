---
title: "Update broke my ubuntu t_t"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by dragonnutds on 2010-02-01
ubuntu told me it needed to update. when it finished it told me in order to finish, ubuntu wouldent load, it just gave me a comand line interface. please help...

---

### Post by wojox on 2010-02-01
Try rebooting again and hold down the left shift key and choose recovery-mode and see if it can fix any broken packages.

---

### Post by dragonnutds on 2010-02-01
> **wojox said:**
> Try rebooting again and hold down the left shift key and choose recovery-mode and see if it can fix any broken packages.

no luck, holding left shift still took me to the command line interface, here is some more info about it, it starts with... "minamul BASH-like editing is suported, press TAB to see..." and the command line part before the > has the word GRUB

---

### Post by wojox on 2010-02-01
If you just boot up normal can you login to the shell? If so run:

```
sudo apt-get install --fix-missing
```

Or

```
sudo apt-get -f install
```

Or does it bring you to the **grub>** each time?

---

### Post by rbolio on 2010-02-02
Ive got a similar problem..

grub shows no kernels, not even win7!

i get the choise, so i went to grub Bash (sh:grub>)

please help :S

---

