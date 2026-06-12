---
title: "Unable to boot - Intel P965 Express MOBO"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by jimbosyn on 2006-07-29
Hello everyone.  I am unable to get ubuntu to boot/install on my new system. I am a linux administrator by trade, and this one has be stumped.  Here are the specs on the system
-
Intel BOXDP965LTCK Socket T MOBO with the intesl p965 express chipset.
Intel Pentium D 805 proc
2 gigs ram
nvidia 7900GT pcie vid card
-
I feel pretty certain that my issues are with the motherboard and some sort of kernel acpi or apic bug.  It should be noted that WinXP runs like a charm with no issues whatsoever.  

I am simply unable to get the live CD to boot up.  I get the grub prompt and have tried acpi=off, noacpi, noapic, and I am still unable to boot.  The error varies based on the install options I pass to the kernel.



just hitting enter yields
[45.271596] PCI: Failed to allocate mem resource #6:200000@90000000000 for 0000:01:00.0


live acpi=off - yields
[0.00000] BIOS bug, no explicit IRQ entries, using default mtable. (tell your hw vendor)

live noapic - yeilds
[0.00000] BIOS bug, no explicit IRQ entries, using default mtable. (tell your hw vendor)
[52.236243] PCI: Failed to allocate mem resource #6:200000@9000000000 for 0000:01:00.0


Any suggestions?

---

### Post by jimbosyn on 2006-07-30
Hello everyone.  Does anyone have any suggestions for me?  This chipset (intel 965 express )is the only current one that will work with the new core 2 duo chips that intel has released.  If this is a kernel bug or ubuntu issue,  there will be a whole lot of questions in the near future once the chips get into the retail channels.  I bought this board for the explicit reason that I wanted a core 2 duo ubuntu system.  I'll try with the most recent suse and knoppix to try and determine if this is indeed a kernel issue.  I will also try with the new edgy pre-release and to see if the new kernel 2.6.17 will work.  I will report back here if I find a solution.

---

### Post by jimbosyn on 2006-08-01
Update.  

Edgy does not work either.  The 6.06 dapper alternative disc gets further than the live cd.  It looks like the problem is the CD drive is not being detected.  The installer is unable to find the CD media.  The text installer prompts me to either load the driver from floppy or manually select the kernel module.  I have no floppy driver disc, so I try each kernel module to no avail.  

Knoppix 5.01, the most recent version fails as well.  I suspect the ide controller chipset on this new board.  This board is a brand spanking new chip designed by intel to support the new core 2 duo chip.  I'll do some more debugging and possibly try an alternate install method.  Maybe a network install will not fail.

---

### Post by Cynical on 2006-08-04
Wanted to let you know you arent the only one. I am getting the same errors. I also suspect its intels fault for removing ide support and forcing manufacturers to add it themselves. I've tried an alternative install cd and several distributions, nothing has helped. I've also used multiple dvd drives. Someone needs to figure this out soon :(

---

### Post by Cynical on 2006-08-05
There are two solutions, but I'm only going to mention the one that involves just a single computer. If you have windows xp installed (and it sounds like you do) you can do what I did and use [instlux]("http://sourceforge.net/projects/instlux") to install ubuntu 6.06 over the internet. It worked flawlessly for me and now I'm a happy ubuntu user once again!

---

### Post by fxtl on 2006-08-16
Edit: never mind..

---

### Post by PinkDaisy on 2006-08-19
[SIZE="2"]Hi, i have the same problem, at first i tried to install ipcop, when that didn´t work i tried ubuntu dapper, same reslult.

But i did notice that the usb harddrive i tried did actually work, so i´m thinking that a usb cdrom should work perfectly since it dosen´t have anything to do with the ide controler.

Now i´m just wating for my local computer store to get the usb-ide conveter in stock so i can buy it and try it out.[/SIZE]

---

### Post by matty429 on 2006-08-23
Booting from USB cd didn't work for me...Gigabyte 965P-DS3

---

### Post by dens57 on 2006-08-23
Me I solved the issue by disabling usb keyboard and usb mouse support in bios.

---

### Post by hamstergirl on 2006-08-28
I've tried what was suggested here but I can't seem to get mine to work either.  Unfortunately I don't have a copy of windows I can use to allow me to install linux.

---

### Post by willnapier on 2006-09-01
Hi. I recognise most of the above. I have just bought a system with an intel core 2 duo processor. I also get these problems and have not been able to use the new computer at all. I have managed to work without windows for three years and don't intend to resort to installing it just to get ubuntu working (I acually use kubuntu). I would really like to know what the other, two-computer option was, mentioned above - or any other solution. With thanks for any help

Will

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this P965 issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by glatzor on 2006-09-27
Use the daily edgy cd image of today. the corresponding patches are now in.

---

