---
title: "taking too long to boot"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by vikasmk on 2008-02-07
hi, i just installed gutsy gibbon with a dual boot with xp.
 Xp boots in about 10 seconds but ubuntu takes about 6 minutes to boot. is that normal??:confused: 
  please suggest something please.
 
 My pc config: intel 845 mother board, 512 Mb ram, 80gb hdisk, P4 2,4 ghz .

---

### Post by jan quark on 2008-02-07
try this

[http://ubuntuforums.org/showthread.php?t=580903&highlight=booting+time](http://ubuntuforums.org/showthread.php?t=580903&highlight=booting+time)

---

### Post by vikasmk on 2008-02-07
tried it but i cant seem to change the menu.lst file , it says that i dont have permission to change the file.:(

---

### Post by CodeDragon on 2008-02-07
Try using sudo to edit the file.  I find this is easiest on the command line.

```
sudo gedit /boot/grub/menu.lst
```

Or replace gedit with your favorite text editor.

---

### Post by vikasmk on 2008-02-08
yep it worked , boots in about  a minute.
 thanks guys..........................:)

---

