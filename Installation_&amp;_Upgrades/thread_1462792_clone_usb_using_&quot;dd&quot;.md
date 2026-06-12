---
title: "clone usb using &quot;dd&quot;"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by TomAbada on 2010-04-26
hi all
i made a live USB ubuntu
and now i wanna clone the USB to another new USB
i wanna do it using "dd" but i have no idea how

both of the USBs connected to my PC. one USB is a live ubuntu,
the other is empty 

how can i clone one to another ??

thanks in advance

---

### Post by Grenage on 2010-04-26
It should be a simple case of:

```
dd if=/dev/sd**x** of=/dev/sd**y** bs=4096
```

Where x is the source USB disc and y is the destination disk.  Do _not_ put the wrong drives in the command, it will overwrite without prompting you.

---

### Post by TomAbada on 2010-04-26
thanks

ive tryed to do that command
but it says it that the USB is a directory

can dd copy directories ?

---

### Post by Grenage on 2010-04-26
dd can copy anything, it's dealing with raw blocks.

Can you post the exact command you used, and a rough output of *sudo fdisk -l*.

---

### Post by TomAbada on 2010-04-26
i forgot to mention an important detail
the live USB has encrypted partitions

is it still possible of doing "dd" ?

btw ive wrote the command and it seems the terminal is not doing anything

though when i try to close it it says "there is still a process running in this terminal, closing the terminal will kill it"

so it means its in the middle of copying ??

---

### Post by Grenage on 2010-04-26
dd is not concerned with partitions, files, directories or anything else.  It literally just copies blocks of data - it does not care what they are.

---

### Post by TomAbada on 2010-04-26
oh i c
so its no problem then

thanks a lot for ur help :)

---

