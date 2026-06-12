---
title: "2 hard drives, 2 OS"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by dethsqurl86 on 2007-01-11
Hi im using ubuntu for the first time ever to broaden my horizons and because ive hear so many good thing about it.  I have a 2 80GB hard drives in my box.  xp is installed on a prim partition on 1 and ubuntu is installed on the other.  the XP hd is the slave on IDE 1 and the ubuntu HD is the master on IDE 2.  My problem lies in te fact that i had windows installed first and i installed ubuntu on the 2nd hard drive. Now whenever i load i can't see windows in the grub loader and i cant access windows at all even if i try to boot from the hd itself. I would appreciate any help, remember I have been using ubuntu for about 2 days so I dont really know alot about its functions yet.

---

### Post by Paerez on 2007-01-11
OK, press Alt+F2 to bring up the "Run Application" window.

Type in:
gksudo gedit

put in your PW if necessary.

Then click "Open" and type this in the location:
/boot/grub/menu.lst

Find the line:
```
hiddenmenu
```
and replace it with:
```
#hiddenmenu
```

Find the line:
```
timeout        3
```
and replace with:
```
timeout 10
```

at then end, paste this in:
```
title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

Then save, close, reboot.

Good luck!

---

### Post by dethsqurl86 on 2007-01-11
Ok ty for the simple instructions. I followed them and rebooted and hit windows xp in the boot menu the system went for a second and then i got a screen saying startin up..... and it hangs there. :(


After reading a few posts i found some helpful information that might mean more to an experienced user unlike myself.  

my XP Hd is loacated at /dev/hdc1

if that helps at all

---

### Post by Paerez on 2007-01-11
oh ok, change the line:
root		(hd1,0)

to
root		(hd2,0)

in the Windows XP entry.

---

### Post by dethsqurl86 on 2007-01-11
ok did that and all i got was a screen telling me taht the selected disk does not exist.

---

### Post by Paerez on 2007-01-11
can you paste me the output to:
```
$sudo fdisk -l /dev/hdc
```

---

### Post by dethsqurl86 on 2007-01-11
disk /dev/hdc: 80.0GB 80090424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
units= cylinders of 15120 * 512 = 7741440 bytes

       Device Boot             Start              End         Blocks     Id    System
/dev/hdc1      *                     1          10340    78170368+     7     HPFS/NTFS



Do you think that their was a problem when installing the grub loader that could cause this?

Im downloading the livecd right now b/c i was using a friends so i will have the livecd shortly

---

