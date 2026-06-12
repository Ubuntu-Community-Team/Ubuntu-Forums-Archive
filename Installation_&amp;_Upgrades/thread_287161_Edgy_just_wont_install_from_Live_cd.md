---
title: "Edgy just wont install from Live cd"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by tep200377 on 2006-10-28
I've downloaded ALL of the edgy isos by now. I first tried out the AMD desktop iso. It gets into the start menu, where i can choose to install and boot the live cd. Then it all stop working. It seems to hang right after the kernel has begun to start up. The progress image looks fu..ed up .. also 

I've tried many things and alle the iso variants. 
Even tried to disable the ACPI controlls in the bios. Thats becuase it said something about that when we tried to install it on my friends AMD machine. 

What am i doing wrong ?
I've got an Asus A8n32SLI Deluxe with a dual core cpu.
2Gb rams, and Sata disks. and a 6600 GT

---

### Post by MuFFiNuk on 2006-10-28
Im having a similar problem, are you using a sata dvd drive?

---

### Post by Wd2048 on 2006-10-28
I too am having this problem. The problem i think is the nvidia drivers are not being used correctly, if at all, from the live cd. I'm trying to find a way around it. I'll let you know if I find anything out.

---

### Post by joegiampaoli on 2006-10-28
When you download an iso image of an **Operating system**, it is best to burn it at low speeds or CD's will have errors, I always burn mine between 4X and 8X.

---

### Post by tep200377 on 2006-10-29
Muffinuk: Im not using sata dvd drives :)  Just plain Plextor CD-rom IDE

joegiampaoli: I burned it at 32x, but i can try it on 4 now .. got plenty of time ;)

Thanks for the replies guys !

---

### Post by dgregory81 on 2006-10-30
I'm having the same problem but with an ati card.  I know that when installing Dapper X used to crash and you could get to the command line and do sudo apt-get install xorg-driver-fglrx but I can't even reach the command line from the cd because the kernel load hangs.  I also had the same problem when i did the distribution upgrade by using synaptic so it's definitely not a problem with the speed at which the cd is burned.  I hope either ubuntu or a very smart user can figure this out.

---

