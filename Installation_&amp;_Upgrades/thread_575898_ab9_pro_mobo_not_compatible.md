---
title: "ab9 pro mobo not compatible?"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by topstinger2007 on 2007-10-14
I have an ABIT ab9 Pro motherboard ([http://www.newegg.com/Product/Product.aspx?Item=N82E16813127004&Tpk=ab9%2bpro](http://www.newegg.com/Product/Product.aspx?Item=N82E16813127004&Tpk=ab9%2bpro))
and I think its causing problems for installation of Ubuntu 7.04 (Feisty Fawn). Im using a SATA harddrive and would like to do a dual boot with vista ultimate. I have a geforce nvidia 8800gts 320mb. core 2 duo 2.4
Can anyone help please?
-Jake

---

### Post by BatPenguin on 2007-10-20
Did you solve this problem? I have the same problem and huge problems...Gutsy live CD will boot until I see mouse cursor and then hang, and I can't even install Windows (was going for a dual-boot) since the machine reboot when the CD starts loading. I think it's related to the Serial ATA hard drives / Cd that I have since gutsy won't go even to the X part without adding "irqpoll" to boot options. I got that option from a previous search.

---

### Post by timothyyip on 2007-10-21
Hi, I'm having the same problem here, I posted about my Gutsy installation experience here:

[http://ubuntuforums.org/showthread.php?t=583924&highlight=ab9](http://ubuntuforums.org/showthread.php?t=583924&highlight=ab9)

At first I thought it was HDD incompatability too, however, after searching for clues in many other directions, based on:

-search forum result here: [http://ubuntuforums.org/showthread.php?t=583924&highlight=ab9](http://ubuntuforums.org/showthread.php?t=583924&highlight=ab9)
-this review post: [http://www.phoronix.com/scan.php?page=article&item=699&num=1](http://www.phoronix.com/scan.php?page=article&item=699&num=1)
-and many archives posts

I think we can conclude that theres a compatability issue with AB9's JMicron chipset (which to be honest, is the only dodgy part of this board's spec in the first place).

Phoronix site has very good reviews concerning hardware with linux, and theres certainly no issue with SATA drives, especially Western Digitals which I am using.

Sad really, but at least it will now give me an excuse to upgrade to newer P35 chipset M/Bs, it seems Asus is the way to go.

---

### Post by BatPenguin on 2007-10-21
Thanks for the message. I'm hoping a BIOS update might help a bit, don't know yet -- didn't get it updated yet since I don't have a floppy drive. Unbelievable how the MB manufacturers can't provide a CD image for flashing, not many have floppies anymore. Anyway, I just prepared a USB key for that, hopefully it works.

From my searches and your experiences, it really does look like the JMicron parts are causing the problem.  Do you happen to know which SATA ports are the JMicrons? I have only 3 SATA devices (2 HDs and one DVD) and since there's 6 ports and supposedly only 2 are controlled by the JMicron thing, I suppose I could avoid those by simply NOT using them. Any idea which ports those would be? They're numbered 1 -6 and I have no idea which ones are which, unfortunately. The Motherboard manual didn't help much either.

Edit: just to clarify: my motherboard is the Abit AB9 QuadGT, so not exactly the same board, but apparently they're extremely similar. The other stuff is 6 GB RAM, Quad Core, 2 SATA hard drives and a SATA DVD burner.

---

### Post by ilmawi on 2007-10-29
i sent feedback to abit about AB9 and linux thru their form on their website. I wish that everybody, who owns AB9,  would do the same. 
Then maybe they would do something about it...

I'm going to keep on doing it until something happens.

[Here  is the link to the form.]("http://www2.abit.com.tw/page/no/contact/feedback.php")

Please let them know!

---

### Post by BatPenguin on 2007-10-29
I've since gotten this to work pretty well. I updated the BIOS to the latest version (not exaxctly easy without a floppy drive...) and disabled the JMicron SATA interfaces, I'm not using all SATAs anyway so I figured just disabling in BIOS would be safest.I also set the other SATA interfaces to use IDE mode. Now when I installed / booted Gutsy with  the "irqpoll" kernel option, it insatlled fine. I haven't had any problems with this since, I think the BIOS version was the biggest issue plus the "irqpoll" switch is essential or everything hangs.

I'll send feedback of course as well, but give the latest BIOS and that option a try if you haven't already! Good luck.

---

### Post by topstinger2007 on 2007-12-06
> **BatPenguin said:**
> I've since gotten this to work pretty well. I updated the BIOS to the latest version (not exaxctly easy without a floppy drive...) and disabled the JMicron SATA interfaces, I'm not using all SATAs anyway so I figured just disabling in BIOS would be safest.I also set the other SATA interfaces to use IDE mode. Now when I installed / booted Gutsy with  the "irqpoll" kernel option, it insatlled fine. I haven't had any problems with this since, I think the BIOS version was the biggest issue plus the "irqpoll" switch is essential or everything hangs.

I'll send feedback of course as well, but give the latest BIOS and that option a try if you haven't already! Good luck.

1. Do I have to worry about disabling the JMicron SATA interfaces? I use my hard drive using SATA so I would need this enabled...right?
2. Do I need to set the other SATA interfaces to use IDE mode?
3. You mentioned the "irqpoll" switch. How can I install / boot Gutsy with  the "irqpoll" kernel option? How do I change it?

My main problem is that I get a bunch of errors when trying to start from live CD. Please somebody help.
-Jake

---

### Post by zozobra on 2008-01-31
> **topstinger2007 said:**
> 1. Do I have to worry about disabling the JMicron SATA interfaces? I use my hard drive using SATA so I would need this enabled...right?
2. Do I need to set the other SATA interfaces to use IDE mode?
3. You mentioned the "irqpoll" switch. How can I install / boot Gutsy with  the "irqpoll" kernel option? How do I change it?

My main problem is that I get a bunch of errors when trying to start from live CD. Please somebody help.
-Jake

You can use IDE, RAID, or AHCI mode in the BIOS. As for the installation, you would hit F6 for other options. When you hit this, it will pop up a string that ends with --. After the --, type irqpoll and then hit enter. 

This worked for me on my AB9-Pro. My Hard Drive is connected to the ICH8R ports (SATA 1-6), I have the JMicron and other SATA controller disabled.

---

