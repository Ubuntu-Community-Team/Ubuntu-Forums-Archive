---
title: "missing hard drive space"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by Douglas Drake on 2005-10-07
last week, i installed ubuntu on my labtop, a ibm thinkpad t21. the labtop came with a 15gb hard drive, but i took that out and put in a 30gb hard drive instead.

the problem:

currently, my file system says it takes up 8.1gb. but it also says i only have 16.9gb free space left. that adds up to 25gb.

my question:

what happened to the other 5gb of hard drive space? 

i have an hda1, hda2, and hda5. are one of these perhaps a unwanted windows partition (i did a clean install)? i have 256 mb ram, would swap space being taking up all that extra space? whats the deal.

help me please,

Douglas Drake
ibm thinkpad t21
ubuntu linux 5.04: the hoary hedgehog

a linux newbie

ps. also, what is hda1, hda2, and hda5 exactly? which one is swap space, my root volume, etc? are these standand ubuntu hda's?

---

### Post by SilentCacophony on 2005-10-07
Hi. We can't answer much of that without more details.

Looks like some of your drive space may be unallocated, for one.

If you're on ubuntu, open the applications>accessories>terminal, and enter:

**sudo fdisk -l**

and paste the output back here

doing the same with

**df**

might help too

---

### Post by Douglas Drake on 2005-10-07
hiya. thanks for the quick reply. here is the info you asked for:


~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3555    28555506   83  Linux
/dev/hda2            3556        3648      747022+   5  Extended
/dev/hda5            3556        3648      746991   82  Linux swap / Solaris


~$ df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             28107164   8943240  17736152  34% /
tmpfs                   128404         0    128404   0% /dev/shm
/dev                  28107164   8943240  17736152  34% /.dev
none                      5120      2820      2300  56% /dev

---

### Post by SilentCacophony on 2005-10-07
Hmm. By the fdisk output, it looks as if it's as it should be, with the / (root) on hda1, and the swap on an extended hda5, with the swap being about triple your ram, which is no real problem.

the df output is odd, though. The las two entries make no sense to me. Can you post the output of this as well:

**cat /etc/fstab**

That'll show what mount points you have set up automatically.

---

### Post by Douglas Drake on 2005-10-07
here ya go:


~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by SilentCacophony on 2005-10-07
Well, that looks just fine. I don't get the results of the **df** command, though. Are you sure that was a clean copy-n-paste?

I've never seen anything like this part of it:

/dev 28107164 8943240 17736152 34% /.dev
none 5120 2820 2300 56% /dev

If that's what you got, I'd like to see the result of a

**mount**

as well.

---

### Post by Douglas Drake on 2005-10-07
i just double checked the copy-paste. it's all clean. those are indeed the results my terminal prints out. as i said, i did a clean ubuntu install, selecting whatever defaults for the installation it gave me.


~$ mount

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

---

### Post by SilentCacophony on 2005-10-07
Well, I don't know how or why these two entries are there:

/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)

Neither one looks right to me.

Have you rebooted since the installation? You could try a reboot with a forced disk check by doing so:

**sudo shutdown -r -F now**

which is case sensative. If your **df** results look the same after that, I'm not sure what is happening there.

---

### Post by Douglas Drake on 2005-10-07
hi again. i just ran the **shutdown **command. then** df **again. same thing, it hasn't changed. 

earlier today, i was playing around with mounting hda1,2,5 when i was trying to figure out what they were. i originally thought perhaps one of them was a windows partition that wasn't deleted. but a reboot should reset that, correct? since i did NOT add them to the boot script.

---

### Post by drogoh on 2005-10-07
Things to consider:

1.  does df -H display the correct size?
2.  could this "missing" space simply be reserved space?

---

### Post by SilentCacophony on 2005-10-07
Yes, I suspected you might have mounted those accidentally, and I would have thought a reboot would have rectified it if so.

You don't remember editing any file to do the mounting?

I don't know what is mounting those two entries. I suppose there could be some valid reason for them, possibly due to it being a laptop, but they look wrong to me.

What do you get from this:

**cat /etc/mtab**

Also, as drogoh mentioned, df -H will show 'human readable' output

---

### Post by Douglas Drake on 2005-10-07
okay, **df -H** displays:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda1               29G   9.2G    19G  34% /
tmpfs                  132M      0   132M   0% /dev/shm
/dev                    29G   9.2G    19G  34% /.dev
none                   5.3M   2.9M   2.4M  56% /dev

which now makes some sense, however, why does the file browser in application --> system tools (i use gnome) say differently. when i right click on FILESYSTEM and click "properties." the "contents" says: 

97171 items, totally 8.1 GB (some contents unreadable)

and the "free space" says 16.9. why is there such a stark difference between the file browser and the **df **command in the terminal?

---

### Post by Douglas Drake on 2005-10-07
no, i didn't edit any files. just playing around with **mount **commands.


~$ cat /etc/mtab

/dev/hda1 / ext3 rw,noatime,errors=remount-ro,commit=600 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0

---

### Post by drogoh on 2005-10-07
Straight from 'man df':

```
     -H      "Human-readable" output.  Use unit suffixes: Byte, Kilobyte,
             Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the
             number of digits to four or fewer using base 10 for sizes.

     -h      "Human-readable" output.  Use unit suffixes: Byte, Kilobyte,
             Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the
             number of digits to four or fewer using base 2 for sizes.

```

It's all about who is counting using which base number.  Hard drive manufacturers use base 10, therefore -H will give you a more accurate count by way of how the manufacturer is counting your space.

By the way, the total space still being off by 1G is most likely reserved root-only space.  You can turn that down or off completely but it's good for I/O performance.

---

### Post by SilentCacophony on 2005-10-08
Well, the difference between 1000 and 1024 isn't great enough to cause the difference he gets, though.  The "(some contents unreadable)" part may explain that better, I think. EDIT - Maybe it is, after all. 

I still don't see any point to these two mount points, and wonder what problems they may cause:

/dev 29G 9.2G 19G 34% /.dev
none 5.3M 2.9M 2.4M 56% /dev

A bit over my head, maybe. If it were me, I'd try unmounting them, but I don't know if that's advisable.

---

### Post by Douglas Drake on 2005-10-08
i think i understand, thanks a bunch!

---

### Post by drogoh on 2005-10-08
[QUOTE=SilentCacophony]Well, the difference between 1000 and 1024 isn't great enough to cause the difference he gets, though.  The "(some contents unreadable)" part may explain that better, I think.

I still don't see any point to these two mount points, and wonder what problems they may cause:

/dev 29G 9.2G 19G 34% /.dev
none 5.3M 2.9M 2.4M 56% /dev

A bit over my head, maybe. If it were me, I'd try unmounting them, but I don't know if that's advisable.[/QUOTE]

The second one is the pseudo file system that provides your /dev.  You definitely DON'T want to umount that.  The first one I don't quite know about because I've never seen it but I wouldn't go umounting it without knowing for sure it's useless, as it could prove bad by your system deadlocking, which wouldn't be very good at all.

---

### Post by SilentCacophony on 2005-10-08
> The second one is the pseudo file system that provides your /dev. You definitely DON'T want to umount that. The first one I don't quite know about because I've never seen it but I wouldn't go umounting it without knowing for sure it's useless, as it could prove bad by your system deadlocking, which wouldn't be very good at all.

Good advice. :)

Perhaps someone else may shed some light on that /.dev one. I've never seen the like.

Anyway, if nothing bad is currently happening...

---

