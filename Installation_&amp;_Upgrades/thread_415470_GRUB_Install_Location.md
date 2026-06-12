---
title: "GRUB Install Location"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by babakan on 2007-04-20
I have seen questions like this posted , but answers conflict...

Installing 7.04 for AMD64.  I want GRUB installed to the beginning of the Linux Primary Partition, NOT THE MBR.

Will the 7.04 64 bit desktop version allow this or do I have to use the Alternate version?

---

### Post by heimo on 2007-04-20
> **babakan said:**
> 

Will the 7.04 64 bit desktop version allow this or do I have to use the Alternate version?

As far as I know, desktop versions don't ask where to put GRUB - I installed 32bit i386 version and it didn't. So, alternate version is a better bet.

---

### Post by Npl on 2007-04-20
the x86-LiveCD has a button with Advanced Options somewhere around the last Installation Pages. Atleast I found it when I selected to manually partition the drives

---

### Post by hetcxp on 2007-04-20
my question is a little bit diferent, in my desktop i'm not the only one how use it but i'm the only how works with linux, i'd like to know how do I put the windows xp option in the first position of the boot loader?

---

### Post by iminj on 2007-04-20
hetcxp:

I assume you want WinXP to be the default OS loaded by GRUB. Here's how I do it:

(1) Open terminal in ubuntu, and enter:

sudo gedit /boot/grub/menu.lst

(2) When the menu.list configuration opens, you'll see a field for default OS and a number beside it. Lower down in the file is a list of each OS on your system. The default counter starts counting each OS starting at 0, 1, 2, 3 ..... (NOT starting at 1 ... very important).

(3) Find the appropriate number for XP, and enter it in the default field. You also can change the time (in seconds) that GRUB waits for you to choose an OS before booting the default.

(3) SAVE the edited menu.lst file, and close out terminal. When you reboot, GRUB should now point to XP as the default Operating System.

Good luck !
iminj

---

