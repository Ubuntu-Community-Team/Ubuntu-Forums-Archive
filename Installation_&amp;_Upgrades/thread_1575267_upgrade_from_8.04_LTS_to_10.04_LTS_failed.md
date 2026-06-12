---
title: "upgrade from 8.04 LTS to 10.04 LTS failed"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by sandy_ptc on 2010-09-15
I was running ubuntu 8.04 LTS happily for more than an year.One fine day got a popup saying upgrade to 10.04. I clicked on it and waited for about 8 hours till my pc downloaded several files and then installed them as well. The last  step asked me to restart the system. This is where I got stuck as I only saw 8.04 in my grub loading menu which failed to start. My Windows OS on the grub  menu works just fine.
Now I am back to running my pc using 7.10 live CD.It seems the data on my HD is intact as I am still able to view the pictures that I have there.

Is it possible to run 10.04 which I suppose is installed in my HD now using legacy GRUB or do I need to necessarily upgrade to GRUB2. If I manage to upgrade my legacy GRUB to GRUB2 will it automatically detect the ubuntu 10.04 and Windows OS ? 
Any responses would be very helpful for me.

---

### Post by arrange on 2010-09-15
I would keep the Grub Legacy for the time being, you can upgrade that later. Can you post the output of the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

[COLOR="DimGray"]I only saw 8.04 in my grub loading menu which failed to start[/COLOR]
Can you give us more detail on that?

---

### Post by KegHead on 2010-09-15
Hi!

If I remember correctly you can't upgrade  8.04 to 10.04.

You can only upgrade from 9.10 to 10.04.

Or do a clean install.

KegHead

---

### Post by melipone on 2010-09-15
> **KegHead said:**
> Hi!

If I remember correctly you can't upgrade  8.04 to 10.04.

You can only upgrade from 9.10 to 10.04.

Or do a clean install.

KegHead
If I'm not mistaken 8.04 is Hardy Heron and 10.04 is Lucid Lynx and yes you can upgrade from one to another. They are both LTS distros of Ubuntu.

---

### Post by sandy_ptc on 2010-09-15
Hi arrange

I managed to run the boot_info_script and the result file is attached.

---

### Post by arrange on 2010-09-15
Reboot, and upon seeing the Grub menu press **e** to edit the line *Ubuntu 7.10, kernel 2.6.22-14-generic* and change it from```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=fe143464-584d-4b8d-9ac4-9b1d38aec945 ro quiet splash
quiet
```

into
```
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=fe143464-584d-4b8d-9ac4-9b1d38aec945 ro
initrd        /boot/initrd.img-2.6.32-24-generic
quiet
```Then press **b** to boot. Success?

---

### Post by sandy_ptc on 2010-09-16
Yes arrange

Success at last. I am booted into my ubuntu from the hard disk.

Thanks alot for you help.

---

