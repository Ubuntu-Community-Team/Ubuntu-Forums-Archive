---
title: "Grub2 &amp; MS-DOS 6.22"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by sefs on 2010-12-30
Hi there,

I am trying to boot a partition I have here that has MS-DOS 6.22 on it.  But it is not working.

Is this possible?  What I have is ...

```

menuentry "Microsoft MS-DOS 6.22" {
	insmod vfat
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set xxxx-xxxx
	chainloader +1
}

```

---

### Post by coffeecat on 2010-12-30
> **sefs said:**
> ```

    insmod vfat

```

There is no vfat.mod in /boot/grub, but there is a fat.mod. Try:

```
insmod fat
```

---

### Post by sefs on 2010-12-31
> **coffeecat said:**
> There is no vfat.mod in /boot/grub, but there is a fat.mod. Try:

```
insmod fat
```

That was  a big help thanks.  I think it is now finding the partion correctly but now saying it is not a system disk and gives me the opportunity to enter a boot disk.  I do and i cant change to drive c:.  If i fdisk i can see the C: drive as a pri dos but when I go c: it says Invalid drive specification.

my updated cfg is such...

```

.
.
#Entry 2
menuentry "Microsoft MS-DOS 6.22" {
	insmod fat
	drivemap (hd0) (hd1)
	drivemap (hd1) (hd0)
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set xxxx-xxxx
	chainloader (hd1,2)+1
}
.
.

```

---

### Post by coffeecat on 2010-12-31
I've never put  a Microsoft OS on anything but the first disc, but I wonder if there is something in this part of the grub2 manual that might help you:

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by sefs on 2010-12-31
> **coffeecat said:**
> I've never put  a Microsoft OS on anything but the first disc, but I wonder if there is something in this part of the grub2 manual that might help you:

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

Yup that is where I got the drivemap from, I tried with the hiding stuff, but it change all the partions to type ameboa :S.

---

