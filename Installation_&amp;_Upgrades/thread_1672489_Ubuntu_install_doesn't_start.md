---
title: "Ubuntu install doesn't start"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by xnicodemusx on 2011-01-20
Hi

The problem that I have is that I tried when I booted from cd everything went well. the problem was when I selected to install ubuntu. whenever I select "install ubuntu" the program seems to start working but it never actually "starts". The monitor only turns black, yet the computer is still running. 

Please someone help me!

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums :)

What are the computer specifications?

We need to know about RAM and graphics card in particular.

Also, which version are you trying to install?

Do you also have other operating systems on the computer, if so what?

---

### Post by xnicodemusx on 2011-01-21
> **Rubi1200 said:**
> Hi and welcome to the forums :)

What are the computer specifications?

We need to know about RAM and graphics card in particular.

Also, which version are you trying to install?

Do you also have other operating systems on the computer, if so what?

My motherboard is a wolfdale 1333-D667.
Processor: Intel Pentium Dual Cpu E2180@ 2.00GHz 1.99GHz
RAM: 2.oo GB
Op syst: Windows 7 professional 32 bit. (previously windows xp professional)
Graphic card: nVIDIA GeForce 7300 LE

---

### Post by Rubi1200 on 2011-01-22
Sorry for the delayed response.

As the CD is booting, select language and try Ubuntu without changes.

Then press F6 to show the boot options and select nomodeset, then Enter to boot.

If all goes well you should be at the live desktop and you can then see if everything works before installing.

A word of caution: there are problems with the installer for 10.10 and it has been known to overwrite other operating systems.

Please choose the manual partitioning option.

If you need more help, let me know.

---

### Post by Rubi1200 on 2011-01-26
> **xnicodemusx said:**
> Hi

The problem that I have is that I tried when I booted from cd everything went well. the problem was when I selected to install ubuntu.

After installing Ubuntu on the first boot when the entry for Ubuntu is highlighted press "e" to edit.

Use the arrow keys to navigate and find the line that ends with quiet splash.

Type nomodeset after quiet splash and then "Ctrl" + "x" to boot.

Once you are at the desktop go to Applications > Accessories > Terminal and run this command:

```
gksudo gedit /etc/default/grub
```

In the file that opens there is a line like this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it to this:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Save and exit, then run this command:

```
sudo update-grub
```

This should take care of things for you as far as booting is concerned.

Let me know if it works or if you need help with anything else.

---

