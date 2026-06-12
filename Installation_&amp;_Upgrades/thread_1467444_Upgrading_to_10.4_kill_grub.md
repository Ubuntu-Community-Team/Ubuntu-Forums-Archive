---
title: "Upgrading to 10.4 kill grub"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by kendzi on 2010-04-30
After upgrading from 9.10 to 10.4 computer stop working. 
Booting stops on grub with a massage:
```
Grub loading.
Error: the symbol 'grub_puts_' not found
grub rescure>
```

I try to restore grub but after command:
```
insmod /boot/grub/linux.mod
``` 
I get error:
```
Error: the symbol 'grub_puts_' not found
```

Is any way to restore grub without Live CD ?

---

### Post by Cyclops_ on 2010-05-01
HERE HERE!

I'm having the exact same issue!!!  I can't get into my desktop!

I even tried installing Kubuntu on some extra partitions that I am not using to see if that would help.  No go!
I can do the whole:

```

grub rescue> set prefix=(hd1,8)/boot/grub
grub rescue> set root=hd1,8

```

but the second I do:

```

grub rescue> insmod /boot/grub/linux.mod

```

I get:

```

error:the symbol `grub_puts_' not found

```

Please, anyone, we need some help here!

---

### Post by Cyclops_ on 2010-05-01
Here are some other things that I have tried:


[LIST=1]
[*]Tried to install a copy of Kubuntu Lucid Lynx to an unused partition.
[*]Use a LiveCD to fix Grub by doing an update-grub
[*]Use a LiveCD to fix Grub by doing a dpkg-reconfigure grub-pc and selecting ALL partitions.
[*]Tried using the grub rescue> prompt to boot from another partition.
[*]Tried loading as many .mod's as I could from /boot/grub, but it still doesn't give me the 'grub_puts_' symbol...  maybe I'm not finding the right .mod.
[/LIST]
PLEASE!!!!!!!!!!!!!!!
This is INCREDIBLY IMPORTANT that I get my computer back up and running!  Without it I cannot work!

THANK YOU!

---

### Post by s.chiu on 2010-05-01
Also suffering from this problem.  I'm going to try going back to the old grub (0.9x), see if that works.

---

### Post by s.chiu on 2010-05-01
OK, I've got Windows back by installing grub again:

```

apt-get install grub
grub
#hd0,1 is sda2 - my linux partition
root (hd0,1)
setup (hd0)
quit

```

Then configuring menu.lst in /boot/grub...

```

title Windows7 
root		(hd0,0)
chainloader	+1

```
seems to work for Windows - still trying to rebuild it for Linux.  I can boot to a shell (BusyBody I think) but I don't really know what to do from there.
I can't see my menu.lst from Windows, unless Win7 has a hidden ability to mount ext3, so I can't post my exact settings here...

Hope this helps some people, also, if anyone can paste in here the right stuff needed in menu.lst to boot Lynx that would be appreciated.

---

### Post by fabrizio.benedetti on 2010-05-01
I have the same issue; using SuperGrubDisk I can boot, but I am not able to reinstall GRUB: I tried removing grub-common and grub-pc packages, then reinstall them again, but to no purpose, I always get the grub_puts_ not found error...

please help us!

---

### Post by s.chiu on 2010-05-01
Now posting from Lucid!  Here's the menu.lst I used:
```

default=0
timeout=5

title Linux Ubuntu Lucid
root (hd0,1)
kernel /boot/vmlinuz-2.6.32-21-generic ro root=/dev/sda2
initrd /boot/initrd.img-2.6.32-21-generic
boot

title Windows7
rootnoverify (hd0,0)
chainloader +1

```

I hope this helps some people... I didn't have any problems reinstalling grub, though.  If anyone can offer tips for getting grub2 to work, I'd be interested in trying it.

---

### Post by fabrizio.benedetti on 2010-05-01
I got it working too! I removed and reinstalled Grub-pc (GRUB2!) some more time, and voila, it's working now...

I think the main issue was selecting the right entry for installing grub to: /dev/sda succeded, /dev/sda5 didn't 

ok, now on to reconfiguring my Nvidia card!

Ciao!

---

