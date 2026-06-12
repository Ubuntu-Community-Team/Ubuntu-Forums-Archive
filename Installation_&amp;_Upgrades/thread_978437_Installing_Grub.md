---
title: "Installing Grub"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Ferguson9 on 2008-11-11
Hi 

I have two internal hard drives, one contains Vista and one with Ubuntu. When I boot my computer, it shows up similar to the following [IMG]http://img150.imageshack.us/img150/1682/grub4kt.jpg[/IMG]. 

Is it meant to look like that or should it look like this: [IMG]http://farm3.static.flickr.com/2157/1634931700_d04652fdd6.jpg[/IMG]?? 

Am I missing something? Im running Ubuntu 8.10 by the way.

Thanks

---

### Post by Ferguson9 on 2008-11-11
Do I need to re-install the grub loader? If so, how do I do this and where do I install it to? 

Ive got Vista on hard drive (0) and Ubuntu on hard drive (1)

---

### Post by Linux4theWin on 2008-11-11
I like

---

### Post by caljohnsmith on 2008-11-11
That second screen you show uses "gfxboot" to give the extra eye candy. There are tutorials on how to install gfxboot, but just a caveat: Intrepid uses a newer ext3 file system with 256 byte inodes, as opposed to previous Ubuntu versions that used 128 byte inode file systems as the default. That means it's really important to use the Grub version that comes with Intrepid (0.97-29ubuntu45), or at least as recent as the 0.97-29ubuntu19 version, because older versions of Grub can't handle the newer ext3 partitions.

---

### Post by Ferguson9 on 2008-11-11
Thanks for the reply, I think I will just leave it as it is.

---

### Post by iamblue on 2009-01-22
im having i horrible horrible problem im a newb to linux i just just installed ubuntu 8.10 i did all the updates but whenever it did the reboot this pops  up n it takes me to a similar screen where it says
[IMG]http://i275.photobucket.com/albums/jj294/xxevilvirusxx/0122090001.jpg[/IMG] THATS BOOT UP

[IMG]http://i275.photobucket.com/albums/jj294/xxevilvirusxx/0122090001w.jpg[/IMG]
THATS AT LOGIN

[IMG]http://i275.photobucket.com/albums/jj294/xxevilvirusxx/0122090002.jpg[/IMG]
AFTER LOGIN
             im getting so mad/sad with this i want to have linux but its being stubborn with me can anyone PLEASE HELP ME im feeling :'(

---

### Post by caljohnsmith on 2009-01-22
Iamblue, from the screen shot you posted, it looks like you are booting into "recovery mode" instead of a normal Ubuntu session. How about rebooting, but on start up select the first Ubuntu entry that shows the "2.6.27-9-generic" kernel. Let me know how that goes.

---

### Post by iamblue on 2009-01-22
thanks for replyin back
it was just highlighted but i was bootin from the kernel.when that failed i went to the boot screen and chose ubuntu.the 2 other pictures are the actual pictures of when i boot into ubuntu
it happens everytime i do the updates for linux.(ive installed it 4x)

---

### Post by iamblue on 2009-01-23
nope didnt work either. im still stuck on the same thing. it always happens after i install updates& reboot.but now at the boot menu i see 4 kernels and 4 kernels with safe mode :(:(:(

---

