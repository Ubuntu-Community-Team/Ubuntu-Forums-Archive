---
title: "Grub - no boot screen"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by Ridgerunrbunny on 2012-05-11
Upgraded to 12.04, lost pretty much what I liked about 11 plus Sudo tells me I do not have a grub splash screen available. OooKaay, now what do I do? I have a 3 three hard drives and 3 operating systems. Sudo also says everything is where it is supposed to be except that missing part. Where do I get it?
Bunny

---

### Post by wilee-nilee on 2012-05-11
Can you post the error, it will help to know how you get it. 

Are you able to get to the desktop?

---

### Post by Ridgerunrbunny on 2012-05-11
Yep.

---

### Post by jacksterson on 2012-05-11
Work with us here, man.  Can't help you if we don't know the exact error you're getting.

---

### Post by wilee-nilee on 2012-05-11
Hmm, two questions and a one word answer not sure I will be able to help we are not on the same page.

---

### Post by Ridgerunrbunny on 2012-05-11
Don't understand me? Do any of you who/what Sudo is? Do any of you know what the Grub Splash screen is? If you do not understand this you won't be able to help me.

---

### Post by Ridgerunrbunny on 2012-05-11
Here is a picture, of what I said.
[IMG]http://pic20.picturetrail.com/VOL171/1448011/24111956/402516305.jpg[/IMG]

Also the menu.lst is messed up. . are there any menu.lst editors around?
Bunny

---

### Post by darkod on 2012-05-11
Why are you still running grub1 (grub legacy)? Ubuntu comes with grub2 since 9.10.

If you have a mix of grub1 and grub2 that could mess up the boot process.

If you look in /boot/grub do you also have grub.cfg there or only menu.lst?

---

### Post by Ridgerunrbunny on 2012-05-11
Because NONE of it worked from the initial so-called UPGRADE  of 12.04. I have been dicking around with this piece of junk (being kind) for over a week. At this point I have no idea what the heck is in there. I have removed, reinstalled, removed, totally removed and reinstalled grub over and over and over again.  Why must you ask why questions?

---

### Post by darkod on 2012-05-11
To know if there is any specific reason you need it, or not. We can't help if we don't have info about your system. And even if you reinstall grub, it's usually better to reinstall grub2, not grub1. Depending what tutorials were you following and whether you knew it's grub1.

You can run the boot info script from the link in my signature. That will show more details so we can give you best help. Post the results of the script as explained there.

---

### Post by Ridgerunrbunny on 2012-05-11
Sorry, don't need your info any more, figured it out on my own. By holding shift on boot the "hidden" splash screen appeared and led me to the grub internal workings, including program fixes, new update for grub, fix, etc.
 
Maybe some of these other people with 12.04 black screens could use that info. To bad I only saw that suggestion once in the whole week.

I certainly will not be upgrading Ubuntu again.

---

