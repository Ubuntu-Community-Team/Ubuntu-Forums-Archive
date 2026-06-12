---
title: "Unistalling Windows Vista"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by D4RknEZz on 2013-02-23
Hello, I'm new to this forum (I'm a noob :D ). I just installed Ubuntu on my sister's laptop with Wubi. She has Windows Vista. So what I want to do, is uninstall Vista, so she would only have Ubuntu. Does it matter that I have installed Ubuntu via wubi, or can I uninstall Vista anyway? And if I can, how exactly can I do it?

---

### Post by howefield on 2013-02-23
Refer to here : [https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

Although I'd say a clean install is going to be quicker, and much easier :-)

---

### Post by D4RknEZz on 2013-02-23
> **howefield said:**
> Refer to here : [https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

Although I'd say a clean install is going to be quicker, and much easier :-)

Thanks for your help.:D What do you mean exactly by "clean install"? How can I clean install ubuntu? Sorry, it's my first time using Ubuntu and I'm a noob.:P

---

### Post by offgridguy on 2013-02-23
> **D4RknEZz said:**
> Thanks for your help.:D What do you mean exactly by "clean install"? How can I clean install ubuntu? Sorry, it's my first time using Ubuntu and I'm a noob.:P
A clean install is a new install of the ubuntu version of your choice.
A wubi install is, ubuntu installed within windows. As a seperate program,
sort of.
   
Myself and many others prefer installing ubuntu, on it's own partition on
the HDD, alongside windows if you are dual booting or instead of , if you
want to replace windows entirely.

When you install from a live CD or USB stick, you will be given those options.
And welcome to the forums.:D

---

### Post by howefield on 2013-02-23
> **D4RknEZz said:**
> Thanks for your help.:D What do you mean exactly by "clean install"? How can I clean install ubuntu? Sorry, it's my first time using Ubuntu and I'm a noob.:P

What I mean is install Ubuntu to its own partition or disk (or indeed by wiping out Windows) from a live CD/DVD or USB.

Do you still have the Ubuntu iso ? Use it to create a bootable live medium using the Ubuntu Startup Disk Creator application, either with a USB memory stick or CD/DVD.

Boot from it and then proceed with the installation.

If you are so new to Ubuntu, I'd probably not recommend getting rid of Windows altogether. I'd look at dual booting side by side so you have the comfort of knowing that Windows is still there if you really need it.

---

### Post by D4RknEZz on 2013-02-25
Ok thanks for your help. I'll use wubi for a while, just to get used to Ubuntu, then I'll delete it and I'll clear-install it. One more question though. I tried to download some programs, but it said something about i386 architecture, that it is not compatitible with amd64 architecture or something like that. Can you explain what this is and how to fix it? If I clear-install Ubuntu, will it be fixed? Thanks.;):D

---

### Post by NM5TF on 2013-02-25
> **D4RknEZz said:**
> Ok thanks for your help. I'll use wubi for a while, just to get used to Ubuntu, then I'll delete it and I'll clear-install it. One more question though. I tried to download some programs, but it said something about i386 architecture, that it is not compatitible with amd64 architecture or something like that. Can you explain what this is and how to fix it? If I clear-install Ubuntu, will it be fixed? Thanks.;):D

it sounds like you tried to download some programs meant for the
i386 architecture onto a machine built with the AMD64 architecture

in other words, the programs were built for an Intel 386 family CPU, 
but you tried to load them onto a machine with an AMD 64 bit
CPU.....makes sense???

try them again, but this time select the programs meant for the AMD 64 bit processor 
( they usually end with some amd64 suffix)
.....should work this time....and by all means, use the 64 bit versions to 
take full advantage of the systems capabilities...

hope this helps,

Tommy

---

