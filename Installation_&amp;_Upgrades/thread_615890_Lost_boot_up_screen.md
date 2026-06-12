---
title: "Lost boot up screen"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-11-17
I have no idea why this happened. It may be to an install or update, but I do not boot my system often. 
I have lost the boot screen ( the Ubuntu progress bar ) during startup. 
Any ideas?
Thanx in advance!

---

### Post by Brautigam on 2007-11-17
you can always reformat...

---

### Post by lsutiger on 2007-11-17
Heh! this is not Microsoft!

---

### Post by Herman on 2007-11-17
```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro [COLOR=Sienna]**quiet splash**[/COLOR]
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
``` Have you checked in your /boot/grub/menu.lst file to see if it has 'quiet splash' in the kernel options part of the kernel command? 
(You may need to move the slider under the code box in this page to the right to see the whole command I sent as an example).

Regards, Herman :)

---

### Post by lsutiger on 2007-11-17
Here is what I have in that list concerning splash:
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=80854392-9914-4d68-918d-6da826a75872 ro quiet splash vga=773
Should I just delete "quiet splash"?

---

### Post by Herman on 2007-11-17
No, you don't need to delete 'quiet' 'splash', that's the command that tries to turns on the boot-up screen with the progress bar,  if it is working.

There must be some other reason for it not to be working then.

If one of your file systems needs to be checked, the boot splash will start but then it will disappear when it gets to the file system check stage of the boot-up. 
The same thing happens if there's an error in /etc/fstab.

You're not seeing it at all eh?

---

### Post by Diabolis on 2007-11-17
> I have lost the boot screen ( the Ubuntu progress bar ) during startup.

So you can boot your pc and log in? if that is the case maybe you just removed usplash, just install it again. sudo apt-get install usplash.

---

### Post by lsutiger on 2007-11-17
> **Herman said:**
> No, you don't need to delete 'quiet' 'splash', that's the command that tries to turns on the boot-up screen with the progress bar,  if it is working.

There must be some other reason for it not to be working then.

If one of your file systems needs to be checked, the boot splash will start but then it will disappear when it gets to the file system check stage of the boot-up. 
The same thing happens if there's an error in /etc/fstab.

You're not seeing it at all eh?

Correct..I see Grub, black screen then GDM

---

### Post by miriad on 2007-11-18
I have the same problem on a IBM T30 laptop.

usplash is installed, and quiet splash is in my kernel options

Any other ideas?

---

