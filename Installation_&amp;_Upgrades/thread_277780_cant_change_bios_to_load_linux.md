---
title: "cant change bios to load linux"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by sts71 on 2006-10-15
Hi Guys

Im frustrated as anything,
I have two IBM PCs, one is a P4 model 8303-JFA and the other a P3 300PL they were purchased with XP installed somewhere on the drive (oem install?) So i dont have disks just the win xp sticker on boxes.

I cant get into the bios, the P4 Ive updated and reflashed bios to update it, Ive tried the F1 key the overflow keyboard trick and removing drives etc but bios will not come up.
The P3 bios comes up but theres no mention of ide order or a way to get it to use the cdrom as startup drive, pc clones Ive had in the past have had these options so I know what to look for.

Ive been all over the ibm site and cant find any info and awaiting the place i bought from to suggest something else.

Ive got 3 versions of ubunti 6.06 so Ive figured theres nothing wrong with disks, only thing I can do is load mozilla thunderbird etc from disks, I cant ge the live cd thing to work to install linux.

On the P4 (IBM 8303) the screen stays black and even the monitor doesnt register that theres a connection, only time is when I dont try to get bios and only thing that works is damn XP.

Has anyone had anything similar to this very frustrating situation thats driving me nuts and I dont know where else to look.
Ive tried the smart boot manager too, using rawwrite it makes the floppy ok but when I try to boot from it the pc just freezes with black screen and even if i leave it for 30mins still nothing, wont boot from anything other then HD!
Thanks heaps in advance if anyone can shed any light here.

Cheers

Steve
(frustrated and really really disliking windows!)](*,)

---

### Post by wpshooter on 2006-10-15
Are you sure that it is the F1 key that opens BIOS ?

Have you tried other keys like possibly the DELETE key, or F2, or F10 ?

Do you not have the documentation/owners manual for the computer.  It should tell you how to get into the BIOS.

Good luck.

---

### Post by wpshooter on 2006-10-15
You know, in thinking about it, I think this is the same or nearly the same model of machine that I am assigned at work.

I believe it is probably the F1 key.

Make sure you are trying the key early enough in the boot sequence.  You may be letting it get by the spot where the key is active.  Just as soon as you hit the power button, just start to tap on the F1 key at about 1/2 second intervals and see if that does not get you in.

Good luck.

---

### Post by sts71 on 2006-10-15
I sure did, tried every key on the keyboard out of frustration!
with speciall attn to esc f1 f8 f10 f12 del space, tried a few times even the hold a numbers of keys to do the keybrd overflow thing didnt work, thanks for the reply thou :)

---

### Post by wpshooter on 2006-10-16
I am back at work today.

My machine is a IBM NetVista 8303-52U.

The BIOS entry key is F1.

If the parameter is set correctly, the entry key for the BIOS should be displayed on the very initial boot screen.

I would thing yours should also be the F1 key.

Perhaps your BIOS has gotten corrupted.

Maybe you need to consider reflashing.

Good luck.

---

### Post by Kateikyoushi on 2006-10-16
How can he refresh the bios if he can only boot to windows ?
Can new flash programs run from it ?

---

### Post by wpshooter on 2006-10-16
> **Kateikyoushi said:**
> How can he refresh the bios if he can only boot to windows ?
Can new flash programs run from it ?

Possibly.  Depends on the BIOS for the IBM.

My preference is to always, if possible, flash from floppy drive, that is, assuming he can boot to that.  If not, yes if possible he should see if there is a windows flash utility available.

P. S. - I consider flashing from Windows as risky.  But does not sound like he has much to lose at this point.

---

### Post by gangalee on 2006-10-25
I have the same problem with every version except 5.04 Hoary.

---

### Post by TigerWolf on 2006-10-25
If you want to reset the bios - remove the battery and then plug it back in.

---

