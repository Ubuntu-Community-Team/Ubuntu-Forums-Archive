---
title: "i686 upgrades available?"
date: 2021-10-30
forum: Installation &amp; Upgrades
---

### Post by justpoppingin on 2021-10-30
Ubuntu's software updater is currently telling me

> 
[B]Sorry, there are no more upgrades for this system
[/B]
There will not be any further Ubuntu releases for this system's 'i386' architecture.

Updates for Ubuntu 18.04 will continue until 2023-04-26.

If you reinstall Ubuntu from ubuntu.com/download, future upgrades will be available.


This is on a 10-year-old laptop.  If I do `lscpu`, I get

```
Architecture:        i686

```

I've been looking around and I *think* I've learned that this is a 32-bit processor and I won't, in fact, find a new Ubuntu download that will work for it (e.g. [this thread]("https://ubuntuforums.org/showthread.php?t=2249133")).  Have I got that right?  I'd rather not learn the hard way by trying to install the wrong thing!

---

### Post by deadflowr on 2021-10-30
Architecture relates to the system in use.
Look at CPU op-mode(s)

As far as the statement reads, from it's perspective if you download and reinstall a fresh Ubuntu then it would have to be 64-bit and therefor will get upgrades into the future.

Also, what release is it?

---

### Post by justpoppingin on 2021-10-30
Thanks deadflowr, I have

```
CPU op-mode(s):      32-bit, 64-bit
``` and the current installation is Ubuntu 18.04.6 LTS.

---

### Post by deadflowr on 2021-10-30
So your machine is 64-bit capable.
You should check if the machine meets the minimum requirements to run Ubuntu Desktop.
(Generally the minimums are 4GB of RAM and a CPU which is dual-core or better and can run above 2GHZ) 

But I wouldn't fret about that as you can simply try a different desktop flavor if Ubuntu is too taxing.
(Ubuntu Desktop is fairly resource heavy whereas flavors like Xubuntu or UbuntuMate are lighter, or can be configured to run lighter)

---

### Post by justpoppingin on 2021-10-30
It also tells me

```
Model name:          Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
```

which [apparently is 64-bit]("https://www.intel.co.uk/content/www/uk/en/products/sku/52220/intel-core-i32310m-processor-3m-cache-2-10-ghz/specifications.html") so I guess I'll be OK?

---

### Post by justpoppingin on 2021-10-30
Thanks again deadflowr.  My "About" page tells me I have 3.8GiB memory, so it looks like the next LTS should work OK.

Very glad I asked!

---

### Post by grahammechanical on 2021-10-30
Do you have Wine installed or any other application that uses 32 bit libraries? The warning could be referring to 32 bit libraries. Another possibility is that some motherboards had a 64 bit CPU but a 32 bit UEFI chip. And I think that required 32 bit code in the boot loader (Grub). Just guessing on this one.

[https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)

Regards

---

### Post by MAFoElffen on 2021-10-31
> **grahammechanical said:**
> Do you have Wine installed or any other application that uses 32 bit libraries? The warning could be referring to 32 bit libraries. Another possibility is that some motherboards had a 64 bit CPU but a 32 bit UEFI chip. And I think that required 32 bit code in the boot loader (Grub). Just guessing on this one.

[https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)

Regards
32bit UEFI does not matter (yet). I have an old MacBook that I run 20.04.3 LTS on to test confirmation of my projects scripts on that hardware... It has 32bit UEFI and 64bit CPU. 

It has no related 32bit warnings on anything. grub-efi-<arch>-signed takes care of that in the 64bit package for both architectures of EFI BIOS'es. Sideline disclaimer to that, is that when it is 32bit UEFI, it creates the 32bit UEFI file, and the 64bit UEFI file(?), which the 64bit UEFI file obviously does not work, so has an extra, non-working Grub menu entry for Ubuntu. (just FYI)

---

