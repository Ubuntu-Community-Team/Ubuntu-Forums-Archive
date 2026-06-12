---
title: "The latest gdm updates broke nvidia 195.22!"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2009-12-15
The latest gdm updates broke nvidia 195.22!

---

### Post by gnomeuser on 2009-12-15
actually this is very likely a dkms problem.

The offending part of /usr/lib/dkms/dkms_installer is here:


      if [ -L /vmlinuz -a -e /vmlinuz ]
      then <--- missing
	linktarget="$(basename "$(readlink /vmlinuz)")"

Insert that and it works

---

### Post by dino99 on 2009-12-15
> **gnomeuser said:**
> actually this is very likely a dkms problem.

The offending part of /usr/lib/dkms/dkms_installer is here:


      if [ -L /vmlinuz -a -e /vmlinuz ]
      then <--- missing
	linktarget="$(basename "$(readlink /vmlinuz)")"

Insert that and it works

yeah, but it's hanging with a black screen; can't call console even in recovery mode.

Seem to only have 1 choice: reinstall from scratch  ;)

---

### Post by orlox on 2009-12-15
> **dino99 said:**
> yeah, but it's hanging with a black screen; can't call console even in recovery mode.

Seem to only have 1 choice: reinstall from scratch  ;)

Actually, you could change that using a livecd...

---

### Post by jppr on 2009-12-15
i don´t have any problem, works fine. just updated latest dkms.

---

