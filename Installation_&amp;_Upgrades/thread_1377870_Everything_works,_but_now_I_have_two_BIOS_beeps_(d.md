---
title: "Everything works, but now I have two BIOS beeps (dualboot Win7 and Karmic)"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by SBloke on 2010-01-10
My machine is now dualbooting win7 x64 and Karmic x64. Not a problem in sight and everything works like a charm but I have one problem:

Ever since I installed Karmic my bios beeps twice. (Three times if I count a very soft long beep before the two distinct beeps) 
Consulted the error charts and it stated problems with my RAM. Suggested reseating them, swapping them round and running something like memtest.
Memtest didn't find anything wrong, and swapping and reseating didn't do a thing either. 

Other than the beepings I can't seem to find anything wrong, everything works and I don't seem to have any RAM problems.

Now I'd hate to blame Karmic for this but my BIOS only started doing this after it's installation. Does anyone have an idea? (Other than sending in my mobo to be replaced, it's only a few months old....)

---

### Post by SBloke on 2010-01-11
bump....

---

### Post by pricetech on 2010-01-11
What kind of computer ??  Is it a branded system or a "whitebox" ??

---

### Post by J V on 2010-01-11
linux likes to make noises like that...
fix:
```
echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by SBloke on 2010-01-12
AMD phenom x3 720
MSI 785GM-E65
4gb DDR3 RAM
ATI 4770

For some reason a few cycles through the BIOS and changing settings (and then back again after another reboot) solved the beeps. Very very strange

But now I have a new problem, which is Windows related xD

---

