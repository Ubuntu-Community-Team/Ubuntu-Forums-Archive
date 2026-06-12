---
title: "It stops mid set up"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by Rhemat on 2005-03-18
Hello, I am trying to set up your version of linux onto my computer.  Ther problem is that it always stops after I get passed select Language and Country.  The screen is either mostly blue with a grey line and cursor, or just grey with cursor.  I can type things in, but nothing responds.
  My computer is a 600mHz pentium 3 with 192mb of SDRAM.  It currently has SuSE 9.1 on it, and I don't have root password (my brother set it up and never gave me the password, and claims he forgot it now).  I ordered the Intel x86 or 86x.  Just thought that info might be of use.  

Thanks in advance.

-Brad

---

### Post by az on 2005-03-18
You ordered the cds?  Did you try the live cd?

I say this because this sounds like a bad cd problem.  If this is not the case, try the additional boot arguments in the F3 F4 F5 menus (acpi=off, for example)


Root access on Suse?  Change the boot arguments (Suse uses grub, I think) and add init=/bin/bash (Upon booting, you can edit your boot parameters in grub.)  This will boot and dropo you into a root prompt.

passwd root

If Your setup uses Lilo, you will have to use a live cd, or something and chroot into the system to change to root password.

---

### Post by MavKato on 2005-03-19
I have a similar problem, when it says "loading components of ubuntu installer, retrieving nic-extra-modules-2.6.8.1-3-386-di", it hangs at 34% and the screen starts flashing.  I have a Pentium Pro with 128 MB ram.  I have Win98 and SuSE linux installed, and want to replace SuSE with Ubuntu.

---

### Post by MavKato on 2005-03-19
I ran the utility to verify the disk integrity, and the CDs I ordered turned out to be bad

---

### Post by Rhemat on 2005-03-19
I am not good with computer programming, scripting, or commands for the start up prompt or any other spot.  If possible, could you give extremely specific steps for entering and changing the grub?
  Thank you for promptly responding though.

-Brad

---

### Post by Rhemat on 2005-03-23
I thank you all for the advice, and sorry for wasting your time.  It turns out that the problem was I had two keyboards plugged in.  The next step it never reached was "Select keyboard layout," and it was trying to decide which one to use, but couldn't.
  Now I had the two plugged in because my USB kb has a long cord, but I have to use my PS/2 kb for typing before the machine reaches the GUI.

  Once again thank you for your help.  Hopefully I won't have many more problems in the future. :oops: 

-Brad

---

