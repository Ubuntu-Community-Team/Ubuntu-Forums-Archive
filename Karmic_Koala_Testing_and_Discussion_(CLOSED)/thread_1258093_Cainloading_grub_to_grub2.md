---
title: "Cainloading grub to grub2"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kelean on 2009-09-04
I installed 9.10 alpha5 and installed grub2 to the root partition.  I then added Karmic to the menu.lst so I could chainload ubuntu.
It came up with the following error.

```

File system type is ext2fs type 0x83

error 13 invalid or unsupported executable format
```


```
title Ubuntu 9.10
root (hd0,8)
chainloader +1
```

I dont know what the problem is, unless grub partition in ext3 and new ubuntu install is ext4.

Thanks Kelean.

---

### Post by VMC on 2009-09-04
> **kelean said:**
> I installed 9.10 alpha5 and installed grub2 to the root partition.  I then added Karmic to the menu.lst so I could chainload ubuntu.
It came up with the following error.

```

File system type is ext2fs type 0x83

error 13 invalid or unsupported executable format
```


```
title Ubuntu 9.10
root (hd0,8)
chainloader +1
```

I dont know what the problem is, unless grub partition in ext3 and new ubuntu install is ext4.

Thanks Kelean.

Did you store the boot information on that 8th partition?

---

### Post by kelean on 2009-09-04
I have ubuntu installed on the 9th partition.

---

### Post by kansasnoob on 2009-09-04
So you have a multi-boot? Please describe your OS layout.

---

### Post by kansasnoob on 2009-09-04
> **kelean said:**
> I have ubuntu installed on the 9th partition.

Please describe the whole set up.

It sounds like you installed Karmic and you're now trying to boot it from grub-legacy on another OS.

---

### Post by kelean on 2009-09-04
Here is my whole menu.lst.


```

timeout 60
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at sda5, newest kernel
root (hd0,4)
kernel /boot/vmlinuz root=/dev/sda5 nomce quiet splash vga=791 resume=/dev/sda6  
initrd /boot/initrd.img
boot

title MEPIS at sda5, previous kernel (if any)
root (hd0,4)
kernel /boot/vmlinuz.old root=/dev/sda5 nomce quiet splash vga=791 resume=/dev/sda6  
boot

title MEPIS at sda5, kernel 2.6.27-1-mepis-smp
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-1-mepis-smp root=/dev/sda5 nomce quiet splash vga=791 resume=/dev/sda6  
initrd /boot/initrd.img-2.6.27-1-mepis-smp
boot

title Microsoft Windows XP Professional at sda1
rootnoverify (hd0,0)
chainloader +1

title Slackware
root (hd0,6)
chainloader +1
```

Grub is installed from Mepis.  Added slackware and then Ubuntu.

I installed grub2 to the root partition when I installed Ubuntu.

---

### Post by kansasnoob on 2009-09-04
You don't understand what I'm asking.

Grub2 doesn't have a menu.lst. So, you've installed Karmic w/grub2 and now you've chosen to use legacy-grub from another OS, I think.

Is that right?

I guess I can look at your menu.lst to get some clues.

---

### Post by kansasnoob on 2009-09-04
So you have Win, Simply MEPIS and Slackware and now you want to boot Karmic using legacy grub?

I couldn't do it. I had to revert Karmic to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Now, I need to update that a lot! But I'm still doing some testing!

OTOH, I think grub2 should be able to boot all OS's!

EDIT: I'm fighting other fires right now, so it'll be a while before I get that updated!

---

### Post by kelean on 2009-09-04
Yes, that is correct.  I have winxp installed first.  Second, installed mepis8 which has grub.  I then installed ubuntu 9.10 and put the bootloader in the root partition  Karmic uses grub2.  I dont think it matters but mepis uses ext3 file system,  Ubuntu uses ext4 file system.  The only problem mepis does not reconiges ext4 file system.  I am not able to mount the ubuntu partition.

I hope that is what you are looking for, Kelean.

---

### Post by kelean on 2009-09-04
I want to boot ubuntu by chainloading.  The way it should work is ubuntu will boot with grub2.  I did that with slackware.  It boot with lilo.  Ir has lilo installed slack's root partition.

If grub2 is installed on ubuntu's root partition then I point to that partition from my grub that is installed in the MBR.  

Is there something I am missing in my grub entry?

---

### Post by kansasnoob on 2009-09-04
And I'm not saying it can't be done, I just couldn't figure it out. I had to revert Karmic to grub-legacy to be able to boot from grub-legacy on another OS.

You can look here regarding grub2:

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by kelean on 2009-09-05
I changed my entry in my menu.lst for ubuntu.

title Ubuntu 9.10
set root=(sd0,8)/boot/grub/grub.cfg
chainloader +1


Now I do not get any errors.  Just get two lines at the top of the screen that say:
chainloding +1
grub

I cannot do any thing except ctrl-alt-del to reboot.

I have no more errors, I think that's a good thing.

Kelean

---

### Post by ranch hand on 2009-09-06
If you are up and running I can make a "smart" comment.

I like the idea of "Cainloading".

I suppose when you do this you can beat the bugger if it doesn't work.  I could use that.

---

### Post by kelean on 2009-09-06
Yes it is very handy.  Once you have grub installed properly. Then all you need to do is to edit your menu.lst file to point to the root partition where the new grub resides.

Here is some more info about chainloading:

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Chainloading_in_Linux]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Chainloading_in_Linux")

Lots of good information in there.

Kelean.

---

### Post by ranch hand on 2009-09-06
Of darn, I thought we were cain loading.  This usualy involves adding lead to the cain to make it heavier.

---

### Post by kelean on 2009-09-06
Well cainloading could be very useful.  I could one on occasion.

---

### Post by VMC on 2009-09-07
> **ranch hand said:**
> Of darn, I thought we were cain loading.  This usualy involves adding lead to the cain to make it heavier.I prefer sugarcain loading myself :)

Back on topic. This is a clever way of getting to grub2. I guess the reverse would work also:
```
title Ubuntu 9.10
set root=(sdxx,/boot/grub/grub.cfg)
chainloader +1
```

---

### Post by BwackNinja on 2009-09-08
```
title		Chainload into GRUB 2
root		(hd#,#)
kernel		/boot/grub/core.img
```

Taken from my old menu.lst when it was set up to chainload grub2 when we were all testing it before I made it default.

---

### Post by philinux on 2009-09-08
I'm still using this.

```
title        SDB Karmic
root (hd1,0)
chainloader +1

```

---

### Post by kelean on 2009-09-12
I tried to install grub2 to the root partition 3 times.  I could not get it to boot.  I used many different ways in my menu.lst.  I got really tired and frustrated.  I gave in and installed grub2 to the mbr.  It works perfectly for me.  I ran sudo grub-update and if found all of my other installs.  I am able to start win, mepis, and slackware.  I did not have to edit anything.

---

