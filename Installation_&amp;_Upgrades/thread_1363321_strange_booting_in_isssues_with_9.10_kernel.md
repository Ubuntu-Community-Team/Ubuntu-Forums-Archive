---
title: "strange booting in isssues with 9.10 kernel"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2009-12-24
hi all !

I had installed Ubuntu 9.04 from a Live CD. I then upgraded it to the next version (9.10) over the internet.

Now, mine is a dual booth system and in the beginning i get to choose between XP and 2 kernels of 9.10.

These are, from top to bottom-

Ubuntu 9.10, kernel 2.6.31-16-generic
Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.28-17-generic
Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)

#1 why is the 16 number kernel shown first? isn't the numnber 17 higher than the 16 ?
#2 strangely, when i try to boot using the second option (i.e. the number 17 kernel), the pointer simply locks into place. i am able to enter the password using the keyboard only.
moreover, the pointer remain frozen in place even when hte OS desktop comes up. i then have to restart using the Alt+F4 command which brings up the shutdown menu. Again, this command does not seem to work in the same way with my normally functionining kernel.
Finally, I am able to work normally when i choose the first option, Ubuntu 9.10, kernel 2.6.31-16-generic.

Any ideas as to what is happening here ?
Thanks!

---

### Post by oldfred on 2009-12-24
28-17 is older than 31-16. It seems because you did an upgrade it is still showing the old kernel 2.6.28-17 from 9.04 which now will not work from the updated install. You can go into synaptic and uninstall the old kernel, just be sure not to uninstall your working kernel.

---

### Post by AM_SOS on 2009-12-26
hey,
thanks oldfred ! i did exactly what you said and carefully uninstalled 28-17 in synaptic. and now i have an uncluttered boot in screen and my laptop boots in just fine.
btw, is it a good idea to keep uninstalling old kernels ? i mean one just needs the one to boot in , right ? and this would have to be the latest one, no ?
so, wouldn't it be a good practice to keep uninstalling old kernels ?
thanks

---

### Post by oldfred on 2009-12-26
We normally recommend that you keep 2 kernels just in case you discover some new problem in the new kernel with your specific system. If you have used new kernel for a while it should be ok to delete the older ones.

With old grub I set my menu.lst to show only 2 kernels. There does not seem to be a setting for this in grub2. Because I have several versions of Ubuntu installed and rarely housecleaned kernels and grub2 is so good at finding all those kernels my current grub.cfg menu is very busy. Another case of do as I say do not do as I do.

If you want to delete versions if tis always best to check exactly which one you are using, since it is usually the last two digits.

Grub version
grub-install -v
lsb_release -a

---

### Post by AM_SOS on 2009-12-28
hey thanks!
will keep this in mind in the future.
please ignore the reply i've sent you about not getting your message in my inbox.
thanks!

---

