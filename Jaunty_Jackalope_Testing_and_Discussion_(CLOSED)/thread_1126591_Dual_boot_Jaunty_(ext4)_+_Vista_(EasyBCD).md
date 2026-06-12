---
title: "Dual boot Jaunty (ext4) + Vista (EasyBCD)"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nirgalksi on 2009-04-15
Hi all !

I'm actually on a dual boot Intrepid/Vista, with the help of EasyBCD because this damn Vista refuse to work with Grub (no relation with my real question but is this the case for all vistas are only for some constructors?)

I would like to know before to go on Jaunty this week end if someone succeed in doing a dual boot Jaunty/Vista:
with EasyBCD and / in ext4
Because I read somewhere that EasyBCD may not support ext4...

(and I can't even leave Vista for XP as I can't install it on my laptop : sony FW)

Thanks to everyone :D

---

### Post by syko21 on 2009-04-15
I use grub with windows vista and it seems to work fine...

---

### Post by dasme on 2009-04-16
> **syko21 said:**
> I use grub with windows vista and it seems to work fine...

Same here using grub with Windows 7 Beta :)

Just install Ubuntu aftr installing Vista. The grub bootloader will detect ur vista os. ;)

---

### Post by jmmL on 2009-04-16
I'm running a EasyBCD and grub combination - the same one that you want to set up.

I'm also using ext4 and it works absolutely fine. I would have liked to use just grub, but my laptop is "tattoo"ed, meaning that if I over-write the MBR, I will have to go through a complicated process to get vista to dual boot again, as the bios will only hand over to a MBR with particular labels and properties. (Or at least, that's my understanding)

So yep, it should work fine.

Saying that, I installed EasyBCD during intrepid testing, and so I was running ext3 at the time. I then upgraded to ext4 and jaunty in January. So I don't have experience of installing them both fresh, but I assume it will be fine.

---

### Post by Nirgalksi on 2009-04-16
Well thanks

I guess I could try a regular installation if it is working for some of you but last time I wasn't able to start vista with grub (only Ubuntu was working), I had an error when trying to boot on vista but I can't remember which one...

I think it'll be better to try with EasyBCD, because I really don't want to fell into the long long process of trying to repair vista, than reinstall vista (only possible with the dvds sony provides me and that are full of crapwares)

---

