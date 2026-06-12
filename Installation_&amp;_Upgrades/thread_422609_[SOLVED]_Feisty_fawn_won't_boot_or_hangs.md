---
title: "[SOLVED] Feisty fawn won't boot or hangs"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by sikke on 2007-04-25
Edit: See my last post.

Hi!

I upgraded to feisty from edgy and now the system only boots about four times out of ten. If it boots the system hangs in few seconds or minutes. So, I made a clean install from CD and the same thing happens. My hardware is quite new, Intel Core 2 Duo, 1024GB RAM, Abit ab9 mobo... What could cause this? No problems with edgy except few random hangs in a month or two.

Thanks in advance!

Sikke

---

### Post by alynx on 2007-04-25
I've got a simmilar problem.  It seems like it hangs after i updated.  But it is only my X that won't start.  I need to press ctrl + alt + f7 to get it up and running.  Can someone help out please ? 

Could you please check if you have the same problem mate ?

---

### Post by Floor19 on 2007-04-25
Hi,

I don't know if i have the same problem but after upgrading my notebook powers off when booting. (Not all the time 3 out of 5 times). 

When i boot in recovery everything works untill loading swapfile and/or configuring network. The light of my pmcia wireless card lights on but right after that my sytems powers off (cuts of power). Anyone has the same problem and has the solution?!

Hoping for an answer...

F

---

### Post by sikke on 2007-04-25
When my machine doesn't boot it does load grub and then starts loading ubuntu but hangs when splash screen appears...

---

### Post by steveleonard2 on 2007-04-28
My feisty fawn 7.04 clean install on a blank hard drive hangs on the boot too, also at the grub splash screen. My hardware works fine with dapper drake 6.10. No problems with that. I noticed in grub that the default script does not end with a line with the word 'boot'. Could that have anything to do with it?

---

### Post by sikke on 2007-05-18
Still no go with this. Here's [a screenshot]("http://docs.google.com/View?docid=dd8rvc69_2f63mdr")

---

### Post by weatherman1293 on 2007-05-20
After getting my wireless to work, mine hangs at eth0 not ready.

---

### Post by sikke on 2008-02-13
After a while I stopped trying and few days ago I installed 7.10 and got the same problem. So, I started googling and found few tips and got the answer. 

Add irqpoll to the end of the kernel line in grub's menu.lst file:

/boot/grub/menu.lst

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=1a87e89d-c9c5-41a0-8e2b-bf9705152a2d ro quiet splash **irqpoll**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

It seems to be a problem with the JMicron SATA/IDE chip on the mother board.

---

