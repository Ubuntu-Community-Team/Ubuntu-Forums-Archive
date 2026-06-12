---
title: "Impossible to install Ubuntu on HP"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by Sanix on 2008-10-24
Hi,
I tried to install Ubuntu 8.04 on a HP Vista 8530w.

I get errors like cpu#1 busy. If I use options such as nolapic and so on, I still can't install it. I get a lot of sata errors.

System specification:
[http://www.neptun.ethz.ch/hardware/modelsPC/h08_specs_large_EN](http://www.neptun.ethz.ch/hardware/modelsPC/h08_specs_large_EN)

---

### Post by logos34 on 2008-10-24
Looks like you're not the only one having problems:

[http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

---

### Post by Sanix on 2008-10-25
Thanks for the link. So this means, it's actually an Ubuntu bug or more specific the kernel, which doesn't work for such a new notebook?
Is there kind of a "rule", how long it will take until this bug will be fixed. Because now I'm using Vista and I really hate it. Nearly nothing runs correctly.

---

### Post by falstaff on 2008-10-25
Hello Sanix,

I wrote you also in the launchpad bug which i opened this week. For me ubuntu works when I use acpi=off, although its not really a solution to work without acpi...

If you can boot ubuntu, you have to install the latest NVidia Graphic driver (177.80, not included in Ibex). You can find a manuel here [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual"). 

Does Sound works for you? For me not atm, but i dont know what the problem might be... aplay -l show devices, but it doesnt work:
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: AD198x Digital [AD198x Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

Anyone any idea?

Bye
falstaff

---

### Post by falstaff on 2008-10-25
News from here:

I installed Ubuntu 8.10 AMD64. I had to activate the failsave graphic mode (F4) and add advanced options (F6) and add there acpi=ht. With this options the installation went fine!

Strange: I tried once again to boot with acpi, and it worked! But only once, so the acpi bug seems to be a sporadical bug. 

After i started sucessfully I installed nvidia restricted drivers, and they are working now like a charm!

I found out that sound at the headphone 3.5 jack works! So only speaker does not work, any how to solve this?

bye
falstaff

---

### Post by Sanix on 2008-10-25
Thanks a lot. I'm going to give a try but a question, do you have an AMD Processor? I've got an Intel. It's kind of "funny". I tried 8.10 and pressed install with several options but finally it starts ubuntu in text mode. But it doesn't start any installation. So I don't know if I can install the nvidia driver, I will probably try tomorrow.

---

### Post by falstaff on 2008-10-25
I've got an Intel Processor also. AMD64 is a processor extension for 64-Bit, which also works under Intel Processors... So you can use more than 3 GB Memory...

With Ubuntu 8.10 Release Canditate it worked for me by pressing F6 at the boot screen and type acpi=ht. With this boot option he doesnt load ACPI except the multi core support...

bye
falstaff

---

### Post by freak42 on 2008-11-01
I got acpi working on the 8530w with Ubuntu 8.10 by fiddling in the bios (Version F.04)
Try disabling "Fan always ON on AC Power" under System Config -> Device Config in the BIOS. This seemed to make it possible for me to boot without any ACPI bootflags during boot. (suspend still doesn't work, though).

Other people confirmed that this helps on [http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

---

### Post by falstaff on 2008-11-02
Thanks freak42, this solution works for me!

---

### Post by talofo on 2008-11-16
> **freak42 said:**
> I got acpi working on the 8530w with Ubuntu 8.10 by fiddling in the bios (Version F.04)
Try disabling "Fan always ON on AC Power" under System Config -> Device Config in the BIOS. This seemed to make it possible for me to boot without any ACPI bootflags during boot. (suspend still doesn't work, though).

Other people confirmed that this helps on [http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

I'm also having the same laptop.
What are the downsides of changing that option on Bios?

Thanks.

---

### Post by freak42 on 2008-11-16
Well the fan won't be always on when on AC Power...

However I don't consider this to be much of a downside, I prefer quiteness over a couple of degrees lower cpu temperature.

If you are worried about this, here the fan works normal when on AC Power, cooling when needed, and turning off again when the temp is lower.

---

### Post by talofo on 2008-11-16
> **freak42 said:**
> Well the fan won't be always on when on AC Power...

However I don't consider this to be much of a downside, I prefer quiteness over a couple of degrees lower cpu temperature.

If you are worried about this, here the fan works normal when on AC Power, cooling when needed, and turning off again when the temp is lower.

Hmm... ok. Seems fine to me.

Have you completly install Ubuntu on your HP. I'm waiting for my hp8530p and I'd love to install Ubuntu and start thinking about a M$ alternative. But I'd like to have it fully functional...

Thanks a lot.
MEM

---

### Post by freak42 on 2008-11-16
Yes I have ubuntu installed.

however not everything works as expected:
- monitor brightness cannot be controlled from ubuntu or the laptop function keys (at all!)
- using the dvi and hdmi outputs are sometimes cumbersome (with nvidia cards)
- hibernate and suspend doesn't really work 

look here:
[http://www.linlap.com/wiki/HP+EliteBook+8530P](http://www.linlap.com/wiki/HP+EliteBook+8530P)

and 

[http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

hth

---

### Post by talofo on 2008-11-16
> **freak42 said:**
> Yes I have ubuntu installed.

however not everything works as expected:
- monitor brightness cannot be controlled from ubuntu or the laptop function keys (at all!)
- using the dvi and hdmi outputs are sometimes cumbersome (with nvidia cards)
- hibernate and suspend doesn't really work 

look here:
[http://www.linlap.com/wiki/HP+EliteBook+8530P](http://www.linlap.com/wiki/HP+EliteBook+8530P)

and 

[http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

hth


Thanks. One last question, in similar cases that you may know about, what will happen on the future? Normally things get done, or the fact that, Ubuntu does not support HP our HP does not support Ubuntu, is just a fatality?

In the product description they (HP) say that this is Suse Enterprise Desktop Certified bla bla, does this actually means something? Maybe... openSuse work?

But if openSuse and Ubuntu are both based on Linux, why does it not work on Ubuntu?

Thanks a lot.

---

### Post by freak42 on 2008-11-16
> **talofo said:**
> Thanks. One last question, in similares cases that you may know about, what will happen on the future? Normally things get done, or the fact that, Ubuntu does not support HP our HP does not support Ubuntu, is just a fatality?

In the product description they (HP) say that this is Suse Enterprise Desktop Certified bla bla, does this actually means something? Maybe... openSuse work?

But if openSuse and Ubuntu are both based on Linux, why does it not work on Ubuntu?

I actually don't know that much about the whole fixing/integrating stuff.
I think usually it is considered a linux bug when something that should work under linux (like changing lcd-brightness...) doesn't and it works on windows on the same laptop (so it's not completely a laptop / hardware problem). (can someone back this up?)

So yeah, expect these things to be worked on, and hopefully fixed someday.

About the certification.. I also thought that this would help linux to run (and work flawlessly) :-( . I don't know if openSuse runs better.

---

