---
title: "How to add a Win7 raid0 install on GIGABYTE controller"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by JohnFante on 2011-02-13
I have a Win7 raid0 install on the Gigabyte controller on my x58-UD4p mobo. I think it is in reality a jmicron chip.

Ubuntu is placed on a SSD on the ICH10R controller set to AHCI. I have two other discs attached. A Linux data partition and a OSX hackintosh install.

The to discs that makes the raid0 install are on /dev/sdd and /dev/sde. 

Grub2 (with some errors) adds the following automatically:

```

}
menuentry "Windows 7 (loader) (on /dev/mapper/jmicron_GRAID)" {
	chainloader +1
}
```

But when I try to use it I get an error and the machine resets.

Any suggestions?

---

