---
title: "Two Ubuntus installed - how to remove one?"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by abakan on 2009-12-11
Hi guys!

It was my first experience with Linux so when I installed Ubuntu I did it twice. So, I've got two systems installed and GRUB says:

Ubuntu, Linux 2.6.31-16-generic-pae
Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)
Ubuntu, Linux 2.6.31-15-generic-pae
Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)
...memory check...
plus VISTA


Is there a way to remove one of the Ububtus?

Thanks in advance for any help!

---

### Post by cosine352 on 2009-12-11
you can install partition editior and reformat the partion of the ubuntu you do not want. 

In terminal type 
> sudo apt-get install gparted

After installation type > sudo gparted in the terminal and look for the proper partition to format. 

WARNING: make sure you are formating the right partition as you will lose everything in that partiton.

---

### Post by darkod on 2009-12-11
> **cosine352 said:**
> you can install partition editior and reformat the partion of the ubuntu you do not want. 

In terminal type 


After installation type  in the terminal and look for the proper partition to format. 

WARNING: make sure you are formating the right partition as you will lose everything in that partiton.

DO NOT DO THIS!!! Not right now at least.
The part of the grub menu you supplied does NOT mean two ubuntus, it just means two kernels.
Yes, open Gparted and take a look at your partitions, but don't delete anything. If you are not sure, post a screenshot of Gparted here so someone can take a look.
Those entries 31-15 and 31-16 might be different ubuntu versions but more likely it seems like two kernels of the same version. If you really did install twice maybe the second install went over the first one.

---

### Post by cosine352 on 2009-12-11
> **darkod said:**
> DO NOT DO THIS!!! Not right now at least.
The part of the grub menu you supplied does NOT mean two ubuntus, it just means two kernels.
Yes, open Gparted and take a look at your partitions, but don't delete anything. If you are not sure, post a screenshot of Gparted here so someone can take a look.
Those entries 31-15 and 31-16 might be different ubuntu versions but more likely it seems like two kernels of the same version. If you really did install twice maybe the second install went over the first one.

darkod is right. I missed the kernel versions. your installation is fine.

---

### Post by tedk89 on 2009-12-11
ok I have the same thing, except I just want to remove the kernal entry from grub or several entries from grub, the list has been slowly growing... Help would be greatly appreciated, sorry I don't mean to hijack this thread.

---

### Post by darkod on 2009-12-11
> **tedk89 said:**
> ok I have the same thing, except I just want to remove the kernal entry from grub or several entries from grub, the list has been slowly growing... Help would be greatly appreciated, sorry I don't mean to hijack this thread.

It's always recommended to keep at least one older kernel which is working fine, in case you meet some issues with the latest one.
Otherwise, go into Synaptics Package Manager (in System-Administration), and look for the kernels you want to remove. You can try putting into the filter box "linux" or "2.6.31-14", etc.
Remove the ones you want to remove. Do
sudo update-grub

afterwards to update the menu (if this was a 9.10 clean install and you have grub2).

---

### Post by tedk89 on 2009-12-11
thank you!

---

### Post by abakan on 2009-12-11
> **darkod said:**
> DO NOT DO THIS!!! Not right now at least.
The part of the grub menu you supplied does NOT mean two ubuntus, it just means two kernels.
Yes, open Gparted and take a look at your partitions, but don't delete anything. If you are not sure, post a screenshot of Gparted here so someone can take a look.
Those entries 31-15 and 31-16 might be different ubuntu versions but more likely it seems like two kernels of the same version. If you really did install twice maybe the second install went over the first one.

Thanks a lot! According to Gparted there is no other ubuntus installed (as far as I can tell).

---

### Post by A_T on 2009-12-11
What would be the advantage of removing one of the kernels? Assuming both work OK.

---

### Post by darkod on 2009-12-11
> **A_T said:**
> What would be the advantage of removing one of the kernels? Assuming both work OK.

Nothing really. Less crowded grub menu. The kernels don't take too much hdd space so I'm not aware of any advantage myself.

---

