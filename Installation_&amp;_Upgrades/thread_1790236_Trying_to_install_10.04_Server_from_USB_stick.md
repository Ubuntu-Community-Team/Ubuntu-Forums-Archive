---
title: "Trying to install 10.04 Server from USB stick"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by Dry Lips on 2011-06-24
Here is an issue that I've just encountered:
 
I've just attempted to put an iso of 10.04 server on an USB-stick, but 
during the installation I run into this problem:

```
No Common CD-ROM drive was detected.  
[snip] 
Manually select a CD-ROM module and device?

``` Now, I *don't* have a CD-ROM, (or, rather, I won't bother plugging 
one in) that's the whole point of using a stick, and if you don't have a CD-ROM,
it simply refuses to proceed.  &#8220;*Installation step failed*&#8221; etc.
 
 Is it impossible to install Ubuntu server from an USB stick, (without a CD-ROM) 
or is the installation somehow corrupted?

---

### Post by C.S.Cameron on 2011-06-24
When all else fails try booting the iso with grub2 using MultiBootUSB.

Also check your iso's MD5SUM to make sure it is not corrupt.

---

### Post by Dry Lips on 2011-06-24
> **C.S.Cameron said:**
> When all else fails try booting the iso with grub2 using MultiBootUSB.

Also check your iso's MD5SUM to make sure it is not corrupt.
   	 	 	 	 	 	  Thanks for your suggestions.
 

 The md5sum was correct. I was able to boot from the USB after using Netbootin, but now I wonder whether or not Ubuntu server requires a CD-ROM for the installation to proceed... Have any of you tried installing Ubuntu server on a machine without a CD-ROM?

---

### Post by YesWeCan on 2011-06-25
This person had to put a CD drive in before it would install. Sigh.
[http://ubuntuforums.org/showpost.php?p=10944428&postcount=1](http://ubuntuforums.org/showpost.php?p=10944428&postcount=1)

---

### Post by Dry Lips on 2011-06-25
> **YesWeCan said:**
> This person had to put a CD drive in before it would install. Sigh.
[http://ubuntuforums.org/showpost.php?p=10944428&postcount=1](http://ubuntuforums.org/showpost.php?p=10944428&postcount=1)

Thanks!
 

 That's what I suspected. Anyway, that's really annoying! I might have to... connect a CD-ROM or do a Netinstall or something! :x Does any of you know if they have fixed this in later versions?

---

btw, I'll mark this thread as solved. But if anyone have further insights, 
feel free write a few lines. And what about my initial Netbootin vs Startupdisk 
question?

---

### Post by Dry Lips on 2011-06-26
Update:
 

 It won't even install if you have a CD-ROM connected. It seems as if the ONLY way to install Ubuntu server is to boot from a physical CD-ROM.

---

