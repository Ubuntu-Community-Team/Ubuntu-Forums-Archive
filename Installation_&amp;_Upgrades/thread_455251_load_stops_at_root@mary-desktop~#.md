---
title: "load stops at root@mary-desktop~#"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by mschoen7 on 2007-05-26
Hello -

I'm a brand new Linux person with what I hope is an easy question.  I've installed Ubuntu on a separate hdd on a Presario S4000NX.  The install went fine, but it won't fully boot afterward.  Doing the recovery startup, the load stops at "root@mary-desktop~@".  It's obviously waiting for a command (since the password doesn't work), but I have no idea what that might be.  

Any help would be greatly appreciated.  Thank you!

-Mary

---

### Post by taurus on 2007-05-26
What is the error message when you boot into Ubuntu (not the recovery mode)?

---

### Post by mschoen7 on 2007-05-26
If I select to boot into Linux without the recovery mode, it takes forever, then finally I see the tan desktop with nothing on it.  The only thing I can do is reboot the machine.  Is there a way to see the load instructions during this process?  Sorry if this sounds stupid -- I'm an old Windows person.

~M

---

### Post by taurus on 2007-05-26
While booting into recovery mode, you can edit /boot/grub/menu.lst

```
nano -Bw /boot/grub/menu.lst
```
and remove the **quiet** at the end of the line for the kernel entry.  Save it with <Ctrl>o and exit with <Ctrl>x.  Now, reboot.

p.s.  Which release are you running anyway?

---

### Post by mschoen7 on 2007-05-26
It gets to 'setting up console font and keymap', then on the next line displays 'root@mary-desktop~#' and stops.  It appears to be waiting for input.

I am using Ubuntu 7.04, Live CD.

Thank you!

~M

---

### Post by mschoen7 on 2007-05-26
UPDATE!!!  I found the problem.  The second hard drive is a Seagate 80 GB ultra ATA drive.  I decided to partition it into smaller pieces with GParted (three 20 GB + one leftover), then try the install again.  Even though I told it to use the whole 80 GB hdd via Guided, it installed successfully.  Yea!   

Now my only problem is I can't get on the internet.  I have a USB Belkin wireless, which talks to our Linksys wireless (unsecured) network and goes to the internet via QWest DSL.  

~M

---

