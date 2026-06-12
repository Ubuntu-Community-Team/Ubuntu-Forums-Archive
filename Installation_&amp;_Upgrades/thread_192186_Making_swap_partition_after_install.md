---
title: "Making swap partition after install"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by wezzer on 2006-06-08
Hi there,

I wanted to try new Dapper and install went fine until I had to make partitions. I didn't remember that there is a limit of 4 partitions / harddrive and I already had 3 partitions for windows full of important files. So I made one partition for ubuntu and continued install without any partition for swap. Installation process did warn me about that but I did continue install. 

Now I have rearranged my files so that I have one 1 GB partition empty for swap. Here is what cfdisk tells me (is the partition right type?)  
[IMG]http://toivanen.org/web/ubuntu.png[/IMG]

And I did modify /etc/fstab to look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda5       none           swap    defaults        0       0
/dev/hda4       /storage        vfat    user,rw,exec    0       0

```


I did ask for help at the irc-channel, but no one really told me what is the solution. I got links for software name parted and someone told me to use swapon, but problem still exists. When I type "mount" in the console, there is no swap.

Help needed!

---

### Post by jsc1328 on 2006-06-08
Hi,

Try:

mkswap /dev/hda5
swapon

IMPORTANT: this will delete all data on /dev/hda5!!!  But you probably already knew that.

Also mkfs -t swap /dev/hda5 might work.  Maybe just a wrapper on the mkswap, but not sure since i'm on windows right now.

\j

---

### Post by wezzer on 2006-06-08
```

antti@spitfire:~$ sudo swapon
usage: swapon [-hV]
       swapon -a [-e] [-v]
       swapon [-v] [-p priority] special|LABEL=volume_name ...
       swapon [-s]

```

Should I put some prefix?

And do I need still need that line on /etc/fstab after these commands?

---

### Post by jsc1328 on 2006-06-08
Also you fstab line needs to be:
/dev/hda5       none           swap    defaults        0       0

(you had the wrong device and there should not be a mount point).

type mount to make sure /swap is not already mounted, if so you'll need to umount /swap before mkswap.

\h

---

### Post by wezzer on 2006-06-08
Okay, the fstab is now fixed with correct information. mkswap and swapon went fine but do I need more commands to show swap on mount list?

---

### Post by jsc1328 on 2006-06-08
I'm afraid you got me there.  Since I'm at work using windows I can't tell if it shows up when I type mount on a linux box.  

What does 'swapon -s' return?

---

### Post by jsc1328 on 2006-06-08
also 'top' should show how much memory is being used (both in ram and in swap space).

---

### Post by wezzer on 2006-06-09
[QUOTE=jsc1328]I'm afraid you got me there.  Since I'm at work using windows I can't tell if it shows up when I type mount on a linux box.  

What does 'swapon -s' return?[/QUOTE]

```

antti@spitfire:~$ swapon -s
Filename      Type            Size    Used    Priority
/dev/hda5   partition       995988  0       -1
antti@spitfire:~$

```
Does this mean that it is working? :-)

Antti

---

### Post by jsc1328 on 2006-06-12
Hi,

Looks good.  I checked over the weekend, mount does not show swap space.

The 'free' command also will show the amount of swap available:

free -m

\j

---

### Post by wezzer on 2006-06-13
Yey, it is working! :-)
Thanks!
```

antti@spitfire:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1011        512        499          0         53        265
-/+ buffers/cache:        193        818
Swap:          972          0        972
antti@spitfire:~$

```

---

