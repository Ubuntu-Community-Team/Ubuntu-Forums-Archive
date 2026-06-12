---
title: "Dual-boot hal.dll error"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cajunlibra on 2009-04-11
I upgraded to Jaunty from Intrepid a few days ago and ha issues with it so I then did a fresh install of Jaunty.  Since the upgrade, I am now getting the hal.dll error when I try to boot in windows. I did change my swap partition from the small one that is listed as unallocated to the current one that is ~1GB. I hadn't booted XP in a few days so I couldn't say when this error originally occured.

I have tried the instructions from [this]("http://ubuntuforums.org/showthread.php?t=78509") thread but making glib spits out tons of errors.

Just a sample of the output
_CHECKS -DG_DISABLE_DEPRECATED -DGIO_COMPILATION -DGIO_MODULE_DIR=\"/opt/gtk/lib/gio/modules\" -DG_DISABLE_SINGLE_INCLUDES -pthread -g -O2 -Wall -MT gpollfilemonitor.lo -MD -MP -MF .deps/gpollfilemonitor.Tpo -c gpollfilemonitor.c  -fPIC -DPIC -o .libs/gpollfilemonitor.o
mv -f .deps/gpollfilemonitor.Tpo .deps/gpollfilemonitor.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -DG_LOG_DOMAIN=\"GLib-GIO\" -I.. -I.. -I../glib -I../gmodule -DG_DISABLE_CAST_CHECKS -DG_DISABLE_DEPRECATED -DGIO_COMPILATION -DGIO_MODULE_DIR=\"/opt/gtk/lib/gio/modules\"  -DG_DISABLE_SINGLE_INCLUDES -pthread  -g -O2 -Wall -MT gseekable.lo -MD -MP -MF .deps/gseekable.Tpo -c -o gseekable.lo gseekable.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -DG_LOG_DOMAIN=\"GLib-GIO\" -I.. -I.. -I../glib -I../gmodule -DG_DISABLE_CAST


I have also tried to replace hal.dll with one that I downloaded and that did nothing.  I used the Dell Diagnostic CD also and it didn't do anything. I'm on a Dell Precision M20 that is 3 years old. 

I also do not have a boot.ini anywhere in my profile.
Following directions fro compiling from [here]("http://library.gnome.org/devel/gtk/unstable/gtk-building.html").

I can't mount my xp partition now either.
I also tried the grub command find /boot/stage1 and got an error that file not found both within jaunty and on the grub loader command line.

Thanks


Partition Table
unallocated    62.75MB
/dev/sda2     ntfs                         boot   (XP)
/dev/sda4     ext3    /
/dev/sda1    extended
     /dev/sda5 linux-swap
/dev/sda3    fat32       mounted w/ label


Using Live distro from USB drive I can mount my XP partition.
```
boot.ini
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

---

### Post by meierfra. on 2009-04-11
> multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Change

partition(2)

to

partition(1)

---

### Post by cajunlibra on 2009-04-11
In the directions I followed, they did exactly the opposite. Can you explain why I should make this change?  I would just like some clarification so that I understand what is going on.


Thanks

---

### Post by meierfra. on 2009-04-11
> Can you explain why I should make this change

Sure.  

> unallocated 62.75MB
/dev/sda2 ntfs boot (XP)
/dev/sda4 ext3 /
/dev/sda1 extended
/dev/sda5 linux-swap
/dev/sda3 fat32 mounted w/ label

Windows counts partitions slightly different than linux. It  uses the same order  as linux

sda1, sda2, sda3,sda4,sda5

but windows ignores extended partitions, so it does not count sda1:


sda2, sda3, sda4,sda5

This makes the windows partition (/dev/sda2) the first partition.

So you need to use "partition(1)"


> I have tried the instructions from this thread but making glib spits out tons of errors.

Forget about those instructions. That tutorial is 4 years old.  Ubuntu now has build-in read and write support for ntfs partition.  So you don't need to do anything special to edit "boot.ini"

---

### Post by cajunlibra on 2009-04-12
Thank you so much.  That did it.  I got a dll error but I just changed back to the original hal.dll and it started right up.

---

### Post by meierfra. on 2009-04-12
```
and it started right up.
```
Great. Enyoy XP and Ubuntu.

---

