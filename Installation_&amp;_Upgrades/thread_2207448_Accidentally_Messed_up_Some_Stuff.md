---
title: "Accidentally Messed up Some Stuff"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by Gaahl_ on 2014-02-23
Ok so I was trying to install Ubuntu for the first time and I selected the demo and full installation bit but when I tried to boot into Ubuntu it said something along the lines of no files found. I am certain this is because I was running the iso through PowerISO and not through an actual CD because my drive is not installed at the moment. I am guessing all I need to do is get a drive and it should work then? If not is there any way I can get rid of it so I am not getting a choice of where to boot to every time I launch my computer?

---

### Post by QIII on 2014-02-23
Hello!

So, you had another OS running at the time you were trying to install Ubuntu?

---

### Post by Gaahl_ on 2014-02-23
Yes I was doing this through Windows 7.

---

### Post by QIII on 2014-02-23
And you were not using Wubi?

---

### Post by Gaahl_ on 2014-02-23
No I was not. Now I have gotten Wubi and uninstalled the previous version and am now re installing Ubuntu. I think this has fixed my problem, thanks a lot!

---

### Post by QIII on 2014-02-23
Well, careful now.

Wubi is a "kick the tires" installation.  It clears out a spot on your drive for what is known as a "loop device", which is partitioned and Ubuntu is installed.  Your Windows boot loader gets a new entry, and if Ubuntu is chosen the computer boots to Ubuntu.  You aren't running one inside the other.  It's either/or.  Just so you understand that.

Wubi was never intended to be a permanent solution and, with the arrival of Win 8 and UEFI, it is not even recommended any longer.

Use your Wubi installation for a while, but at some point you will probably want to create a genuine dual boot arrangement.

Have fun for a bit.  We'll be around when you want to actually dual boot!

Best wishes.

---

