---
title: "Install problem."
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by lylebarras on 2008-12-02
Hi all,

Sorry to bother you all with what is probably a dead simple thing but I am having a problem installing Ubuntu.

I have picked up a cd from linux emporium and also got one of their cd's. I also picked up the latest 8.10 cd. All these seem to do the same thing.

I have a laptop made by tiny. Its about 4 years old and runs xp. I put the cd in and install but all I end up with is a kind of command prompt. It looks (something) like this ubuntu@ubuntu$ (as far as I can recall)

The installation stops there. This is the same if I use the install or the try inside windows option.

I hope you can help.

---

### Post by Pumalite on 2008-12-02
Download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Try the Alternate CD.
Do md5sum on the iso, test CD for integrity. Do not use CD-RW
Burn at 4x or less

---

### Post by lylebarras on 2008-12-08
Thanks for that. I got the new CD. I thought that I should test it so I set it up without a problem on a pc at work. (Really should remove that now :o )
Got home and gave it a whirl. I had exactly the same situation. the text that the install finishes up on says nothing of errors but talks about how to use root commands etc.

It seems for all the world that it is working except it can launch the GUI side of things.

I'm getting the feeling that it is a hardware kind of issue with my old laptop. I may have to file in under B1N or at worst case switch back to Windows.

---

### Post by Pumalite on 2008-12-08
If you have 256 MB of RAM or less; go with Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)
Or DSL or Puppy
If it's not the memory. Could be your graphics. Graphics?

---

### Post by karamu on 2008-12-08
I had a similar problem when trying to install Xubuntu on an old laptop- I didn't manage to resolve it unfortunately and ended up putting Windows 2000 on it- XP installed but ran very slowly (as I said it was an OLD laptop!!). Sorry I can't be any more helpful.

---

### Post by Pumalite on 2008-12-08
If you have 512 of RAM or more and the Alternate CD does not work; you could try some boot parameters:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 vga=789 vga=791
To be tried one by one or in different combinations.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

