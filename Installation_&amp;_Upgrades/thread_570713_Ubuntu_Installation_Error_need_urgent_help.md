---
title: "Ubuntu Installation Error need urgent help"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Sri123 on 2007-10-08
Hi,

Am trying to install Ubuntu from a Live CD i had used this cd on a different comp. so the CD is good...

The following error message gets displayed...

===================================================
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
Loading, please wait....
===================================================

After sometime Ubuntu logo gets displayed and they nothing seems to happen....

Pl. help me....


Sri

---

### Post by wpshooter on 2007-10-08
Have you checked to make sure that you have the latest version of the BIOS that is **available** is installed on the computer ?

---

### Post by shad0w_walker on 2007-10-08
When you boot with the LiveCD in, wait for the menu to come up and press F8 (I believe) and you get a long text box appear at the bottom of the screen. At the end of the text in this box add in this:

```
acpi=force
```

When you have added the text, press enter to start booting.

This will tell the kernel to continue loading and ignore the error (It doesn't look to be a serious error)

---

### Post by wpshooter on 2007-10-08
My **FIRST** choice for fixing this problem would be to attempt to update the BIOS if possible BUT they may not be able to if the computer is fairly old.  Then I would fall back to the ACPI=FORCE.

---

### Post by shad0w_walker on 2007-10-08
I only suggested forcing the ACPI setting as most motherboards/bioses require a custom application to perform the update (Normally a windows only application) and that might not be possible in this case.

---

### Post by Sri123 on 2007-10-08
1. The BIOS is a old version i think i dont how to update it....
2. about the  ACPI=force after the f6 button give the boot log : i had tried it did not work...

Please help me

---

### Post by wpshooter on 2007-10-08
> **Sri123 said:**
> 1. The BIOS is a old version i think i dont how to update it....
2. about the  ACPI=force after the f6 button give the boot log : i had tried it did not work...

Please help me

The computer or motherboard manual should give you some fairly detailed instructions on updating the BIOS.

If you can give the exact Computer brand and model number or the exact brand and model number of the motherboard, we can have a look on the web to see if there might be an undate available.

---

