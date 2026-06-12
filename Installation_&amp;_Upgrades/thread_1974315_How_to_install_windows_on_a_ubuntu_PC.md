---
title: "How to install windows on a ubuntu PC"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by loseby on 2012-05-05
Lost my windows 7 and decided to install Ubuntu 12.04 first on my SSD drive ( that had windows on it ).

Now 12.04 is pretty good and I want to put Windows on a different drive and make this a dual boot system.

Whats the best way to do this ? I could disconnect the SSD and then install win7 on the hard drive and then reconnect and then use GRUB to add windows to the boot menu or even just leave the SSD connected and install windows on the drive I want.

Is there a simple way or better way ?

---

### Post by oldfred on 2012-05-06
If Windows sees that another drive is the boot drive it will try to put its hidden 100MB boot/repair partition on that drive. You want it on your hard drive. I think you can just set BIOS to boot hard drive before install and you should be ok. 

You have to have a primary partition with the boot flag formated NTFS. If you just have unallocated space and an available primary partition it will install to two partitions, with the separate boot partition.

---

### Post by carl4926 on 2012-05-06
I'd pull the Ubuntu SSD

Install windows
Then add back the Ubuntu drive and set it as first boot device
Then run update-grub

---

### Post by loseby on 2012-05-06
yes.....I think I will unplug the ssd and see how it goes as I dont want windows installer messing with my Ubuntu installation

some more info on updating grub would be nice

---

### Post by carl4926 on 2012-05-06
Once you put the Ubuntu drive back and it's first in boot order, Ubuntu will boot (should) normally.

Once at the desktop, open a terminal and do

```
sudo update-grub
```

That's it

---

### Post by loseby on 2012-05-08
pretty much a disaster

I have a feeling that the hard drive that I installed Win7may be a bit "dicky"  ... 


anyway, new plan of attack, am getting another SSD and win7 is going on that

---

### Post by loseby on 2012-05-11
well there is a big problem somewhere

I can install o/s's seperately but when I connect all up and boot windows dies..... you can disconnect the 12.04 drive again but windows wont load.....

my feeling now is that the new type of BIOS for the Z77 motherboards is doing something weird or 12.04 is

In the past I have never had problems like this

---

### Post by loseby on 2012-05-11
solution is simple   


dont use the Z77 mobo


moved the SSD with 12.04 to an older and simpler chipset  ....58


now have dual boot

---

