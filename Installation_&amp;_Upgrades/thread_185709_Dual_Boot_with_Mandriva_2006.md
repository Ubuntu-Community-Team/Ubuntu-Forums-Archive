---
title: "Dual Boot with Mandriva 2006"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by spiffx on 2006-06-01
Hi,

i'm an Ubuntu newbie (but a long-time mandrake/mandriva user). i'm going to try installing Ubuntu 6.06 tonight, to dual boot with Mandriva 2006 (which is currently using lilo).

has anyone got any recommendations for preparing for the dual boot? will ubuntu 6.06 allow me to use lilo, or do i need to use grub? i'd prefer to use lilo, as that's the default on mandriva and so for the moment it would be simpler for me to get working i think. i don't have windows at all, and mandriva 2006 and ubuntu 6.06 will be on separate drives.

thanks very much for your help!


spiffx

---

### Post by nkbj on 2006-06-01
I have Ubuntu on /dev/hda and Mandriva on /dev/hdb. The Ubuntu grub-installer autodetected Mandriva, so I just let it install grub on the MBR (Master Boot Record) in /dev/hda. I can now choose to boot Mandriva from the grub menu.

Regards,
Niels Kristian

---

### Post by spiffx on 2006-06-01
[QUOTE=nkbj]I have Ubuntu on /dev/hda and Mandriva on /dev/hdb. The Ubuntu grub-installer autodetected Mandriva, so I just let it install grub on the MBR (Master Boot Record) in /dev/hda. I can now choose to boot Mandriva from the grub menu.

[/QUOTE]


ok cool. i was worried the grub installer would not find mandriva and i'd have to hand edit it to work with mandriva. 

i'm looking forward to running ubuntu! mandriva / amndrake has been very good for me for the last five years, but it seems to be getting out of date, a bit buggy and does not really seem like it is improving. so i thought it was a good time to try (k)ubuntu!


spiffx

---

