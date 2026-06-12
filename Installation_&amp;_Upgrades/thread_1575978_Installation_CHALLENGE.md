---
title: "Installation CHALLENGE"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by Arcnsparc on 2010-09-16
Here is what I am trying to do:
I have a 16gB usb stick partitioned as follows:
sdb1   55mB fat16  I want to put grub here
sdb2   5gB  ext3   I want to put ubuntu here
sdb3   10gb fat32  I want to mount this under linux or windows


So I've read through about a dozen how-to's on putting grub on its own partition or on a usb stick but not both...  I'd also enjoy being able to boot isos stored on sdb3 from the grub menu, but ill get to that once i get the stick booting correctly.  

So I need ideas for:
1) getting grub on sdb1 & booting from sdb1
   I am about to reboot now, I may have figured this one out by using the --prefix=PATH modifier on the grub 'configure' script.
2) getting ubuntu on sdb2 after i get sdb1 working

---

### Post by Arcnsparc on 2010-09-16
I got "MBR FA:"  again....  So thats super cool... i have the sb1 flagged as bootable and grub installed to it without any obvious errors...  I was using Grub 1.98, ill go back to the grub pages to see if I can figure this out, but any ideas would be much appreciated!

now looking into using the SGD  [http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
       *edit*  I could not get the above method to work

---

