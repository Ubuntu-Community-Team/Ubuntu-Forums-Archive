---
title: "menu.lst gets misconfigured on kernel upgrades"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by xchip on 2008-05-26
Kernel upgrades keeps changing in my menu.lst the line "root (hd0,0)" into "root (hd1,0)"

Is there a way to fix this?
Thanks!

---

### Post by louieb on 2008-05-26
Look for the line that  has **groot=  **and make the change there.

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)


```

---

### Post by masonfoley on 2008-05-26
Just happened to me I think.  Well, Adept update after initial install of 7.10 just blew up during the updating process (Adept crashed) and when I reboot, file not found when attempting to select 7.10.  (I have 8.04 installed and that boots up just fine).

---

### Post by masonfoley on 2008-05-26
> **louieb said:**
> Look for the line that  has **groot=  **and make the change there.

```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)


```

Mine is currently commented out.  Are you suggesting that it should be uncommented?  If so, to which values?  (hd0,0)?  Mine currently reads (hd0,2).

Can you clarify a bit as to what edits you mean specifically?

---

### Post by logos34 on 2008-05-26
> **masonfoley said:**
> Mine is currently commented out.  Are you suggesting that it should be uncommented?  If so, to which values?  (hd0,0)?  Mine currently reads (hd0,2).

Can you clarify a bit as to what edits you mean specifically?

Then your should read:
 
> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,2)**

(the hash symbol included.  Grub still reads it--the exception to the rule)

---

### Post by louieb on 2008-05-26
> **masonfoley said:**
>   If so, to which values?  (hd0,0)? 

Change the (hd0,2) part to (hd0,0) or whatever you need it to be.   
And as logos34 said lieave the # at the front of the line   in the automagic section of  menu.lst. comments are started with ##

---

### Post by xchip on 2008-05-27
thanks everyone!

---

