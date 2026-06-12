---
title: "No permission"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-06-26
After today's update, it seems that I no longer have permission to use "Users and groups", and also I can't mount any partition, mounting will cause an error saying "Cannot get volume.fstype.alternative". Is it just me having this problem?
If anyone know, is there any way of solving it?
Thanks.

Edit: 
-The problem's cause is narrowed down to libgdu0 and devicekit-disks, downgrade those 2 packages will work arround the "unable to mount" problem. Detailed howto is [HERE]("http://ubuntuforums.org/showpost.php?p=7525719&postcount=13").
-As for permission problem, just fireup users and groups again, and it will work.

---

### Post by philcamlin on 2009-06-26
sudo ?:D

---

### Post by Vanishing on 2009-06-26
> **philcamlin said:**
> sudo ?:D

Its not that..Usually "users and groups" will run, and prompt for my password, now it just says something like I don't have permission.

---

### Post by Vanishing on 2009-06-26
> Commit Log for Fri Jun 26 14:20:33 2009


Upgraded the following packages:
devicekit-disks (004-1) to 005-0ubuntu1
devicekit-power (008-1) to 008-1ubuntu1
libdevkit-power-gobject1 (008-1) to 008-1ubuntu1
playonlinux (3.5-1) to 3.5-1ubuntu1

Installed the following packages:
libeggdbus-1-0 (0.5-1)
libgudev-1.0-0 (20090615+1-4)
libpolkit-backend-1-0 (0.92-0ubuntu1)
libpolkit-gobject-1-0 (0.92-0ubuntu1)


Just checked update history, no doubt 1 or some of them caused the problems...

---

### Post by K.Y.A on 2009-06-26
I never thought updates could remove your roof (@ signature).

But, I think that running```
 sudo apt-get install ubuntu-desktop
``` should fix your problems. Also, try running```
 sudo apt-get upgrade --dist
```

---

### Post by Vanishing on 2009-06-26
> **K.Y.A said:**
> I never thought updates could remove your roof (@ signature).

But, I think that running```
 sudo apt-get install ubuntu-desktop
``` should fix your problems. Also, try running```
 sudo apt-get upgrade --dist
```

Just as I expected..downgrading these 3 packages fixed the problem:
> devicekit-disks (004-1) to 005-0ubuntu1
devicekit-power (008-1) to 008-1ubuntu1
libdevkit-power-gobject1 (008-1) to 008-1ubuntu1

---

### Post by K.Y.A on 2009-06-26
So my commands fixed it? yay.:KS

---

### Post by Vanishing on 2009-06-26
> **K.Y.A said:**
> So my commands fixed it? yay.:KS

lol....
Now my usb external harddrive can mount on system startup, but the other partitions still can't mount.
Still working to fix the problem..

---

### Post by Vanishing on 2009-06-26
Yup, external hard drive auto mounts on startup, but manually mounting other partitions will cause a "DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)" error.
So it is something related to dbus?

---

### Post by Vanishing on 2009-06-27
> **Vanishing said:**
> Yup, external hard drive auto mounts on startup, but manually mounting other partitions will cause a "DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)" error.
So it is something related to dbus?

Finally, found the problem.
Now my system is back to "no problem discoved state".
Apparently there was an update of "libgdu0 (0.3-0ubuntu2) to 0.4-0ubuntu1" when I started my machine tonight. Simply downgrade that lib fixed everything.
My suggestion is not to upgrade that lib file just yet.:popcorn:

---

### Post by K.Y.A on 2009-06-27
> **Vanishing said:**
> Finally, found the problem.
Now my system is back to "no problem discoved state".
Apparently there was an update of "libgdu0 (0.3-0ubuntu2) to 0.4-0ubuntu1" when I started my machine tonight. Simply downgrade that lib fixed everything.
My suggestion is not to upgrade that lib file just yet.:popcorn:
I don't upgrade at all anymore. Just distro releases. :)

Linux is secure as it is.

---

### Post by zika on 2009-06-27
> **Vanishing said:**
> Its not that..Usually "users and groups" will run, and prompt for my password, now it just says something like I don't have permission.
Same here. It works after second attempt. Mounting Vista partition on the same disk doesn't work ... :)
How did You downgrade version of libgdu0?

---

### Post by Vanishing on 2009-06-27
> **zika said:**
> Same here. It works after second attempt. Mounting Vista partition on the same disk doesn't work ... :)
How did You downgrade version of libgdu0?

I figured its not just libgdu0 you have to downgrade.
This is my work arround:

First, try to downgrade libgdu0 AND devicekit-disks.
download links are:
> [http://launchpadlibrarian.net/26498215/libgdu0_0.3-0ubuntu2_i386.deb](http://launchpadlibrarian.net/26498215/libgdu0_0.3-0ubuntu2_i386.deb)
[http://launchpadlibrarian.net/26381454/devicekit-disks_004%7Egit20090415-0ubuntu2_i386.deb](http://launchpadlibrarian.net/26381454/devicekit-disks_004%7Egit20090415-0ubuntu2_i386.deb)

put those 2 debs on the Desktop.
Fire up terminal, cd to Desktop, and :
> sudo dpkg -i libgdu0_0.3-0ubuntu2_i386.deb devicekit-disks_004%7Egit20090415-0ubuntu2_i386.deb
then enter your password, after installation is done, reboot.

Second, tell me if it works.:popcorn:

FYI: This is only a temporary solution, you can always get the newer packages if new update solves this problem.

---

### Post by zika on 2009-06-27
> **Vanishing said:**
> I figured its not just libgdu0 you have to downgrade.
This is my work arround:

First, try to downgrade libgdu0 AND devicekit-disks.
download links are:

put those 2 debs on the Desktop.
Fire up terminal, cd to Desktop, and :

then enter your password, after installation is done, reboot.

Second, tell me if it works.:popcorn:

FYI: This is only a temporary solution, you can always get the newer packages if new update solves this problem.I do not need files from Vista right now so I will wait for upgrade to fix it. I just wanted to learn where I can find previous versions of packages. Thank You.

---

### Post by Vanishing on 2009-06-27
> **zika said:**
> I do not need files from Vista right now so I will wait for upgrade to fix it. I just wanted to learn where I can find previous versions of packages. Thank You.

No problem.:P

---

### Post by inportb on 2009-06-27
> **K.Y.A said:**
> Linux is secure as it is.

... partly because of the updates?

---

### Post by kiliya on 2009-06-28
This fix worked for me, or at least I can view my SanDisk Drive again. Thanks for the help, this one took awhile. Have you submitted a bug report?

---

### Post by Vanishing on 2009-06-28
> **kiliya said:**
> This fix worked for me, or at least I can view my SanDisk Drive again. Thanks for the help, this one took awhile. Have you submitted a bug report?

I think similar bug report have been filed.:popcorn:

---

### Post by zika on 2009-06-29
After today's update when I try to mount NTFS partition I get:```
Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PolicyKit1 was not provided by any .service files
```Is that a step towards improvement or ... :) ?

---

### Post by Vanishing on 2009-06-29
> **zika said:**
> After today's update when I try to mount NTFS partition I get:```
Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PolicyKit1 was not provided by any .service files
```Is that a step towards improvement or ... :) ?

No, but I think I got this error message before, like last update that broke the disk mounting..:guitar:

---

### Post by zika on 2009-06-29
> **Vanishing said:**
> No, but I think I got this error message before, like last update that broke the disk mounting..:guitar:Now it is:```
Cannot get volume.fstype.alternative
``` ... :) It looks like we are getting there ...

---

### Post by Vanishing on 2009-06-29
> **zika said:**
> Now it is:```
Cannot get volume.fstype.alternative
``` ... :) It looks like we are getting there ...

Yes. Just upgraded, and now I get that error too.

---

### Post by Vanishing on 2009-06-29
> **Vanishing said:**
> Yes. Just upgraded, and now I get that error too.

Downgraded hdparm package. Now it works.
Is it gonna be fixed?T.T

---

### Post by muglikar on 2009-06-29
> **zika said:**
> After today's update when I try to mount NTFS partition I get:```
Not Authorized: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.CheckAuthorization() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PolicyKit1 was not provided by any .service files
```Is that a step towards improvement or ... :) ?

Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

