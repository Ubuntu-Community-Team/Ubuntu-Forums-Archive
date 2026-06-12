---
title: "4GB memory support"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by mjokiel on 2009-12-05
Hello,

I am using Kubuntu 9.10 on AMD, 64bit version with kernel 2.6.32 compiled by myself.
I compiled it with options:

CONFIG_HIGHMEM4G=y
CONFIG_HIGHMEM64G=y

and i have 4GB memory in my laptop, os see only 3,2GB memory.

Do you know how to resolve this problem?

Kind regards,
Mariusz

---

### Post by phillw on 2009-12-05
Hi the 64 Bit Kernel should see 4GB no problem, the 32Bit only goes upto 3.5GB by default, although there is a package to extend this. Are you sure you're using the 64Bit version

If you'd like to read a quite lively debate on RAM and Ubuntu, head over here --> [http://ubuntuforums.org/showthread.php?t=1247372](http://ubuntuforums.org/showthread.php?t=1247372)

Regards,

Phill.

---

### Post by mjokiel on 2009-12-05
> **phillw said:**
> Hi the 64 Bit Kernel should see 4GB no problem, the 32Bit only goes upto 3.5GB by default, although there is a package to extend this. Are you sure you're using the 64Bit version
Phill.

I downloaded the kernel from kernel.org - mainline
Is it correct? Or should i download some other version?

---

### Post by phillw on 2009-12-05
Not sure, but here is the official site -->  [http://releases.ubuntu.com/kubuntu/9.10/](http://releases.ubuntu.com/kubuntu/9.10/)

Obviously, you want the 64 bit one (Desktop) unless you want to run a LAMP server.

Regards,

Phill.

---

### Post by JBAlaska on 2009-12-05
You most likely have "shared" memory with your integrated GPU. Thats' where the stray memory is going.

There may be a setting in your BIOS to control how much RAM your GPU shares.

---

### Post by mjokiel on 2009-12-05
> **JBAlaska said:**
> You most likely have "shared" memory with your integrated GPU. Thats' where the stray memory is going.

There may be a setting in your BIOS to control how much RAM your GPU shares.

There is no such option in BIOS on my laptop.
It is ASUS K51AC.

---

### Post by phillw on 2009-12-05
> **mjokiel said:**
> There is no such option in BIOS on my laptop.
It is ASUS K51AC.

Nice laptop - just looked it up :-)

You may, as pointed out, be using shared memory for the graphics, or a dedicated seperate unit. The chip-set for your graphics supports both. - But, it also states that you will only see 3.5GB RAM with a 32 bit o/system.

Phill.

---

### Post by mjokiel on 2009-12-07
I have 64bit system:
/lib64$ 
Linux zoom 2.6.32-mk #1 SMP Thu Dec 3 15:14:14 CET 2009 x86_64 GNU/Linux
free -m                                                 
             total       used       free     shared    buffers     cached
Mem:          3143       3090         52          0          0       2424
-/+ buffers/cache:        665       2477                                 
Swap:         9538          1       9537

---

