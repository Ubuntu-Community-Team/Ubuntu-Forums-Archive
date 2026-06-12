---
title: "64bit Feisty installed under 32 bit processor"
date: 2007-06-10
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-06-10
I mistakenly installed the 64 bit version of Feisty on a 32 bit processor.  Is there a way to revert to the 32 bit version without having to completely reinstall from CD?

---

### Post by madmetal on 2007-06-10
> **JarG0n said:**
> I mistakenly installed the 64 bit version of Feisty on a 32 bit processor.  Is there a way to revert to the 32 bit version without having to completely reinstall from CD?

you can use ubuntu 64bit with no problems at 64bit cpu.. 
although if you want to use 32bit ubuntu you have to re-install it...

---

### Post by bmaxd on 2007-06-10
Unless you really need 64-bit, you will want to use the 32 bit version.  Sadly, that means reinstalling.

---

### Post by prince_niceguy on 2007-06-12
this is technically not possible. your processor has to be 64 bit to install 64 bit OS on it. you cannot install 64 bit OS on 32 bit computer.

since you have installled 64 bit... try it for some time. If you do not like it then reinstallation is the only option... :-(

---

### Post by Sweet00th on 2007-06-12
can you explain how you accomplished this?

---

### Post by zackboarman on 2007-06-20
You could just install a 32bit kernel & edit apt configuraton files to change from amd64 to i686, then install the 32bit versions of the programs. 

**OR**

If you are somehow using the 64bit ubuntu on your computer & it works, just back up /home, /etc/passwd, etc. to another partition, or drive & reinstall the whole system using a 32bit CD.

---

### Post by family on 2007-07-28
64 -> 32???  How?

---

