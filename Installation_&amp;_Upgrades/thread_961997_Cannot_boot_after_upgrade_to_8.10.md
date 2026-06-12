---
title: "Cannot boot after upgrade to 8.10"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by feedmecereal on 2008-10-28
I just upgraded from 8.04 to 8.10 and I cannot boot. I get to the boot splash screen then it stops part of the way through and shows an error message. It pauses for a few minutes before displaying another error message:

> Server Authorization directory (daemon/SErvAuthDir) is set to /var/lib/gdm but is not owned by user 108 and group 118. Please correct the ownership or GDM configuration and restart GDM.

Please help!! What do I do?

---

### Post by ad_267 on 2008-10-28
I'm only guessing here, but you could try changing the group and owner of /var/lib/gdm. I'm not sure about that though, it might be that the ownership is correct but GDM is configured incorrectly.

Can you enter commands into the terminal? You might have to switch to another tty using Ctl-Alt-F1, you can switch back again with Ctrl-Alt-F7. Otherwise you can get a recovery login form the boot menu.

Can you check that the file /etc/gdm/gdm.conf has these lines:
```
User=gdm
Group=gdm
```
You can use "less /etc/gdm/gdm.conf" to view the file.

Then you can change the permissions with:
```
sudo chown gdm /var/lib/gdm
sudo chgrp gdm /var/lib/gdm
```

---

### Post by feedmecereal on 2008-10-28
I tried that and it didn't work.

After I restarted I wrote down some error messages that might help you figure this out:

> Starting Kernel log daemon
It had some other stuff right after that but I didn't have time to write it down. But it did give this at the end:
> start-stop-daemon: Unable to open pid file '/var/run/klogd/kmsgpipe.pid' for writing: Read-only file system

---

### Post by ad_267 on 2008-10-28
How much work would it be to use the live cd to back up all of your data and then do a clean install? That's probably the easiest thing to do.

---

### Post by feedmecereal on 2008-10-28
That might be a whole lot more work than I would like to do because I have a lot of data on /home. I guess I should have repartitioned like I have read about.

Do you know what the problem might be?

---

### Post by ad_267 on 2008-10-28
I'm not really sure but someone else might be able to help. It seems like the file permissions have been messed up somehow. The "read-only file system" message seems to indicate that root does not have permission to write to a file it needs to.

---

### Post by wilshire on 2008-10-29
i am having the same problem.

i've been using ubuntu since breezy, and *someday* i'd like to be able to upgrade it without it breaking.

my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=69d1535c-ded5-4b51-b73c-645887624b98 /               ext3    relatime 0       1
# /dev/sda3
UUID=c95064c7-c2e8-486a-b2c3-51f99740ae30 /home           ext3    relatime        0       2
# /dev/sda2
UUID=4ca9cea0-76e2-4da8-a72f-433efe0d55de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

---

### Post by wakebdr on 2008-11-01
Same problem here too.  I tried to upgrade from 8.04.

It looks like the whole filesystem is being mounted read-only, thus the errors we are seeing.

---

### Post by feedmecereal on 2008-11-01
Oh well, I just ended up reinstalling Ubuntu on another partition and then moving my old /home to my new installation.

---

### Post by acearle on 2008-11-03
I have the same problem, but found that if I boot using 2.6.24-21-generic instead of 2.6.17-7-generic it works.

Anyone have any ideas? I'm going to poke around a bit and see what I can find, but....ermmm....I'm a danger to myself and others editing conf files, lol!

---

### Post by acearle on 2008-11-03
Another error that might be related is the following endless loop on boot:

sd 2:0:0:0: [sdd] add. Sense: No Additional Sense Information
sd 2:0:0:0: [sdd] add. Sense Key: No Sense [current]

---

### Post by Ruiner75 on 2008-11-03
Same "*Unable to open pid file '/var/run/klogd/kmsgpipe.pid' for writing: Read-only file system*" problem here. Strange thing is if i boot in recovery mode and then click on "resume boot" it work all just fine. Only problem: gedit doesn't work anymore...

---

### Post by macvr on 2008-11-03
i also have the same problem...
this seems to be rare and fond only 3 such instances while googling yday, one in the french forum, and the others in chinese and german ubuntu forums
[I] but may be it has increased by now
[/I] but no one knew the fix


 i have filed a bug report... in launchpad>>>

[https://bugs.launchpad.net/ubuntu/+bug/293220]("https://bugs.launchpad.net/ubuntu/+bug/293220")

pls add ur info too to speeden the bug resolution

---

### Post by macvr on 2008-11-03
i'm able to use ubuntu  now, i had, still have similar problem but, everything now works for me in the recovey mode> check my post the process i have done are here, might help someone
[http://ubuntuforums.org/showthread.php?t=966356]("http://ubuntuforums.org/showthread.php?t=966356")

---

### Post by falken78 on 2008-11-06
major issues here aswell...  not to happy right now.. last to upgrades has been a mess.

* Hangs at boot. Does not matter what kernal img I pick.
* I have tried to remove "relatime" option from fstab - saw a note about this in another forum...
* the system is monted in RW when i pick recovery mode. Only having problem with system disk (mount point /) not my other disk /home (and so on)
* Saw some notes about /etc/nsswitch.conf (something like this the filename was) and that ldap should be removed. I did not have anythinig saying ldap in this file..

pleaese help me...

---

