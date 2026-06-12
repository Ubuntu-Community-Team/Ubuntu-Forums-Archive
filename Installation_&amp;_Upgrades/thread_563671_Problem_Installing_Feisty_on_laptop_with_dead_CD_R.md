---
title: "Problem Installing Feisty on laptop with dead CD ROM and can't boot to USB"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by roguetrooper on 2007-09-30
Hi,
I'm trying to install Ubuntu on an old laptop (Acer Extensa 710TE) but the CD ROM drive is dead.
The BIOS won't allow boot from USB
The machine has no built in networking. Only a Linksys PCMCIA card.
At present the machine will boot to Win XP, on the HDD, from where I can use the network card and read USB devices.
I don't want to keep XP, apart from not liking it, the HDD is only about 4GB in size.
It also has a working floppy drive, but it's the only working floppy drive I've got so anything that needs to written to floppy has to be done using XP while that still works.

So far I've tried the SMB disk option, but it still can't see the USB device.
I tried a GRUB boot disk but agin it would only allow for root to be the HDD and the FDD.

Then, from links on the forum, I found this page for installing from Windows using a netboot approach <http://marc.herbert.free.fr/linux/win2linstall.html> and I think I follwed the instructions correctly.
I can now launch GRUB when booting from the HDD and it will load the kernel and presumably ramdisk because it starts the install procedure. However it then can't see the network card (PCMCIA WIFI thing) which I thought it might not.
Is there a way of modifying this approach to use the kernal loaded to detect and use the USB device (a 2GB SD card) onto which I've copied the contents of the alternate install CD. I think there might be but I only followed the instructions. I didn't really understand them. Certainly not deeply enough to be confident in modifying them.

Secondly, assuming I can get Ubuntu installed, willI be able to use the Linksys PCMIA WIFI card with it ?, or any other PCMCIA WIFI card for that matter,  if not, I might as well not bother.

Thanks for any help you can offer.

Roddy

---

### Post by logos34 on 2007-09-30
> **roguetrooper said:**
> So far I've tried the SMB disk option, but it still can't see the USB device.

right, because SMB still lacks USB support (you would think they would have added that by now)

> Is there a way of modifying this approach to use the kernal loaded to detect and use the USB device (a 2GB SD card) onto which I've copied the contents of the alternate install CD. 

If there is I'm unaware of it.
> 
assuming I can get Ubuntu installed, willI be able to use the Linksys PCMIA WIFI card with it ?, or any other PCMCIA WIFI card for that matter, if not, I might as well not bother.

Since your wifi card seems to be the sticking point here, I think your only option is to try [Wubi]("http://wubi.sourceforge.net/faq.php#development").  If wireless works then you can convert Ubuntu to a permanent installation on a dedicated partition using[ LVM]("http://lubi.sourceforge.net/lvpm.html").

With such a small HDD (4 gig) go with Xubuntu.  It's a lot smaller and lighter

---

### Post by roguetrooper on 2007-09-30
> **logos34 said:**
> 
Since your wifi card seems to be the sticking point here, I think your only option is to try [Wubi]("http://wubi.sourceforge.net/faq.php#development").  If wireless works then you can convert Ubuntu to a permanent installation on a dedicated partition using[ LVM]("http://lubi.sourceforge.net/lvpm.html").

With such a small HDD (4 gig) go with Xubuntu.  It's a lot smaller and lighter

Alas, the first thing Wubi did was check to see how much spare disk there was then quit saying that 4GB was the minimum.
With only a 4GB HDD, there's only 1.45GB left after XP has taken up residence. I ran XP's disk cleaning tools and it didn't identify much that it didn't regard as optional or an "installed application" that I could delete. (I managed to go from 1.2GB free to 1.45GB). I'm not aware of anything else that can be removed, although this is a 2nd user laptop, maybe there's some files I haven't spotted. Does anyone know if 2.5GB for an XP install is about average.

Roddy

---

### Post by ljonesj on 2007-09-30
yeah that sounds about right after all devices are installed

---

### Post by rodica.balasa on 2008-01-18
here is how i installed on an old computer, using a floppy and netboot:

[http://www.len.ro/work/tools/life-to...d-i8000-1/view]("http://www.len.ro/work/tools/life-to...d-i8000-1/view")

---

### Post by roguetrooper on 2008-01-18
Alas your link get's truncated. I did manage to find it by deleteing back to the word tools and then selecting likely looking links from that page.
I take it it was alink to the "Old/new 18000" pages.

There are some difficulties I need to overcome.
I don't understand what you're doing in the first few steps, I also suspect you're not doing them on the laptop. The laptop I've got is currently only running windows not Linux of any flavour.
The laptop I've got has no ethernet port/card. Only a pcmcia wifi card.
I may have damaged the connection to the laptop's screen trying to getthe HDD out as someone suggested mounting the HDD on another machine to put the install images on it that way.

I'm afraid I'm pretty much going to give up on this project and take the laptop to landfill.

Thanks though.

Roddy

---

