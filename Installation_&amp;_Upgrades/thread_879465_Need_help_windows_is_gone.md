---
title: "Need help windows is gone"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by spwn on 2008-08-04
Hey, i have kind of a little problem...

you see i have installed xubuntu 2 times, one successfull but too little space, and another one with somewhat more space.

However, i thought since im doing reinstalls ect. i might (since im dual booting) let me just reinstall windows.

I have a "recovery mode" for that. Wich i used to recover windows.
The mode says it was successfull.. however windows does not appear in my boot list.

I know for a fact that windows still needs to have that little configuration thingy with first setup. But if i cant get to it how do i do this.

My windows partition is still there, i checked.. however like i said. It probably still needs to complete the install (keyboard layout, language, ect...)

It's the dual boot in the very beginnning that's probably cousing this.
But can i get my xubuntu to re-check the dual boot, or refresh it or something.

Please help me...

---

### Post by kspncr on 2008-08-04
try using the super grub disk to help boot windows:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's pretty simple if you choose "super grub disk with help"

---

### Post by spwn on 2008-08-04
So if i burn this to a disk i will be able to boot windows (the install) ?

---

### Post by kspncr on 2008-08-04
yes, make sure you choose the "with help" option. I can't remember the exact path to get there, but if you navigate around a little you'll a "fix boot of windows" option and that may get it working

EDIT: not sure what you mean by "the install"

---

### Post by spwn on 2008-08-04
what i mean by the install is ...

well i have this option to press a button and get this "acer recovery" and possibility to reinstall windows entirely without a recovery cd..

but after this recovery you still get this bleu screen first, with little sound that asks for your keyboard layout, language, if you want to register ect...

i said, that i thought it was that i didn't configure it, that its that why xubuntu boot cannot find it

---

### Post by kspncr on 2008-08-04
okay, so the Windows partition is still there and you never got rid of windows, because you were dual-booting.

It seems to me like you won't need to completely reinstall Windows and it's just a mbr problem and the super grub disk can fix that. If you follow my (kinda poor) instruction above, I think you'll be fine.

Best of luck to you.

---

### Post by erickghint on 2008-08-04
check this out first. 

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)


it's for vista, however the instructions are just about the same for xp.

---

### Post by uberlube on 2008-08-04
1) You should format all your Linux partitions and then run your Windows recovery to make sure it is installed first and foremost.

2) Once Winblows is installed defragment your hard drive to make sure all your blocks are lumped together and then resize your win partition to whatever you want it to be so there is sufficient room for Linux.

3) Install Linux on your remaining space with your preferred partitioning.

4) Because Winblows was installed first Ubuntu will automatically recognize it in grub and you will be good to go.

5) Download Eric Cartmans version of "come sail away" by Styx. Its hilarious! :)

---

