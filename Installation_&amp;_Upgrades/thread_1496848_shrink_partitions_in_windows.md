---
title: "shrink partitions in windows"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by rap3point0 on 2010-05-29
I am going to setup for dual-boot with Ubuntu, but need to shrink the windows 7 partition. The partition is defragmented already, but windows will only shrink it to 113 gigs when it also says 98 gigs are free. I would guess there is an unmovable file in the way is there a way to get around this. 
Thanks in advance

---

### Post by stinger30au on 2010-05-29
the ubuntu installer will shrink it for you, you just need to tell the installer how much u want to be set aside for ubuntu and it will do the rest

---

### Post by darkod on 2010-05-29
Uhhh... you better search windows forums and tutorials for that.
I think it was System Restore, you know, saving the restore points if you wanna go back. Disable the option and I think it will allow you to shrink more.

BUT NOTE: I think disabling the setting removes all currently existing restore points, so think whether you need any of them. And also, I'm not 100% sure this is the reason it can't shrink more.

The option was somewhere in Advanced System settings, System Protection tab.

---

### Post by darkod on 2010-05-29
> **stinger30au said:**
> the ubuntu installer will shrink it for you, you just need to tell the installer how much u want to be set aside for ubuntu and it will do the rest

Yeap, but that can also corrupt windows because it likes to do its disk checks after a resize, and the ubuntu installer will continue to install ubuntu right away. Doing the resize first as separate step is best option, if possible.

---

### Post by rap3point0 on 2010-05-29
I planned on having a shared partition and /home partition too I am not sure Ubuntu installer can do that automatically.

---

### Post by darkod on 2010-05-29
> **rap3point0 said:**
> I planned on having a shared partition and /home partition too I am not sure Ubuntu installer can do that automatically.

Spot on, it can do only standard root + swap setup with the guided methods.

---

### Post by Mark Phelps on 2010-05-31
> **stinger30au said:**
> the ubuntu installer will shrink it for you, you just need to tell the installer how much u want to be set aside for ubuntu and it will do the rest


Please don't advise folks to do this.  They run the risk of corrupting their Win7 partition in the process.  Much safer approach is to use the Win7 Disk Management tool.

---

