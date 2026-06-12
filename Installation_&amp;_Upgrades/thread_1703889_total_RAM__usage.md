---
title: "total RAM  usage"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by snif123 on 2011-03-09
Hi
I was trying to have a go at installing MAC on my dell alongside Ub and W7. I copied the grub2 to the first part of my sda5 so as to put the mac loader in MBR.I have since repaired grub2 back to MBR.But now my beloved Ubuntu starts up then continuosly increases RAM usage till 90% then SWAP 90% even when no application is running!!
In windows,this is not happening.
Any ideas?

---

### Post by Dutch70 on 2011-03-09
Can you open system monitor and see what is using the RAM? 
Even better, post the output of 
```
free -m
```

Is it really using that much, does your system lag?

---

### Post by mörgæs on 2011-03-10
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

