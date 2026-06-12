---
title: "Problem booting into os x after clean install of Ubuntu 10.4 on a separate drive"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by tomekpilot on 2010-05-18
The hardware is a psystar box with 2 drives for os x and ubuntu respectively.

I attempted install of ubuntu over older version of xubunut without  physically disconnecting the os x drive :-(
After install I could not boot into either system. THEN I remembered something about the install problem that 10.4 has and installed ubuntu again, this time following the instruction regarding booloader install.

Now I can boot ubunut fine, but of course when I select drive holing os x it hangs on 'Verifying DMI pool data....'

I've been looking at some thread on here about dual boot problems with Win7 and such, but are any of the recommended diagnostic and repair steps relevant to my case, specifically testdisk and bootinfo scripts?


I did not have a chance to run boot info yet, but will later tonight.

Thanks in advance!

---

### Post by tomekpilot on 2010-05-18
just run BootInfoScript, attached the results.txt


```
 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 126113320 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
```

... any ideas on how to proceed from here?

---

