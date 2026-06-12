---
title: "Installation did not complete - reinstall?"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by codyr452 on 2008-02-17
Hi there,

I'm totally new to Linux and probably approached this the wrong way but whatever...

So I was installing 7.10 from the Live CD and it got through to 94 % and then stopped at loading module something about IDE Floppy.  I went out for lunch and did some other stuff and 3 hours still no go.  Anyways, system eventually was reset and I'm assuming I have an incomplete installation now.  I was able to use the Live CD to get back and set the partition with XP back to boot but I don't want 40GB of wasted hard drive space.

Can I go back and reinstall on that partition?  Any ideas on what my next step should be?  If I use the partition thing in the install and just tell it to erase all data on that partition will that just be like starting again?  Should I use the alternate disk?

I did check that my live cd passed the winmd5sum and integrity check.

Thanks for any help.

Also, when I use the live cd I can't access the internet.  Is my network card not recognized or is there always a manual step at that point?

---

### Post by zvacet on 2008-02-18
Yes,you can reinstall.when you come to partition step select Ubuntu partition(ext3 format) and delete it.Now you have unallocated space on wich you can install again.Maybe alternate is good option.To configure network go to the upper right and click on network manager applet>manual config>window will pop up and select your modem(don´t tick it just click on it)>properties>select your connection type(dhcp or static)>close>DNS tab>you will see one address there,delete it and ad your nameservers>connections tab>now tick your modem and window will pop up with message configuring network interfaces(or somrthing similar).When it is finish go to the programs<accessories>terminal and type

```
pppoeconf
```

---

