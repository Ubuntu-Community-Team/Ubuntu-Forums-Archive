---
title: "no other harddisks in /dev"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by Buu on 2005-03-08
Hello,
I have only acces to the partition that i've installed ubuntu on. I have two other HD but I don't see them in /dev. With the live-cd I had no problems mounting them.
Grtz

---

### Post by Buu on 2005-03-08
Oops, I'm wrong in the /dev are all the other HD. The problem I can't mount them.
Gave me an error that it could not be found in /etc/fstab or /mtab

---

### Post by bored2k on 2005-03-08
[QUOTE=Buu]Oops, I'm wrong in the /dev are all the other HD. The problem I can't mount them.
Gave me an error that it could not be found in /etc/fstab or /mtab[/QUOTE]
 > $ sudo fdisk -l

Can you see the partition you want to mount there? If you do, mount  /dev/hdaX /made/up/dir
and give it you're desired permissions [if desired] . If the partition you're trying to mount is NTFS you won't have write support .

---

### Post by Buu on 2005-03-09
I did the sudo fdisk -l, and I see my other HD. When I try doing what's been said I get the same error back (could not be found in /etc/fstab or /mtab)

---

