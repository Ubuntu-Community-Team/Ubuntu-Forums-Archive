---
title: "server install on MD/RAID1 supported?"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2007-11-08
Hi,

I want to move from Fedora to Ubuntu server. I want my system disk to be RAID1 using MD, just as I have another system for Fedora.

I see [this]("https://help.ubuntu.com/community/Installation/RAID1"), which suggests it isn't supported. Is this still the case? If so, I don't see much point in moving to Ubuntu from Fedora.

I see other posts where people have been installing onto MD RAID1, so I am guessing it actually works, so I'm curious why it isn't supported, especially for the server.

Perhaps the doc only refers to the desktop version...

Max.

---

### Post by Uwe82 on 2008-02-14
Just saw your post: I want to install UBuntu server (for VMWare usage) on my nvidia board with MCP51 SATA RAID controller. I also want to use a RAID1 to install the base system and needed files on it. Is it really not supported by UBuntu (Server?). Is there a way that I can just create a RAID1 in the RAID BIOS and install UBuntu on the RAID device?

---

### Post by davidmaxwaterman on 2008-02-14
> **Uwe82 said:**
> Just saw your post: I want to install UBuntu server (for VMWare usage) on my nvidia board with MCP51 SATA RAID controller. I also want to use a RAID1 to install the base system and needed files on it. Is it really not supported by UBuntu (Server?). Is there a way that I can just create a RAID1 in the RAID BIOS and install UBuntu on the RAID device?

My post refers to using MD RAID1 which is purely software implementation.

Using on board controllers is a different issue. I would guess it would work for you just fine, but some controllers need support from drivers so it's best to check.

In any case, for the record, my MD RAID1 install has been working just fine for quite a while now. I installed onto a pair of 2.5" laptop drives (the case only fits a single 3.5" drive), each driven from each of the motherboard's eide channels.

I never did find out if RAID1 was supported on the system disk, and if not why not. For a server OS it's an amazing thing not to support. I know some Linux OSes that insist you use RAID1 on the system disk, even if you only have a single disk (it runs with the second disk failed).

Max.

---

### Post by Uwe82 on 2008-02-14
You are right, I forgot that MD is software emulation. I hardly did anything with RAID in Linux yet, only in Windows. The linux on this server will just be the base for an VMWare server to have several guest OS running on one machine ;)

I will try then this evening, if it really works, Ubuntu 7.10 AMD64 is already on my harddisk and ready to e banned on CD ;)

Thanks for the quick reply.

//EDIT: There seems to be support for this chip in sata_nv module. It's a long time ago, that I did an Ubuntu install, is this module automatically loaded or do I have to load it manually in installation?

---

### Post by davidmaxwaterman on 2008-02-14
> **Uwe82 said:**
> You are right, I forgot that MD is software emulation. I hardly did anything with RAID in Linux yet, only in Windows. The linux on this server will just be the base for an VMWare server to have several guest OS running on one machine ;)

I will try then this evening, if it really works, Ubuntu 7.10 AMD64 is already on my harddisk and ready to e banned on CD ;)

Thanks for the quick reply.

//EDIT: There seems to be support for this chip in sata_nv module. It's a long time ago, that I did an Ubuntu install, is this module automatically loaded or do I have to load it manually in installation?

I think it might be there already. Best to just try.

I must say, I don't recommend those half-baked RAID solutions at all. I would recommend MD over it any day of the week. For example, if your mobo fails, you need to find a compatible one to replace it. When my mobo failed recently, I could choose any mobo I wanted, and I knew my RAID5 array would work just fine.

Upto you, of course.

Max.

---

### Post by Uwe82 on 2008-02-14
> **davidmaxwaterman said:**
> I think it might be there already. Best to just try.

I must say, I don't recommend those half-baked RAID solutions at all. I would recommend MD over it any day of the week. For example, if your mobo fails, you need to find a compatible one to replace it. When my mobo failed recently, I could choose any mobo I wanted, and I knew my RAID5 array would work just fine.

Upto you, of course.

Max.
I prefer the hardware based version. With a RAID5 its another topic, but a RAID1 is no problem there, because I can just use one of the drivers, if I need to ;) So this one is better with a hardware-based solution, I think.

---

### Post by davidmaxwaterman on 2008-02-14
> **Uwe82 said:**
> I prefer the hardware based version. With a RAID5 its another topic, but a RAID1 is no problem there, because I can just use one of the drivers, if I need to ;) So this one is better with a hardware-based solution, I think.

IINM, the driver on it's own is no good. You need the h/w too, hence my point...

---

