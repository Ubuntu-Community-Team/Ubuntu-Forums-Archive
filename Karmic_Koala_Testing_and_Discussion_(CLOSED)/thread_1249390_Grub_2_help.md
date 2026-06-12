---
title: "Grub 2 help"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2009-08-25
I used to have grub call a conigfile to another disk.  I have no idea how to do this with grub 2, since there seems to be no menu.lst in /boot/grub.

I searched for half an hour on the web and could not find any specifics on how to do this.

Anyone know how to convert/where to save something like this?

[INDENT]title  Chakra
configfile (hd3,1)/boot/grub/menu-1.lst[/INDENT]

---

### Post by drs305 on 2009-08-25
Custom entries for the grub 2 menu are now placed in /etc/grub.d/40_custom and are entered into the grub menu after "update-grub" is run.

Click on the "Grub 2" link in my signature line for a post on "Grub 2 Basics", which explains the new files associated with Grub 2.

---

### Post by petteriIII on 2009-08-25
If you edit /boot/grub/grub.cfg by hand the configfile(hdx,y)/boot/grub/grub.cfg command operates, sort off.
But editing grub.cfg is best to begin by making two (=2) copies of grub.cfg, editing sensibly by 'baby steps' and it is recommended to have fresh Karmic live-CD at hand so that you can undo editing by CHROOt:ing to your non-booting Karmic. 
But living in danger-zone is good. If you have time and patience.

---

### Post by maestrobwh1 on 2009-08-25
I guess I am kind of dumb here, because after reading, I still don't know what to do to add my entry.  Does grub2 even support the "configfile" call?

Grub 2 is totally different than what I am used to.  It is perhaps better, but before, i had one file to deal with, now there are significantly more.

I assume I create a new file in /etc/grub.d; however, I am lost with the syntax after the "setroot" line in your example so this is the best guess:


echo "Adding Chakra Arch" >&2
cat << EOF
menuentry "Chakra Arch" {
**set root=(hd3,1)**
**configfile /boot/grub/menu-1.lst**
}
EOF

---

### Post by drs305 on 2009-08-25
The Grub 2 post was meant just to explain the basics of the way the new grub process works. I don't have any experience using configfiles, but this post deals with lots of Grub 2 configuration issues, and discussions of configfiles begins in post 15. 
[http://ubuntuforums.org/showthread.php?t=1223280#15]("http://ubuntuforums.org/showthread.php?t=1223280#15")

---

### Post by maestrobwh1 on 2009-08-25
Thanks - post #15 there:

"We can't use the configfile command between the two different GRUBs because they are so different that GRUB Legacy can't understand GRUB 2's grub.cfg and GRUB2 can't understand menu.lst."

So beyond this, how would I make an entry in /etc/grub.d/ that would find the kernel, say (hd3,1)

Here is the menu.lst in that disks /boot/grub/menu.lst

title  Chakra
kernel /boot/vmlinuz vga=791 lang=en nonfree=yes quiet
initrd /boot/chakra.img

the UUID for the disk (vfat - I use an image with larch doing a session save to an SD card) is 808F-F6D2 but I think that is irrelevant here.

#!/bin/sh
echo "Adding Chakra Arch" >&2
cat << EOF
menuentry "Chakra Arch" {
set root=(hd3,1)
linux /boot/vmlinuz vga=791 lang=en nonfree=yes quiet
initrd /boot/chakra.img
}
EOF

---

### Post by ranch hand on 2009-08-25
You need to go to the link in drs305s sig and create a custom entry.

You need to keep in mind that the number for the drive is the same in grub2 as grub-legacy but the number for the partition is now the same as gparted uses.

Here is a couple of custom entries of mine;
```

echo "Adding Jaunty on sda8" >&2
cat << EOF
menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
        linux /boot/vmlinuz-2.6.28-14-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
        initrd /boot/initrd.img-2.6.28-14-generic
}
EOF

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

``` 
Here are acouple of other handy links;

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

Grub2 is very different and a work in progress.  I think it is going to be great.

If you search this forum (testing) you will find a lot of information and probably a lot of confusion.  A teacher of mine, back in the 60s (hey, so I'm a geezer) said that confusion is the foundation of learning.

HAVE FUN

---

### Post by maestrobwh1 on 2009-08-25
Being a HS chemistry teacher, I can relate, but my students don't seem to subscribe to the point of view beyond minimal frustration.

---

### Post by ranch hand on 2009-08-25
I assuume that your system was booting before.  If that is the case, it will boot now.

Editing the 40_custom file is where you are supposed to edit and will not hurt a thing.

Those entries may not work but the rest should.

Double entries is a common problem and I hope it is corrected soon.

The last entry that I gave in my sample should, with editing to your system, work on any OS.  You may want to try that if what you have does not work.

You may need to add;
```

set root=(hd3,1)

```
in any entries (see possition in my first example).

I would try that on the entries that you have if they do not work as a first try in fixing them.

You can add a document to grub.d.  This would be the same as you 40_custom file with a name like 06_custom.  This will put yoour custom entries at the top instead of the bottom of your menu which is where 40_custom will put them.

---

### Post by maestrobwh1 on 2009-08-25
Yes, Kubuntu was/is booting.  I have not tried WindowsXP yet but that takes forever to boot and I rarely use it anyway.

I was getting "file not found" for the 40_custom added entries so I will try adding *set root=(hd3,1)* and post back.  

The double entry: I just commented out what was in 30_otheros.  The automatic script was adding windows and 30_otheros was adding them again.

I guess I am a bit savvy to figure that last bit out.

---

