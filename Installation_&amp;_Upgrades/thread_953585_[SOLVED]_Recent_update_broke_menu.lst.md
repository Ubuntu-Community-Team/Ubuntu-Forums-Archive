---
title: "[SOLVED] Recent update broke menu.lst"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by neondiet on 2008-10-20
Hi.

Last thursday (16th Oct) I downloaded a bunch of software updates and then shutdown the system for the weekend.  It needed a reboot anyway to pick up the changes.  

This morning I attempted to boot and discovered it wouldn't.  After a timeout it dropped me back to the initramfs prompt, after giving the error:

[INDENT]ALERT! /dev/disk/by-uuid/88d23c2e-811b-46d2-bb43-1503a55417db does not exist. Dropping to a shell[/INDENT]

It seems that during the software update, the definition for the root disk in menu.lst got changed from /dev/md2 to point to the above UUID.  I can confirm this by looking at the contents of the menu.list~ backup file, date stamped: 2008-10-16.  What really threw a spanner in the works was that this strange UUID isn't the correct UUID for md2, which is:

```
root@dsv01:~# vol_id --uuid /dev/md2
bf04ff56-4c8c-4e60-be82-21d8d471a34b
```

I'm puzzled as to how this happened, and where it got that UUID from. I can see that this UUID used to exist, as it's present in menu.list.sav dated from back when I first installed this system.  i.e.

```
root@dsv01:~# ls -l /boot/grub/menu.lst.sav 
-rw-r--r-- 1 root root 4272 2008-08-26 17:53 /boot/grub/menu.lst.sav
root@dsv01:~# grep UUID /boot/grub/menu.lst.sav
# kopt=root=UUID=88d23c2e-811b-46d2-bb43-1503a55417db ro
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=88d23c2e-811b-46d2-bb43-1503a55417db ro quiet splash
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=88d23c2e-811b-46d2-bb43-1503a55417db ro single
```

But it's not present on any of the disks in the system today:

```
root@dsv01:~# findfs UUID=88d23c2e-811b-46d2-bb43-1503a55417db
findfs: Unable to resolve 'UUID=88d23c2e-811b-46d2-bb43-1503a55417db'
```

So where did the update get this UUID from?  And why is it choosing to input something different from the already defined (and working) root disk entry in menu.lst?

Actually that last question may have something to do with the menu list that I had to choose from with respect to updating menu.lst after the update completed.  I wasn't familiar with all the choices so picked the first one, as that seemed like a sensible suggestion.  I can't even remember what the choices were now.  There was no extra help available to educate me about those choices.

Looking in Synaptic's history log, here's a list of the changes applied on thursday:

Commit Log for Thu Oct 16 09:15:20 2008

Upgraded the following packages:
cupsys (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
cupsys-bsd (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
cupsys-client (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
cupsys-common (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
dbus (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3.1
dbus-x11 (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3.1
jockey-common (0.3.3-0ubuntu8) to 0.3.3-0ubuntu8.1
jockey-gtk (0.3.3-0ubuntu8) to 0.3.3-0ubuntu8.1
libcupsimage2 (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
libcupsys2 (1.3.7-1ubuntu3) to 1.3.7-1ubuntu3.1
libdbus-1-3 (1.1.20-1ubuntu2) to 1.1.20-1ubuntu3.1
linux-generic (2.6.24.19.21) to 2.6.24.21.23
linux-headers-generic (2.6.24.19.21) to 2.6.24.21.23
linux-image-generic (2.6.24.19.21) to 2.6.24.21.23
linux-libc-dev (2.6.24-19.41) to 2.6.24-21.42
linux-restricted-modules-common (2.6.24.13-19.45) to 2.6.24.14-21.51
linux-restricted-modules-generic (2.6.24.19.21) to 2.6.24.21.23

Installed the following packages:
linux-headers-2.6.24-21 (2.6.24-21.42)
linux-headers-2.6.24-21-generic (2.6.24-21.42)
linux-image-2.6.24-21-generic (2.6.24-21.42)
linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.51)
linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.32)


If anyone else has been bitten my this, or can throw some light on a possible cause, I'd appreciate it.  I'd like to know how to avoid this happening in future.

Regards.

---

### Post by louieb on 2008-10-21
>  where it got that UUID from.most likely it got the uuid from the kopt option in the automagic section.
heres an example
```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=17b872d8-a967-45fa-b748-441cd8e1294e ro


```

---

### Post by neondiet on 2008-10-21
Oh yes.  That seems to be a default UUID then as that's the number for kopt I have defined in my menu.lst too.  

Doesn't seem right to me though that there is a default UUID common to all Ubuntu installs.  Wouldn't that mean that all Ubuntu systems by default have the same UUID for their boot disk, and isn't the point of a UUID supposed to be that it's unique?

Come to think of it, why would it be using a number on a line that's commented out.  That's exactly the opposite behaviour of what I would expect.

---

### Post by louieb on 2008-10-21
Its a Debian thing. the module **update-grub** uses the commented out lines in the automagic section. GRUB itself just sees them as comments.  The UUID is set to whatever it was when you install Ubuntu.  Things like formating and resizing can change a partitions UUID. 
Just be sure to update the UUID in the **kopt **option so that future kernel update will pickup the right UUID.

---

### Post by neondiet on 2008-10-21
Thanks for taking the time to explain that.  Now I know how to avoid it in future.  Much appreciated.

---

### Post by louieb on 2008-10-21
Your welcome. Please use the thread tools to mark this one as solved.

---

