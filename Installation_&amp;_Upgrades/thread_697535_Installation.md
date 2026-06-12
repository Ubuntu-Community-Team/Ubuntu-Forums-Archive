---
title: "Installation"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Chewyniceva on 2008-02-15
Can anyone help,

I run the Ubuntu CD and the Install begins just fine then as the first screen should come up with the install 
icon i get one of two things.

Either my screen goes blank and just say out of range 

Or I get the desktop view with the install icon but it is very poor or half missing then the screen again goes
blank and out of range.

Can anyone shed any light on what might be happening 

Thanks Lew

---

### Post by jan quark on 2008-02-15
sounds like your graphic card is fighting with ubuntu

what are your specs ?

try the alternate CD
it is a text-based installation but as easy as the graphical one
it solves many graphical issues

here [download]("http://releases.ubuntu.com/gutsy/")

here [guide]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by Pumalite on 2008-02-15
Edit your boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
And try:
vga=0x317
Or others
You can go insto safe graphics mode too.

---

### Post by Chewyniceva on 2008-02-15
Thanks for the tips 

safe graphics mode has the same result, and i looked at the parameters page and yes sorry would not know where to start, and the text base install continues to get to 53% and then i/o error error reading boot cd 

Am now very stuck please can any one help 

Thanks Lew

---

### Post by Pumalite on 2008-02-15
You can try the Alternate CD. Or you can keep trying different parameters. Here is a collection to be tried one by one or in combination:
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off

---

### Post by Herman on 2008-02-15
Sometimes a simple thing like cleaning the lens in your optical drive can make a huge difference.
Unfortunately most CD/DVD drives have the lens built in where it's hard to reach and those lens cleaning CDs don't always do the job they say they will.

---

### Post by Pumalite on 2008-02-16
You are right Herman; maybe he needs to change the burner.

---

