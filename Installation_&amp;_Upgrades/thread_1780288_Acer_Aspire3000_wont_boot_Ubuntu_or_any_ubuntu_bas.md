---
title: "Acer Aspire3000 wont boot Ubuntu or any ubuntu based variant"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Frogster on 2011-06-11
Evening All,

I hope someone can help with this, its got me perplexed. 

Load the Ubuntu 11.04 liveCD and this is what I get

Busybox v1.17.1 (Ubuntu 1:1.17.1-Ubuntu1) built-in shell (Ash)
Enter help for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed:Input/output error
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

It seems like the only live CD that I can get to load is an old 7.10 version and an 9.10 install cd.

Help please

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Frogster said:**
> Evening All,

I hope someone can help with this, its got me perplexed. 

Load the Ubuntu 11.04 liveCD and this is what I get

Busybox v1.17.1 (Ubuntu 1:1.17.1-Ubuntu1) built-in shell (Ash)
Enter help for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed:Input/output error
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

It seems like the only live CD that I can get to load is an old 7.10 version and an 9.10 install cd.

Help please

Did you check to see if your system is listed:

[http://www.linux-laptop.net/acer.html](http://www.linux-laptop.net/acer.html)

---

### Post by Frogster on 2011-06-11
Thanks for the reply. I followed the link and found:

# Acer Aspire 3000 [Mandriva LE 2005] (in Fran&#65533;ais)
# Acer Aspire 3000 [Ubuntu Fiesty 7.0.4]
# Acer Aspire 3000 [Debian 5.0 (lenny)]
# Acer Aspire 3000 [Ubuntu 7.10]
# Acer Aspire 3000WLCi [opensuse 11.

Does this mean that 7.10 is the only Ubuntu version that will work? If so, ita a non supported version. I thought with each iteration more hardware was supposed to be supported?

Still confused

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Frogster said:**
> Thanks for the reply. I followed the link and found:

# Acer Aspire 3000 [Mandriva LE 2005] (in Fran&#65533;ais)
# Acer Aspire 3000 [Ubuntu Fiesty 7.0.4]
# Acer Aspire 3000 [Debian 5.0 (lenny)]
# Acer Aspire 3000 [Ubuntu 7.10]
# Acer Aspire 3000WLCi [opensuse 11.

Does this mean that 7.10 is the only Ubuntu version that will work? If so, ita a non supported version. I thought with each iteration more hardware was supposed to be supported?

Still confused

What i would do if I were you is this, since you are working with an older computer/laptop. 

Create a live USB Flash Drive of Ubuntu 10.04. Keep going back until it actually boots. Trial and error at this point.

Once you get it install to your Hard Drive, you can run:

```

sudo apt-get update && sudo apt-get dist-upgrade

```And upgrade it to the latest version of "supported" ubuntu.

---

### Post by Frogster on 2011-06-11
Thanks linuxinstalledfromhdd, 

I will give it a try, hopefully can give this laptop a new lease of life

---

### Post by linuxinstalledfromhdd on 2011-06-11
No problem Please click on "Thread Tools" to close this thread up above if you are done. :)

---

### Post by Frogster on 2011-06-12
Hmmm, I couldn't boot from Usb (no boot option available) but found that I could install from an old 8.04 disk. I then upgraded to 10.10. Quite a long process but all seems to work now.

---

