---
title: "RAID Install"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by surj08 on 2008-10-28
Im getting ready to boot windows off my computer for good :)

I have a hardware helped RAID (i set it up in the bios) windows during the install requires an extra driver, will i have to do the same for ubnutu?

Its 2 sata 250 seagate drives the mobo is an abit kn9 with 4 sata ports the harddrives will be put in sata1 and 2

---

### Post by lemming465 on 2008-10-30
> **surj08 said:**
> I have a hardware helped RAID ... windows ... requires an extra driver

If windows requires an extra driver, you have *fakeraid*, not real hardware RAID.  There may or may not be a corresponding Linux driver.  Check your motherboard documentation; if there is one, it should mention it.  

If not, which is most likely, you'll have to turn off the BIOS RAID and go back to using the two disks independently. Do not despair!  If you need either RAID-0 striping or RAID-1 mirroring, you can use one of the alternate install CD's to get that directly from the Ubuntu Linux kernel using *mdadm* to administer it.  I do it all the time on systems which either lack hardware RAID, or where I want RAID 1/0 striped mirrors and the hardware can't get that far.

---

### Post by Hero_boy on 2008-10-31
I thought I'd post this question here rather then start a new thread.

I have noticed that a few places have advertised FakeRAID support in Ubuntu 8.10, such as here:

[http://willysr.blogspot.com/2008/10/ubuntu-810-released.html](http://willysr.blogspot.com/2008/10/ubuntu-810-released.html)
[http://ubuntuforums.org/showthread.php?t=936732http://www.theregister.co.uk/2008/10/27/ubuntu_intrepid_ibex/page2.html](http://ubuntuforums.org/showthread.php?t=936732http://www.theregister.co.uk/2008/10/27/ubuntu_intrepid_ibex/page2.html)

FakeRAID vs Software RAID aside, has anyone tried this feature out? What RAID controller chips is it compatible with? 64bit & 32bit flavours?

I have a GA-MA78GM-S2H motherboard I was hoping to use this with.

---

### Post by lemming465 on 2008-10-31
My personal inclination is to stay away from the fakeraid, as most of my systems are multiboot and I often try beta versions of different distributions.  The odds that all the windows and Linux and *BSD variants I'm playing with will understand fakeraid the same way and have drivers are basically zero.  So I stick to software RAID - which both Windows and Linux can do - unless I have an actual full-on hardware controller from Adaptec or LSI or someone mainstream and widely supported.  There is little or no speed advantage to the fakeraid, so I'm not losing anything important.

---

### Post by Hero_boy on 2008-10-31
As mentioned:

> **Hero_boy said:**
> 

FakeRAID vs Software RAID aside...

I was just wondering if it was possible. I really didn't want to start another FakeRAID vs Software RAID thread.

---

### Post by psusi on 2008-10-31
> **lemming465 said:**
> If windows requires an extra driver, you have *fakeraid*, not real hardware RAID.  There may or may not be a corresponding Linux driver.  Check your motherboard documentation; if there is one, it should mention it.  


No, real hardware raids also require a driver.  Most likely though, the OP has a fakeraid and can get it working in Ubuntu.  I had a few issues installing Intrepid using the livecd but the alternate install cd is supposed to work fine with it.

> **lemming465 said:**
> My personal inclination is to stay away from the fakeraid, as most of my systems are multiboot and I often try beta versions of different distributions.  The odds that all the windows and Linux and *BSD variants I'm playing with will understand fakeraid the same way and have drivers are basically zero.  So I stick to software RAID - which both Windows and Linux can do - unless I have an actual full-on hardware controller from Adaptec or LSI or someone mainstream and widely supported.  There is little or no speed advantage to the fakeraid, so I'm not losing anything important.

The reason for the fakeraid is to allow booting from a raid0 or raid5, which you can't do with software raid, and to dual boot Windows.  Also Windows requires dynamic disks to do software raid these days, which I don't think Linux can understand, so you won't be able to use the same disks, or access data on one from the other.

---

