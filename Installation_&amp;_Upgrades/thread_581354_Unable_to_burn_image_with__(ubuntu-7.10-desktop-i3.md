---
title: "Unable to burn image with  (ubuntu-7.10-desktop-i386.iso)"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by irkush on 2007-10-19
Hello,

I have downloaded ubuntu-7.10-desktop-i386.iso,

When i try to burn the image with InfraRecorder i get an error as - 

"
[B][Timestamp]-Started to write disc in real write mode
[Timestamp]-Input/output error. write_g1: scsi sendcmd: no error
[Timestamp]-Input/output error. read buffer cap: scsi sendcmd: no error
[Timestamp]-Started to write track 1
[Timestamp]-Input/output error. write_g1: scsi sendcmd: no errorCDB: 2A 00 00 00 00 00 00 00 1F 00status: 0
[/B]"

The CD gets ejected and nothing is written.

I have checked the md5Sum and found it to be matching. Also when i do a simultaed burning it seems to be working fine with a 80min(700mb) CD. Its when i actually try to burn it that i get this error.
Iam currently running Winxp SP2.

Regards,

---

### Post by wpshooter on 2007-10-19
Have you tried rebooting your computer ?

---

### Post by irkush on 2007-10-19
Yes , I've  done that. Doesn't seem to work.

Regards,

---

### Post by Topsiho on 2007-10-19
Did you try and burn the .iso as an image?

I do not know how this is called in your CD burning program, it should have an option for burning .iso's (disc image files)

You could burn it using the Live CD of course, but then you should have the Live CD ...
Hmmm...

Topsiho

---

### Post by irkush on 2007-10-19
Yes iam trying to burn it as an image.

Regards,

---

### Post by Lord Landis on 2007-10-19
Do you have access to any other burning apps?  Nero (even the free/OEM version) works great for burning isos, and even Roxio does a good job.

---

### Post by wpshooter on 2007-10-19
> **irkush said:**
> Yes iam trying to burn it as an image.

Regards,

Can you successfully burn **OTHER** ISO images ?

---

### Post by irkush on 2007-10-19
No i have not tried burning an other image. But when the simulated burning works fine, i guess it should be able to do the actual burning process as well.

Regards,

---

### Post by Seboj on 2008-02-27
Hey there Irkush,

I had this -exact- same problem not too long ago, trying to burn GG to a dvd from Vista. All I had to do was format the dvd, and it fixed the problem.

Hope this helps!

---

