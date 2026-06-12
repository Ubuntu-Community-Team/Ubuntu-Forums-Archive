---
title: "Ubuntu 15.10 fails to boot after installation"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by Raffael_Vogler on 2016-01-10
Hello!

There is not much to describe about the problem (no error messages as far as I can tell). Except for me having installed Ubuntu 15.10 64bit on my laptop and it fails to boot (black screen).

But for the context let me give you a couple of details:

Boot mode is set to "Legacy" in BIOS
I make a full fresh install - erase everything and start from scratch
Up until few hours ago my laptop was running Ubuntu 14.04 just fine
I also tried installing Linux Mint 17.3 and also run into boot issues
I install using disc encryption and LVM
I use the default partitioning - no configuring here
I intend to install Mint on my 64GB SSD (where also Ubuntu was running)
Next to the SSD I also use a 500GB HDD

Looking forward to some feedback on how to troubleshoot - obviously you need some hard facts - for that purpose I need some instructions on what commands you want me to run.

Kind Regards

Raffael

---

### Post by Raffael_Vogler on 2016-01-12
Fairly disappointing that nobody even tried to give some guidance here.

Anyway I also tried to install Linux Mint 17.3 which led to very similar symptoms. Thanks to forums.linuxmint.com I could resolve the issue and I strongly assume that the same will work for Ubuntu 15.10. Essentially the problem was a missing driver for my NVIDIA graphics card.

Here you go:

[http://forums.linuxmint.com/viewtopic.php?f=46&t=213657](http://forums.linuxmint.com/viewtopic.php?f=46&t=213657)

For what it's worth: Linux Mint and Cinnamon are awesome

---

