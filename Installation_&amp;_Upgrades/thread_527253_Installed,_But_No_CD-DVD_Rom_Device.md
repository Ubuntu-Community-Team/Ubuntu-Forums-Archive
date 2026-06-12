---
title: "Installed, But No CD-DVD Rom Device?"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by pcboy123 on 2007-08-16
Hello everyone.. first of great OS im new to this... I only have one lil problem how do i get my CD-DVD Rom Device to mount.. i tried the forums and the tips and tricks they got but no luck..

---

### Post by jnorthr on 2007-08-16
i would have expected them to auto load if you have a recent  machine with plug and play technology. What happens when you put a music cd into the drive and close the door ? Does ubuntu give you an icon on your desktop ?

---

### Post by pcboy123 on 2007-08-16
No nothing... shows any external usb device i have connected

---

### Post by dabl on 2007-08-16
Does /etc/fstab show any sign of a CD/DVD drive?  If so, make a /media/CDR_Drive directory and mount it there.

---

### Post by pcboy714 on 2007-08-16
it doesnt let me run /etc/fstab say permission failed

---

### Post by pcboy714 on 2007-08-16
this wat comes up:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5d652f77-1b4f-4886-b526-fd4420b5df68 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=482a571e-d753-4080-829a-f2d6f07d3e8c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by dabl on 2007-08-16
> **pcboy714 said:**
> this wat comes up:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



Well, right there is a problem.  Removable optical drives should be numbered in the "scxx" device series, not the "hdx" series, which is reserved for hard IDE drives.

I don't know what the consequences will be, so make a backup copy of your fstab file, and then edit this one and change that "hda" to "scd0", save it, and reboot your system.  I'll burn some chicken feathers ... :lolflag:


EDIT: I have the impression there are more partitions or more drives missing from this picture ... what is between sda1 and sda5, for example?

---

### Post by pcboy714 on 2007-08-16
yeah i have dual boot with vista...

---

### Post by dabl on 2007-08-16
OK.

You're not trying the old "unplug drive x while installing Linux on drive y" are you?

---

### Post by pcboy714 on 2007-08-16
nope.. 
Vista reads the drive.. and i can install Ubuntu off it also but once the os loads it dont see the drive...

also im use generic video drivers can that cus a problem i need to install video drivers for Nvidia Quadro NVS 140M

---

### Post by dabl on 2007-08-16
It's weird that the /etc/fstab file was built without the other partitions showing, but that's not really a problem unless you need access to them from Linux.

The latest Nvidia driver (100.14.11) will run your new Quadro card.  I use "Envy" to install my Nvidia driver (I'm lazy).

Try the edit on your CD ROM device in fstab, as I suggested -- it could work, and won't likely make it worse.  :)

---

### Post by pcboy714 on 2007-08-16
I did ... it didnt work

---

### Post by dabl on 2007-08-16
Have you gone into the "Admin>Preferences>Hardware Info" utility, to see what it shows about your optical drive?

---

### Post by pcboy714 on 2007-08-16
It dont show nothing..

---

### Post by dabl on 2007-08-16
OK, I'm trying to mentally switch between Kubuntu and Ubuntu, so I may get this wrong.

In the Ubuntu "Adminstration>System Adminstration" menu, I think there is a "Mount" utility.  Can you find that?  Does it provide an ability to look at storage devices, and see if they are mounted?  It may be that you only need to mount /dev/scd0 on /media/cdrom (approximately).

---

### Post by pcboy714 on 2007-08-16
no theres no app under that name nor in add.remove download selection

---

### Post by dabl on 2007-08-16
Meh -- and I'm stuck at the office in front of a Win-trash piece of junk!

OK, put a non-bootable CD in that drive, like a music CD, and see what happens.

If nothing happens when you do that, if you left your fstab with the /dev/scd0 device, defined as a UDF cdrom, then you can open a console window and try this:

```
sudo mount -t /dev/scd0 /media/cdrom0
```

I don't remember whether CD ROM drives need a filesystem type specified or not.  If it does, then it would be

```
sudo mount -t udf /dev/scd0 /media/cdrom0
```

---

### Post by pcboy714 on 2007-08-16
> **dabl said:**
> Meh -- and I'm stuck at the office in front of a Win-trash piece of junk!

OK, put a non-bootable CD in that drive, like a music CD, and see what happens.

If nothing happens when you do that, if you left your fstab with the /dev/scd0 device, defined as a UDF cdrom, then you can open a console window and try this:

```
sudo mount -t /dev/scd0 /media/cdrom0
```

I don't remember whether CD ROM drives need a filesystem type specified or not.  If it does, then it would be

```
sudo mount -t udf /dev/scd0 /media/cdrom0
```

I get this msg:
mount: special device /dev/scd0 does not exist
after i do 
```
sudo mount -t udf /dev/scd0 /media/cdrom0
```

i would like to get this drive working so i can install envy =-) the lazy way

---

### Post by pcboy714 on 2007-08-16
i ran gedit /etc/fstab in terminal i got this 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=5d652f77-1b4f-4886-b526-fd4420b5df68  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=482a571e-d753-4080-829a-f2d6f07d3e8c  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda1                                  /media/sda1    ext3         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda5                                  /media/sda5    swap         defaults                    0  0  

---

### Post by pcboy714 on 2007-08-16
<Solved>
Adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

It works for me!

Thank you for your time... this lil trick should be a PIN.
or in FAQ
...

---

### Post by dabl on 2007-08-16
OK, let's try again (Google is such a friend!)

With a CD in the drive, in the console, ```
sudo mount -t iso9660 -o ro /dev/scd0 /media/cdrom0
```


On Envy, you don't need the CD ROM drive, you need to download it from [[COLOR="Magenta"]**here**[/COLOR]](http://albertomilone.com/nvidia_scripts1.html)

You want the file "envy_0.9.7-0ubuntu8_all.deb" which is about halfway down the page.  Download it to your desktop, then right-click and "GDebi Install" it.  It should end up as an icon in your System menu.

---

### Post by pcboy714 on 2007-08-16
**[SIZE="6"]<Solved>[/SIZE]**
Adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

It works for me!

Thank you for your time... this lil trick should be a PIN.
or in FAQ

---

### Post by dabl on 2007-08-16
Excellent!

Good luck with that Quadro -- I'm kinda jealous of that one.   :guitar:

---

### Post by pcboy714 on 2007-08-16
well it installed the nvidia drivers i think.. it restarted  just dont know how to check or change settings./..

yeah its a Quadro 256mg card top of the line for dell latitude model

---

### Post by pcboy714 on 2007-08-16
> **pcboy714 said:**
> well it installed the nvidia drivers i think.. it restarted  just dont know how to check or change settings./..

yeah its a Quadro 256mg card top of the line for dell latitude model

nevermind i found the settings.. =-) okay im happy now..

---

### Post by dabl on 2007-08-16
To enable Compiz Fusion or Beryl, you'll need glx enabled.

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```


To change the default resolution and refresh rates:

```
sudo nvidia-settings
```

On the "X Configuration" panel, first do "detect display", then set resolution, then set refresh rate, then in the lower right click the "Save To X Configuration File" button, then "save" and you're done.

---

### Post by pcboy123 on 2007-08-16
yeah i got it working now. all i need is the verizon broadband card to work.. =)

---

