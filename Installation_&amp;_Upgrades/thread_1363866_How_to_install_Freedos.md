---
title: "How to install Freedos"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by linsq109 on 2009-12-25
i got a method is by unetbootin, but seems that i should install on USB(for if i choose harddisk, it always choose C:\, but C:\ is my windows 7.)
 
so i run unetbootin under ubuntu9.04,
just as follwing picture
select freedos iso file pic-1
select usb drive pic-1
copy....autuomatically pic-2
reboot
 
press [tab] to edit option, pic-3
so if i choose freedos, just as pic-4
if i choose fdos just as pic... long time "initdisk....." pic-5
so i don't know how to intall freedos in my USB drive or Harddisk
i dont intend to install it in virtual enviroment
i also try it in my windos OS the same result
any one can help me
 
any other method is OK~~~
 
thanks

---

### Post by rCXer on 2009-12-25
Here's how I dualboot Ubuntu and FreeDOS on my hard drive.  I have also used [this method](http://www.etherboot.org/wiki/appnotes/make_usb_drive) to make FreeDOS thumbdrive from windows.

0.  Backup anything important!  Just in case a mistake is made.

1. Create a 1GB fat32 partition for FreeDOS.  A partition can only be edited if it is unmounted. If you plan to edit the partition Ubuntu on you have to do this from its live cd. 

Graphical partitioners are easier to use. Get gparted using...
```

sudo apt-get install gparted

```
-Start gparted. System -> Administration -> Partition Editor
-Make a 1GB fat32  partition by either [resizing an existing one](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition) or [creating a new one](https://help.ubuntu.com/community/HowtoPartition/CreatingPartitions).
-Note your new partition's number.  For example, if the "partition" column contains "/dev/sda3", the partition number is 3.

2. [Download](http://www.freedos.org/freedos/files/) and [burn](https://help.ubuntu.com/community/CdDvd/Burning) a FreeDOS LiveCD using any tool.

3. Install FreeDOS.  [This video](http://www.youtube.com/watch?v=sIxK9qO95p8&feature=player_embedded%20target=) should be helpful to watch.  You should not repartition the drive since this was done in step 1.
- Insert it into your CD drive and restart your computer.
- When the FreeDOS splash screen with the fish appears, select "1" to boot FreeDOS from the LiveCD. Select "1" on the next screen to Install it.
- Follow the on screen instructions and FreeDOS should install itself to your fat32 partition.

4. Add FreeDOS to your grub bootloader menu.
- Backup and edit your menu.lst...
```

sudo cp "/boot/grub/menu.lst" "/boot/grub/menu.bak"
gksudo gedit "/boot/grub/menu.lst"

```
- Add the following to the file...
> 
title FreeDOS
root (hd[COLOR="Red"]x[/COLOR],[COLOR="Blue"]y[/COLOR])
savedefault
makeactive
chainloader +1

- Change the line "root (hd[COLOR="Red"]x[/COLOR],[COLOR="Blue"]y[/COLOR])" to match where FreeDOS was installed. [COLOR="Red"]x[/COLOR] tells which hard drive FreeDOS was installed on.  It should be 0, since this is your main hard drive. [COLOR="Blue"]y[/COLOR] is the partition it was installed on.  It should be _**one less**_ than the partition number you found in step 1.  For example on my system, FreeDOS was installed on "/dev/sda3". Therefore [COLOR="Blue"]y[/COLOR] is 2...
```

root (hd0,2)

```
- Save menu.lst and restart the computer. Select "FreeDOS" from the menu. If it doesn't work, try different values for x and y.

---

### Post by linsq109 on 2009-12-26
according to your help,
 
i burn iso image CD 153M(fdfullcd.iso)
and boot from CD,
Fisrt Screen select "1" for install freedos,
then long time the following Page "checking for CDROM driver or C:\fdbootcd.iso....
as follwing (PIC)
 
 
3. Install FreeDOS. [This video]("http://www.youtube.com/watch?v=sIxK9qO95p8&feature=player_embedded%20target=") should be helpful to watch. You should not repartition the drive since this was done in step 1.
- Insert it into your CD drive and restart your computer.
- When the FreeDOS splash screen with the fish appears, select "1" to boot FreeDOS from the LiveCD. Select "1" on the next screen to Install it.
- Follow the on screen instructions and FreeDOS should install itself to your fat32 partition.
 
4. Add FreeDOS to your grub bootloader menu.
- Backup and edit your menu.lst...
```

sudo cp "/boot/grub/menu.lst" "/boot/grub/menu.bak"
gksudo gedit "/boot/grub/menu.lst"

```
- Add the following to the file...
 
- Change the line "root (hd[COLOR=red]x[/COLOR],[COLOR=blue]y[/COLOR])" to match where FreeDOS was installed. [COLOR=red]x[/COLOR] tells which hard drive FreeDOS was installed on. It should be 0, since this is your main hard drive. [COLOR=blue]y[/COLOR] is the partition it was installed on. It should be _**one less**_ than the partition number you found in step 1. For example on my system, FreeDOS was installed on "/dev/sda3". Therefore [COLOR=blue]y[/COLOR] is 2...
```

root (hd0,2)

```
- Save menu.lst and restart the computer. Select "FreeDOS" from the menu. If it doesn't work, try different values for x and y.[/quote]

---

