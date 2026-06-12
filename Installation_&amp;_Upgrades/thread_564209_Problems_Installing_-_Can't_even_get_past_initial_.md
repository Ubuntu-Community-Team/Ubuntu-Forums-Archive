---
title: "Problems Installing - Can't even get past initial screen&quot;"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by Poene on 2007-09-30
Issue: I cannot "check CD for defects" nor am I able to install ubuntu with the alternate CD on my main desktop. 

Facts: Upon selecting check CD for defects or Install ubuntu I get this: 
```
 /bin/sh: symbol lookup error: /lib/libc.so.6: undefined symbol: _res_oconf. version GLIBC

[1.21200] Kernel Panic - not syncing: Attempted to kill init!

[1.21200] 
```

The CD checks passes on my other desktop.

Hardware:

AMD Athlon 4200+
ECS Motherboard
2G DDR2 RAM
ATI X1950 PRO
Seagate 250GB HD IDE
Maxtor 200G HD IDE
Maxtor 200G HD SATA

---

### Post by Pumalite on 2007-09-30
Graphics?

---

### Post by Poene on 2007-09-30
updated!

---

### Post by Pumalite on 2007-09-30
With your ATI Video Card, you need the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'
Follow these guidelines: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(burn at 4x)

---

### Post by Poene on 2007-09-30
_I am using the alternate CD._ The MD5SUM on the ISO passes and so does the Check CD tool on the CD itself.

---

### Post by Pumalite on 2007-09-30
Clean the lens in your CD-ROM or try the CD's in another computer.

---

### Post by Poene on 2007-09-30
How do I clean the lens in my CD-ROMs safely though?

The CDs work fine in another computer.

---

### Post by Pumalite on 2007-09-30
You can get a special CD 'Cleaner' in  any computer store. If you are more technically inclined you could take your CD drive out and use compressed air.

---

### Post by Poene on 2007-09-30
> **Pumalite said:**
> You can get a special CD 'Cleaner' in  any computer store. If you are more technically inclined you could take your CD drive out and use compressed air.

I will try this and post updates later.

---

### Post by Pumalite on 2007-09-30
Ok.

---

### Post by Poene on 2007-09-30
I used the CD-RW Drive from this computer (which works because I'm on it right now =D). I get a different error of 

```
 :VFS: Unable to mount root fs on unknown-block(104,1) 
```

Any help is greatly thanked.

---

### Post by Pumalite on 2007-09-30
[http://ubuntuforums.org/showthread.php?t=550737](http://ubuntuforums.org/showthread.php?t=550737)
[http://ubuntuforums.org/showthread.php?t=477921](http://ubuntuforums.org/showthread.php?t=477921)
[http://www.linuxquestions.org/questions/showthread.php?t=458751](http://www.linuxquestions.org/questions/showthread.php?t=458751)
[http://www.linuxquestions.org/questions/showthread.php?p=2903923](http://www.linuxquestions.org/questions/showthread.php?p=2903923)
[http://www.unixadmintalk.com/f39/linux-kernel-2-6-3-kernel-panic-vfs-unable-mount-root-fs-unknown-block-0-0-a-56204/](http://www.unixadmintalk.com/f39/linux-kernel-2-6-3-kernel-panic-vfs-unable-mount-root-fs-unknown-block-0-0-a-56204/)

---

### Post by twist2b on 2007-09-30
i may be to late but you should try to reinstall the file for amd and all then reburn... just redo it all ya know?

that might do something good :P

---

### Post by Poene on 2007-09-30
> **twist2b said:**
> i may be to late but you should try to reinstall the file for amd and all then reburn... just redo it all ya know?

that might do something good :P

Which files for AMD are you talking about?

eh... My processor is an AMD Athlon 64 X2. Does this mean I need the 64-bit version? I am confused =C

---

### Post by Poene on 2007-09-30
> **Pumalite said:**
> [http://ubuntuforums.org/showthread.php?t=550737](http://ubuntuforums.org/showthread.php?t=550737)
[http://ubuntuforums.org/showthread.php?t=477921](http://ubuntuforums.org/showthread.php?t=477921)
[http://www.linuxquestions.org/questions/showthread.php?t=458751](http://www.linuxquestions.org/questions/showthread.php?t=458751)
[http://www.linuxquestions.org/questions/showthread.php?p=2903923](http://www.linuxquestions.org/questions/showthread.php?p=2903923)
[http://www.unixadmintalk.com/f39/linux-kernel-2-6-3-kernel-panic-vfs-unable-mount-root-fs-unknown-block-0-0-a-56204/](http://www.unixadmintalk.com/f39/linux-kernel-2-6-3-kernel-panic-vfs-unable-mount-root-fs-unknown-block-0-0-a-56204/)

I tried many of those solutions such as disabling power management, disabling ACPI (I had to re-enable it as it made the problem worse).

I read on one of the links that a kernel panic is a low-level error. I don't think it could be my RAM as it is new RAM that I bought in July. 
. 
My processor runs at 139 degrees Fahrenheit Is that normal?

---

### Post by twist2b on 2007-10-03
YES, you need to downlaod a diffrent ISO file, sorry... but its all good try the amd verison... if it doesnt work... use alternet cd... if it still doesnt work... then post again :P

---

