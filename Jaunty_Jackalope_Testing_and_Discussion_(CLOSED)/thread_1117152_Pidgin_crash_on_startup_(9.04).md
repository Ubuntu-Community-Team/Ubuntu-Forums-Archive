---
title: "Pidgin crash on startup (9.04)"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Arizon_Dread on 2009-04-05
Hi!

I decided to make a fresh install with the Ubuntu 9.04, but I forgot to bind my home partition to /home during installation, so first I added a line to bind that new partition as home to my /etc/fstab

```
/dev/sda9   /home   ext3   defaults   0   1
```

before reboot, I copied the hidden files from my current home to the new (or old) home directory

```

cp -r .* /media/disk-3

```

After reboot, Pidgin started crashing on contact list load, I ended up formatting my / and installing 9.04 anew, but to no avail

I've also tried to completely remove pidgin plus the .purple in /home and reinstall, but nothing changes.

this is what I get when it crashes:
```

arizon@arizon:~$ pidgin
*** glibc detected *** pidgin: double free or corruption (out): 0x0a1a9910 ***


```

or 

```
arizon@arizon:~$ pidgin
Segmentation fault (core dumped)

```

Any suggestions?

EDIT:
more info:
```

(00:19:27) msn: S: NS 000: ILN 0 NLN x@hotmail.com 1 Xxx 2254295084 %3Cmsnobj%20Creator%3D%22x%40hotmail.com%22%20Type%3D%223%22%20SHA1D%3D%22NoB%2FDiJN51LOTmzpAucnRjGs6jA%3D%22%20Size%3D%222556%22%20Location%3D%220%22%20Friendly%3D%22QwBJAE0ARwAzADIANgA1AGMAAAA%3D%22%2F%3E
(00:19:27) msn: Queueing buddy icon request for x@hotmail.com (buddy_icon_window = 0)
(00:19:27) blist: Updating buddy status for x@hotmail.com (MSN)

(00:19:27) nautilus: couldn't save '/home/arizon/.gnome2/nautilus-sendto/pidgin_buddies_online': Failed to create file '/home/arizon/.gnome2/nautilus-sendto/pidgin_buddies_online.LX7NRU': Permission denied
*** glibc detected *** pidgin: double free or corruption (out): 0x0a840640 ***

```

---

### Post by Arizon_Dread on 2009-04-05
I think my issue comes from the fact that I copied hidden files to my home dir and they're now conflicting each other, but I have no idea how to fix it. Clearly, removing .purple has no effect...

---

### Post by Arizon_Dread on 2009-04-05
[FIXED]
When I copied the hidden files, the directory ~/.gnome2/nautilus-sendto/ had the owner root:root

so, this fixed the problem:

```

cd ~/.gnome2/
chown arizon.arizon nautilus-sendto/

```

---

### Post by Haitao on 2009-04-10
Hi!

I add the same problem and the reason for me getting "Segmentation fault (core dumped)" was the display picture. I actually removed .purple/ and recreated my 4 accounts, no problem. Then when adding the display picture... segfault!

Retried with a smaller picture, same result. Hope that helps someone and that the bug eventually gets fixed.

Fred

---

