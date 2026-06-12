---
title: "Dual-boot - Installed Ubuntu, XP disappeared?!"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by leeandrews_uk on 2006-03-30
Hey, so I'm a very new linux user, but I'm slowly getting the hang of it so please bear with me!

I had Windows XP installed on my hard disk, and intended to put ubuntu on the same hard disk (new partition) as a dual boot for development purposes. This seemed to work just fine, installation seemed to go smoothly, and ubuntu booted in without error.

The problem occured however when I tried to reboot and use the GRUB loader to boot back into Windows. Upon loading the list of O/S, XP was not there, and as such cannot be booted. The original XP partitions are still there as my C:/ drive appears on the U desktop as 'sda1' - although is not accessible due to NTFS and file permissions etc - and I mounted my other partition into U.

Is this a case of just modifying GRUB to see Windows again, or have I screwed up the MBR? Ideally I'd like to avoid having to re-install XP So what do I have to do to get around it?

I'm using ubuntu 5.10 if that makes a difference.

Thanks in advance.

Lee

---

### Post by beerorkid on 2006-03-30
yup just have to edit menu.lst

```
sudo gedit /boot/grub/menu.lst
```

add this somewhere

```
title        Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```

this had messed with me a few times as well

You may need to change the line starting "root" to wherever your windows partition is. Remember that you just have to start all over if windows is not in the beginning of the hard drive. Microsoft requires its OS to be in the first few Gb, not necessarily the first partition

---

### Post by leeandrews_uk on 2006-03-31
Sweet... made the changes and works just fine! Cheers for your time.

Lee

---

### Post by joeuser1 on 2006-04-03
I need help on this too! I gave up on installing Ubuntu Breezy because XP didn't load. hal.dll missing. I had to fix it by repairing it with the XP CD. I installed Ubuntu 3 times and XP twice in a single day. Then I gave up.

Does your GRUB modification fix this hal.dll error? Please show me a way!

Diwakar

---

### Post by beerorkid on 2006-04-03
well I do not really know.  What I posted above is a fix for when the XP gets bumped out of the menu.lst, so it is not a fix for that.  I will look around though.

---

### Post by beerorkid on 2006-04-03
hmmmm...... a few threads with some ideas:

[http://ubuntuforums.org/showpost.php?p=610544&postcount=6](http://ubuntuforums.org/showpost.php?p=610544&postcount=6)

[http://www.ubuntuforums.org/showpost.php?p=426634&postcount=6](http://www.ubuntuforums.org/showpost.php?p=426634&postcount=6)

seems like it is possibly hard drive related or a messed up /boot/grub/menu.lst

sorry I cannot help more.

---

### Post by joeuser1 on 2006-04-04
Lotsa thanks for the links. One of 'em suggests that the hal.dll error could be overcome with editing the boot.ini.

Cheers!
Diwakar

---

### Post by beerorkid on 2006-04-04
yeah that is one of the easier ways to fix it.  hope it helps.

I hardly ever get into my XP partition anymore, but sometimes when I do it hangs and I have to hard reboot to get it back up again.

Gotz to be able to play my games every now and then ;)

---

### Post by juliovg on 2008-02-11
I have a similar problem, but in my case no c partition appears
so I cannot boot from xp, I check and this is what I got

julio@julio-laptop:~$ df -k
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda2              3842408   2022680   1624540  56% /
varrun                  253796        92    253704   1% /var/run
varlock                 253796         0    253796   0% /var/lock
udev                    253796        72    253724   1% /dev
devshm                  253796         0    253796   0% /dev/shm
lrm                     253796     34696    219100  14% /lib/modules/2.6.22-14-generic/volatile
julio@julio-laptop:~$ df -k

any clue on this

---

