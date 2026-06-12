---
title: "dual boot upgrade"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by webbdawg on 2010-05-18
I have a sony vaio that dual boots (separate partitions) which is why I can still use my computer.

I went ahead an let 9.04 upgrade to 9.1 and something must have went wrong because I cannot boot to the KDE desktop.

I can boot to a command line. SO if anyone knows some majic words I can type to finish the install or figure it out that would be great.

What is odd is the Grub loader still says 9.04.

Thanks
Dave

---

### Post by zvacet on 2010-05-18
```
sudo dpkg --configure -a

sudo apt-get -f install
```

```
sudo apt-get update && sudo apt-get upgrade


sudo apt-get dist-upgrade
```

---

### Post by webbdawg on 2010-05-18
Do I do them in order after each finishes or do I pick one go with it??

---

### Post by zvacet on 2010-05-19
In order I typed them,and after every command hit enter.

---

