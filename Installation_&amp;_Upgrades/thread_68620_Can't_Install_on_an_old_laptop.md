---
title: "Can't Install on an old laptop"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by Tony Goodwin on 2005-09-23
Hi everyone, this is my first post.

So I just bought an old laptop. It is a Compaq LTE 5300

I don't know how to install Ubuntu onto it. I have Ubuntu 5.04 on a bootable CD. It will not boot from the CD (**or any CD for that matter**). It can boot from a floppy. I have successfully booted both a Win98 boot disk, and Hal91 (Linux on a floppy).  Unfortunately, the floppy and cd-rom share a bay, and you can't use both at the same time. They may be warm-swappable, but I have been unable to verify that.

It is not networkable. It does have a pcmcia 56k modem card. However it goes to a regular phone line, not an ethernet port. Any ideas?

-Tony

---

### Post by cbudden on 2005-09-23
[QUOTE=Tony Goodwin]Hi everyone, this is my first post.

So I just bought an old laptop. It is a Compaq LTE 5300

I don't know how to install Ubuntu onto it. I have Ubuntu 5.04 on a bootable. CD It will not boot from the CD (or any CD for that matter). It can boot from a floppy. I have successfully booted both a Win98 boot disk, and Hal91 (Linux on a floppy).  Unfortunately, the floppy and cd-rom share a bay, and you can't use both at the same time. They may be warm-swappable, but I have been unable to verify that.

It is not networkable. It does have a pcmcia 56k modem card. However it goes to a regular phone line, not an ethernet port. Any ideas?

-Tony[/QUOTE]
 Where did you get the Ubuntu CD from?

---

### Post by Tony Goodwin on 2005-09-23
I downloaded it on my desktop computer (Windows XP)... burned as an .iso

-Tony

---

### Post by Foaming Draught on 2005-09-23
You may need to tweak the Compaq's BIOS to enable booting from a CD. The default boot sequence will be that the BIOS looks for a boot floppy, then a boot sector on the hard drive. I don't know how to get into set-up on yr particular laptop, it usually involves pressing a function key as the screen first starts bursting into life.
My 6 year-old Dell notebook has had new life breathed into it by running ubuntu, it whizzes along more quickly than my wife's 6 month old super-duper Dell under Win XP.

---

### Post by Tony Goodwin on 2005-09-23
[QUOTE=Foaming Draught]You may need to tweak the Compaq's BIOS to enable booting from a CD. The default boot sequence will be that the BIOS looks for a boot floppy, then a boot sector on the hard drive. I don't know how to get into set-up on yr particular laptop, it usually involves pressing a function key as the screen first starts bursting into life.
My 6 year-old Dell notebook has had new life breathed into it by running ubuntu, it whizzes along more quickly than my wife's 6 month old super-duper Dell under Win XP.[/QUOTE]

Sorry if I was not clear. This is an old laptop, it does not support booting from the cd-rom.

--Tony

---

### Post by Foaming Draught on 2005-09-23
Ah, I've just had a shufti at yr laptop, it is old isn't it. Here's a place to get the set-up file, which you can run on a floppy to change the boot routine to include a CD.

[http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html](http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html)

---

### Post by Tony Goodwin on 2005-09-23
[QUOTE=Foaming Draught]Ah, I've just had a shufti at yr laptop, it is old isn't it. Here's a place to get the set-up file, which you can run on a floppy to change the boot routine to include a CD.

[http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html](http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html)[/QUOTE]


Thank you, not sure if it will work, but I will give it a try...

---

### Post by Foaming Draught on 2005-09-23
Sorry for the implied certainty, I mean which you perhaps might run on a floppy  :-#

---

### Post by BiggoCharley on 2005-09-23
[https://wiki.ubuntu.com//SmartBootManagerHowto](https://wiki.ubuntu.com//SmartBootManagerHowto)
Take a look at this.
Charley

---

### Post by Tony Goodwin on 2005-09-23
Unfortunately, since the cd-rom and floppy can not be used simultaneously, that won't work.

-Tony

---

### Post by Tony Goodwin on 2005-09-23
[QUOTE=Foaming Draught]Ah, I've just had a shufti at yr laptop, it is old isn't it. Here's a place to get the set-up file, which you can run on a floppy to change the boot routine to include a CD.

[http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html](http://h18007.www1.hp.com/support/files/obsolete_diagnostics.html)[/QUOTE]


Yeah, it requires a 720kb floppy....

so, it didn't work.

-Tony

---

### Post by Tony Goodwin on 2005-09-24
Any other suggestions?

---

### Post by az on 2005-09-24
1.  You can install debian woody from floppies and dist-upgrade.

2.  If there is already a windows OS installed, you can use loadlin.

---

### Post by Tony Goodwin on 2005-09-24
[QUOTE=azz]1.  You can install debian woody from floppies and dist-upgrade.

2.  If there is already a windows OS installed, you can use loadlin.[/QUOTE]


I may try that .


Thanks

---

