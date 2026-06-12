---
title: "After fresh install"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by agronk on 2007-04-05
Hello, sorry for my english first
 I`m new on linux but not with Pc 
I have this configuration
Asus P5B deluxe 965
Intel 6300
2x512 DDRII 800mhz kingston
MSI Radeon 1950 XT
After a suksesful install when I restart I get this message>
Grub Loading, please wait
Error 21

and it hangs there
Best regards 
Agron:confused:

---

### Post by rsambuca on 2007-04-05
The grub error 21 means that it is looking for a drive that isn't there.  Often this is just due to bios issues.   Do you have more than one hard drive?  If so, check the order of the drives in the bios.

---

### Post by agronk on 2007-04-05
For now I have just one HDD and that is not sata but IDE Maxtor 80Gb

---

### Post by rsambuca on 2007-04-06
I think you should just try re-installing grub from the live CD.  If you boot from the live CD, enter a terminal (Applications -> Accessories -> Terminal)

Then enter ```
sudo grub-install
```

---

