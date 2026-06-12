---
title: "Live CD Boot problem"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Ennui on 2007-03-03
I tried to boot the Ubuntu 6.06 LTS CD on my laptop, but it always freezes up. I know the CD has no defects because I ran it on my desktop and it loaded live just fine. I also ran the error check on my laptop and there were no errors. I tried starting it in graphics safe mode and it still freezes. It freezes during the black screen when it is checking my hardware and such. Can anyone help me with this?

By the way my laptop is new and in good condition.

It is: 1.6 ghz AMD Turion 64
1 GB ram
80 Gb Hard drive

---

### Post by tgalati4 on 2007-03-03
Did you try a live 64-bit version?  Perhaps the Live 32-bit version is missing something to put the Turion64 into 32-bit mode?

---

### Post by rsambuca on 2007-03-03
> **tgalati4 said:**
> Did you try a live 64-bit version?  Perhaps the Live 32-bit version is missing something to put the Turion64 into 32-bit mode?

No.  That is not the problem.

Try using some of these as boot options (F6 at the main menu)

ide=nodma  

If that doesn't work, try adding all of this:

irqpoll pci=noacpi noapic nolapic acpi=off

---

### Post by Ennui on 2007-03-04
Thanks rsambuca. I have no idea what it does, but I typed ide=nodma and it worked. :)

---

### Post by rsambuca on 2007-03-05
ide=nodma turns of Direct Memory Access to your IDE drives.  It is a defect with some chipsets.  If you are going to install ubuntu onto your hard drive, you will want to turn dma back on or it will take a long time without dma.  To turn on DMA back on, you can enter these commands in a terminal (Accessories ->Terminal)
```
sudo hdparm /dev/hda -d1
```

You will have to do this for every IDE drive that you have (ie hda, hdb, hdc, etc.)

Good luck, and welcome to ubuntu.

---

### Post by tgalati4 on 2007-03-05
Good call.

---

### Post by Ghokun on 2008-01-25
Hi,
I have the exact problem as Ennui had. I just bought a new laptop with AMD 3600+. At first it did not have any OS. So I tried loading with my old xubuntu 6.06 live cd to check components and such. It worked fine and I started downloading the new version of the ubuntu. While the dowload process is going on, I tried installing Windows XP just for seeing my notebooks performance. I installed all the drivers that has been supplied by the cd with my notebook.

Everything here was good. Then my download finished and I burned the 7.10 Ubuntu distro. When I try to boot my live cd, it crashes at a random point. Sometimes at splash screen sometimes at black screen where there is nothing but a cursor on the top left like " _ ".

I tried adding ide=nodma just before the -- . It passed the first crashing but it stopped when the ubuntu cursor appeared on screen. Tried again and crashed just like the old times :(

After a night with full of headaches my last hope was adding 

irqpoll pci=noacpi noapic nolapic acpi=off

this line to the boot screen. 

Guess what ? It worked! And I am so happy now since I am now installing ubuntu on my new notebook :)

My question is should I change anything after installation as in the last post of rsambuca.

Thanks :)

---

### Post by Ghokun on 2008-01-26
My happiness did not last long :( 

After I succesfully  installed ubuntu  , I could not open it. When it is loading, it crashes just like the live cd :(

---

