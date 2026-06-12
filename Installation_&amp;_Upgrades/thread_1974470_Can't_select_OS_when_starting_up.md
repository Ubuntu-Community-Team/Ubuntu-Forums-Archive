---
title: "Can't select OS when starting up"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by eggsbenedict on 2012-05-06
Greetings,

I recently installed Ubuntu 12.04 along side my existing Ubuntu 10.04 set up.  I followed the installation instructions, and chose to install them along side each other.  However, after successful installation, every time my computer starts up, it boots into 10.04, never prompting me to choose between 10.04 or 12.04.  

I more than likely didn't do something correctly, but I can't figure out what it is - after all, the ubuntu installation instructions are so easy to follow!

Thank you for any help!
-EB

P.S. Apologies if this is discussed elsewhere; I searched around and couldn't find anything that matches my problem!

---

### Post by mips on 2012-05-06
where did you install grub to?

---

### Post by zvacet on 2012-05-06
If you installed grub on MBR then press shift key during boot and you will se it.if you instaled grub on partition then boot in 10.04 and 

```
sudo update-grub
```

---

### Post by darkod on 2012-05-06
You probably have more than one hdd and the grub2 from 12.04 ended up on another disk. You are still booting the grub2 from 10.04 and until you run the update-grub it will not detect the new 12.04.

If you prefer booting grub2 from 12.04, select to boot from another disk as first option in BIOS. That grub2 should already have both 12.04 and 10.04 because it detected it during install.

---

### Post by eggsbenedict on 2012-05-06
Thank you, everyone!  I ran in terminal:

sudo update-grub 

This worked.  I'm very thankful for the responses.
Now, when I boot up, I get the choices:

Ubuntu, with Linux 2.6.32-41-generic
Ubuntu, with Linux 2.6.32-41-generic (recovery mode)
Ubuntu, with Linux 2.6.32-38-generic
Ubuntu, with Linux 2.6.32-38-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Ubuntu, with Linux 3.2.0-23-generic (on /dev/sda6)
Ubuntu, with Linux 3.2.0-23-generic (recovery mode)


Using trial and error, I figured out that the Linux 3.2.0-23-generic is the 12.04 that I wanted to boot, and the 2.6.32-41-generic is the 10.04.  But, I have a quick question: what is the 2.6.32-38-generic?  When I boot it, it looks like 10.04, but should I ignore this one?  

Thanks again for all the help!

---

### Post by darkod on 2012-05-06
The first three numbers with the dots inbetween are related to the version and will always be the same usually. The last number after the - is the kernel, and when new kernels are released they install and don't remove the old ones. Sometimes if you see an issue with the latest kernel -XX you can boot the previous -YY that worked. That's why the old ones are not automatically removed.

So, you're right, both -41 and -38 is your 10.04 LTS.

I don't know the exact scientific explanation, but it's sort of like the core files. And there can be more than one installed, as you can see. Usually you would always boot the latest, with the higher -XX number, unless you have problems with it.

---

### Post by drs305 on 2012-05-06
It's just an older kernel which was replaced by 2.6.32-41. When a newer kernel is installed within an Ubuntu release, the older kernel is retained and is still displayed (somewhere) in the menu.

In your case, if you plan on using Precise, you probably want Grub to use the Grub files from the Precise installation. At the moment, if you posted them in the order they appear in your menu, it's using your other Ubuntu installation.

The easiest way to change over to Precise's grub is merely to boot into Precise, and then run:
```

sudo update-grub
sudo grub-install /dev/sdX
```
with X being the *drive* your BIOS boots first (sda, sdb, etc)

---

### Post by eggsbenedict on 2012-05-06
Excellent!!  Thank you for the explanations and solutions.  I can say that everything is working smoothly, the way I'd like it to.  The only thing left is that is that the Ubuntu boot animation (Ubuntu logo with dots underneath showing it is loading) is  weirdly distorted.  So far this is just an aesthetic difference - everything works great, though!

Thanks so much!

---

