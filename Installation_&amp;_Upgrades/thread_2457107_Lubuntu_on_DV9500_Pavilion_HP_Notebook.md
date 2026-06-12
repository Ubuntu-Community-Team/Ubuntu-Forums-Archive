---
title: "Lubuntu on DV9500 Pavilion HP Notebook"
date: 2021-01-26
forum: Installation &amp; Upgrades
---

### Post by novawaves on 2021-01-26
Hi

i want to install lubuntu on my notebook. but after i start from de usb stick i got an APCI Error and nothing starts.

i find in the net some knowledge wich say  i should do 

pci=nommconf
modprobe.blacklist=nouveau

as startup kernel option

after that it starts until the blue lubuntu screen check the filesystem

after that it takes a long time and nothing happens

can anyone please tell me whats the probel with this notebook is?

why i got a APCI error

---

### Post by ActionParsnip on 2021-01-26
Try the boot option
```

noapci

```
Make sure you have the latest BIOS (if possible)

---

### Post by novawaves on 2021-01-27
Not working

---

### Post by CelticWarrior on 2021-01-27
it's "acpi", not "apci", therefore the option to try is "noacpi".

---

