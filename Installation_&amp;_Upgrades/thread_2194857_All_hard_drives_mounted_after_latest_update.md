---
title: "All hard drives mounted after latest update"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by riceroma on 2013-12-21
Hello. All

I am running ubuntu 13.10, had no problems until I ran.
A software update :-( Now all my hard drives are auto
mounted at startup. I've tried to unmount the drives. All I get is errors.
I've tried doing reboots, and restarts a number of times.
I also did three reinstalls, and no joy at all.

Thanks

---

### Post by ian-weisser on 2013-12-21
Show us the exact error message,
and show us exactly what you did to get the error.

---

### Post by Mark Phelps on 2013-12-21
> Now all my hard drives are auto mounted at startup.

HOW did you determine that they were actually mounted?  IF you use the disks icon, whenever you click one, it THEN mounts that partition.

Besides, having them auto-mounted doesn't pose any real problems.

So, what is the concern?

---

### Post by riceroma on 2013-12-21
Hello. Ian-weisser and Mark Phelps

Well, this is how it all got started ;-) By going to search, Software Updater and excepting all downloads I believe the total download was about 61, MB in size I can't recall exactiy. After doing a reboot as was instructed to. Now I am new to all this, but my belief is, it had something to do with updating the kernel file(s)? Any and all help will be much appreciated.

Error unmounting Filesytem

Error unmounting /dev/sda6: Command-line 'umount "/dev/sda6"'exited with non-zero exit status 1: umount:/:device is busy.
(In some cases useful info about processes that use the device is found
by lsof(8) or fuser(1))
(udisks-error-quark, 14)

I found this informations by searching through disk utility. In volumes on every partition there's an arrow, and star? Right below the volumes there's a set of sprocket wheels, if I click it a menu gives me more actions, doing so, I can click on it to Edit More options. Under Automatic Mount, the button is set to the on position. There is a box with a check mark, yes it's checked for Mount at startup.

@Mark Phelps

"Besides, having them auto-mounted doesn't pose any real problems."

My concerns are, that my hard drive may have to over work in the background? I am not sure if this is the case. My other concern is security.

Much thanks to both  of you.

---

