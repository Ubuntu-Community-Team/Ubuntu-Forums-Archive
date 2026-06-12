---
title: "Cannot mount cd (anymore)"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-07-30
I put in a CD into my drive and I get the message popped up (same as if I try as root:)

sudo mount /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


What does it mean? It is just a data cd.
BTW, /etc/fstab shows:
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0


I had this CD already open and I can still read this CD on a Windows machine. What could happened here?

bye

R.

---

### Post by logos34 on 2008-07-30
I have a DVD+RW that does that---refuses to automount for some reason.  Nothing to do with windows in my case because all burns to it were done in k3b with 'linux-only' + Rock ridge (no Joliet).  I have to manually mount it:

sudo mount -t iso9660 /dev/scd0 /media/cdrom0

---

### Post by ELMIT on 2008-07-30
I was so sure that I mentioned that I cannot even mount it as root - as you mentioned it.

bye

R.

---

