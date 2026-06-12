---
title: "Stupid Question.. :D"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by Enzo. on 2011-03-01
Well Hello, Since im total noob in lunux OS I would like to ask something

I've found some codes on the net, like how to mount .iso image etc.

Code:
BASH# mount youriso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0

And the problem is I don;t know where to put 'em (How to run them) Any help?

THank you

---

### Post by zenwalker on 2011-03-01
Find terminal from your menus and paste it there.

Btw thats called command. Not code.

---

### Post by kc1di on 2011-03-01
I'm not sure why you would want to mount and ISO Usually you just burn them to a cd or DVD disk using your cd burning software and burn image mode.

But in any event the code you posted would be run from a terminal as root.

---

### Post by matt_symes on 2011-03-01
Hi

> **Enzo. said:**
> Well Hello, Since im total noob in lunux OS I would like to ask something

I've found some codes on the net, like how to mount .iso image etc.

Code:
BASH# mount youriso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0

And the problem is I don;t know where to put 'em (How to run them) Any help?

THank you

You need to enter statements like that in the terminal. 
From the menu: Applications->Accessories->Terminal.

You will need to create the mount point.

```
sudo mkdir /mnt/iso
```

Enter your password you will not see it echoed to the screen.

youriso.iso will need to be the full path to your iso if not in the same directory.

you will also need sudo infront of the command

```
sudo mount /path/to/youriso.iso /mnt/iso/ -t iso9660 -o ro,loop=/dev/loop0
```

Unmount when finished

```
sudo umount /mnt/iso
```

Or you could use the archive mounter. Right click on the iso in Nautilus and select open with->archive manager.

Kind regards

---

