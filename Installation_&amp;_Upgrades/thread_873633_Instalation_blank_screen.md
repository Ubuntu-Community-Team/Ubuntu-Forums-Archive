---
title: "Instalation blank screen"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by chejose on 2008-07-29
I recently bought a HP 2133 which I like very much. But it comes loaded with SUSE which I don't like at all! It seems to be a limited edition made to look like Windows. It lacks commands like apt-get and lspci... in fact I have found no way to add programs.

But the problem: I have the live CD (Ubuntu) installed on a memory stick (there is no CD drive), and booted the HP with it. Everything seemed normal, but towards the end I get a blank screen and it stays that way (tan color). I checked the stick on my work computer and it is OK.

Would there be some kind of workaround for that? The video card is VIA Chrome 9 HC 1Gp.

Thanks for any suggestions,

José

---

### Post by jtappin on 2008-07-29
There's a very useful installation guide at: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") which covers many of the issues associated with the HP2133.

The key thing here is when booting off the CD/DVD select the "Boot options" (F6) and add the xforcevesa option to the boot line.

A couple of issues with the video drivers are not that clear in the Wiki page linked above:

1) To get hardware acceleration with the drivers from VIA you need to use the original Hardy kernel 2.6.24-16 not the current -19 and -20 versions.
2) The openchrome packages in Hardy do not recognize the video card -- you do need the current subversion tree.

If you are using ALSA 1.0.17 (as opposed to RC3), some users have reported problems with building or installing.  These can be avoided by using 
```

./configure --with-cards=hda-intel

```
which will also save on compilation time

---

### Post by chejose on 2008-07-29
Very good and many thanks. At least I have something to work on now. Hopefully I will not have to come back to this.

José

---

