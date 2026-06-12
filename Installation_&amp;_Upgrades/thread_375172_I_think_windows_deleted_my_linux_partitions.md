---
title: "I think windows deleted my linux partitions :/"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by kragen on 2007-03-03
after installing windows vista I now have a large space where two of my 4 linux partitions were - they were raid 0 partitions and their counterparts are still on the other disk, so I know their exact size, is it possible to restore them somehow, by allocating partitions of their exact size on the MBR and not formatting them?

---

### Post by wavesound on 2007-03-03
Hi
Can you try using one of the live cd's like Ubuntu and looking at your drive info.
You may be able to repair the MBR, but I have no experience of using Raid.
:KS 
Cheers
Bob

---

### Post by kragen on 2007-03-03
yeah, i've already used the live cd, I don't really know why its done this, but its literally just deleted two of my partitions, but not created new ones in their place. My question was, if I know exactlay where the start / end of those partitions was, can I simply re-create them somehow (I'm thinking yes, because the data will still be there), and how do I do that - will fdisk work or will it unwittingly overwrite some of the data, i.e. do I need something more sophisticated.

---

### Post by kragen on 2007-03-03
ok, found a guide and it agreed with what I thought - I can create and destroy partitions all I want, and as long as i dont physically overwrite the data, I should be able to recover the partition as long as I get the start and end blocks right.

I've managed to recover one of the partitions 100% fine (the one with all my data on it :D), the other one I'm having problems with - for some reason the extended partition it was created in seems to have moved...

anyway, just posting to let people know that I've figured it out, I'm amazed it was that easy in fact :P

---

### Post by wavesound on 2007-03-04
Nice one!
I can now get windoze to boot using super grub disk
but I have to have the CD in.
I'm still trying to load to the MBR without using windoze

cheers
Bob

---

