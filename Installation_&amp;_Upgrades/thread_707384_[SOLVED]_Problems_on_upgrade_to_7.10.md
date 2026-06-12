---
title: "[SOLVED] Problems on upgrade to 7.10"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by bcwhittle on 2008-02-25
Recently, having 7.something installed (sorry, can't remember which one), I went through the procedure to upgrade everything automatically.  The next time I rebooted, I got an Error 15.  I have researched it some, and this is the best that I can figure . . .

GRUB seems to be working okay.  I can get the menu.  But no matter what choice I make, I get the error 15.  I have tried to go to a shell and directly boot from a kernel in /boot, and then I get a kernel panic.

Any suggestions on what I should do?  I would rather not have to install over the old installation, but if that's the only way, I can . . .

---

### Post by jeffus_il on 2008-02-25
Don't install again. Something changed on your system on your system and grub can't find a file, probably the kernel. Use the livecd to have a look at the contents of the /boot folder on your hard drive. Make a note of the kernel images you find there.
Reboot and at the grub menu hit <escape>. Highlight the line starting with "kernel", type e (for edit) and make sure that the kernel in the menu is actually on the disk. If not change the kernel and type "b" (for boot)

---

### Post by bcwhittle on 2008-02-25
GRUB is looking for 2.6.22-14-generic.

Here are the files in the /boot directory:
abi-2.6.22-14-generic
config-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
initrd.img-2.6.22-14-generic.dpkg-bak
memtest86+.bin
System.map-2.6.22-14-generic
vmlinuz-2.6.22-14-generic

I have tried using the vmlinuz as kernel, and either of the initrd files, and end up with a kernel panic either way.  Am I missing some files?  If so, where do I find them to get them on the hd?

---

### Post by jonny5tails on 2008-02-25
[FONT=Comic Sans MS]Hi bcwhittle, is this your error mess. - (15 : File not found
     This error is returned if the specified file name cannot be found,
     but everything else (like the disk/partition info) is OK.)?
Can you post your /boot/grub/menu.lst? This will tell us what grub is actually trying to do.
jonny ](*,)
[/FONT]

---

### Post by jeffus_il on 2008-02-25
You are missing initrd.img-2.6.22-14-generic.
Try rename the .bak file using:
```
sudo mv initrd.img-2.6.22-14-generic.bak initrd.img-2.6.22-14-generic
```

---

### Post by bcwhittle on 2008-02-25
Thank you, Jeff . . . renamed the file and that did it.  Oh, I wish I had thought of something so simple, would have a bit more hair than I have now.

---

### Post by bcwhittle on 2008-02-25
A new problem has emerged.  And I think this may be what caused the problem in the first place.

When I try to run Adept Updater, I get a message that Databases are locked. . . another program is using the packaging system database.  Problem is, I have just recently restarted it and have not run anything except firefox.  How can I find out what is causing the database to be locked, how can I unlock it and continue?

---

### Post by jeffus_il on 2008-02-26
Try <ctrl><alt><f1> to a console
Stop kdm  ```
sudo /etc/init.d/kdm stop
```run ```
sudo aptitude update
```and then ```
sudo aptitude upgrade
```

---

### Post by bcwhittle on 2008-02-26
Whew, that did it.  I'm pretty sure this time!

Thanks again.

---

