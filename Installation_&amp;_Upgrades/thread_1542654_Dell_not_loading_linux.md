---
title: "Dell not loading linux"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by The Biking Viking on 2010-07-30
I'm really new to all this and not even sure if this is the right place to put this post so please bear with me.

I've never installed linux before -- done a fair amount of reading by now, though. I've burned a number of different versions of linux on my Sony Vaio with windows XP using infracorder and ImageBurn for a much older Dell. 

The Dell is a pentium III dimension 4100 with only 380 some MB of memory. Even though it has two CDrom drives and I have went into bios and changed the loading config to the adapti cdroms. I disabled the silent boot so I can make sure the memory is good. So it counts through that, does a little "thinking" (lights on the drives come on) with the two cdrom drives then it keeps asking to install a bootable floppy in A: drive. 

SoOo, I've been going through the bootloaders trying to maybe to make a floppy disk that would help enable booting the CDroms or even the version of Puppy Linux I put on a USB drive (the other computer will not natively boot from USB).

It's all become very frustrating. 

Goals: Short term to get any linux running on the other computer as a learning tool., to start. 

An aside: My main PC, this pentium 4 2.53ghz 768MB 120Ghz drive is getting 'old' as far as windows is concerned so I'm considering switching over and becoming a part of this community. I'm just sick of upgrading with bloatware! (plus spending more time trying to relearn a new piece(upgraded, constantly upgrading!) of sw than installing one version right, learning it, and being able to continue to spend time USING it for a long time which is what I understand linux is much better about.

Long term: I'm very interested in Kubuntu because I have a dual tuner card ATSC/NTSC (before the digital conversion) and bought the whole "fancy" windows logo package with IR blaster, Snapstream, Beyond TV, Nero ...and they called it obsolete and unsupported about a year after I bought it!

Thanks... I appreciate your time.
The Biking Viking

---

### Post by Sef on 2010-07-30
I would get some more ram, or try xubuntu which is made for computers with less ram.

As for your other computer, look at mythbuntu.

Run any CD as a Live CD to make sure that all works before installing.

---

### Post by The Biking Viking on 2010-08-02
> I would get some more ram, or try xubuntu which is made for computers with less ram.

 
Right, I plan to once I determine the old pentium III dimesion 4100 works. Right now it has two optical drives and not even a HD. I just wanted to put something like puppy linux in there and see it basically functional. Make sure it works. Then play around with linux for a bit.
 
Then I'll make an order for RAM, HD, a better graphics card and whatnot. Until I know it thoroughly works there is no sense putting a dime into it.
 
At the moment I just need help with the part where the computer is stuck at 
 
**Insert a bootable floppy disk in drive A:**
 
**???**
 
**Thanks**
-- TBV

---

### Post by lechien73 on 2010-08-02
Since the laptop may not support booting from ISOLINUX, you could try creating a boot floppy containing the smart boot manager file from the Ubuntu install CD.

Locate the sbm.bin file in the Install directory of your Ubuntu CD. If you can boot the Live CD, then drop to a terminal, change to the install directory and type:

```
dd if=sbm.bin of=/dev/fd0
```

Or, if you're using Windows, then you could use [RawWrite]("http://www.chrysocome.net/rawwrite") to create the floppy.

When you boot with this floppy, you should get a menu with an option to start Linux from the CD.

---

### Post by The Biking Viking on 2010-08-04
> Since the laptop may not support booting from ISOLINUX, you could try creating a boot floppy containing the smart boot manager file from the Ubuntu install CD.
 
It doesn't have enough memory for Ubuntu right now and with no HD it's got no place to store it either. Two optical drives only. Is that the same proceedure with puppy? 
 
It's not a laptop. I'm not sure why it wouldn't boot from the two CDroms. I set the BIOS. But I'm unfamilair with iso formats. When you insert one and click on its properties, under windows, what should it say?

---

### Post by cascade9 on 2010-08-04
> **The Biking Viking said:**
> Right, I plan to once I determine the old pentium III dimesion 4100 works. Right now it has two optical drives and not even a HD. I just wanted to put something like puppy linux in there and see it basically functional. Make sure it works. Then play around with linux for a bit.
 
Then I'll make an order for RAM, HD, a better graphics card and whatnot. Until I know it thoroughly works there is no sense putting a dime into it.
 

Just so you know, that computer is limited to 512MB of RAM, and AGP/PCI video cards. Also, its only got a 200watt power supply, which can limit your video card choice (not that you will find that many power hungry AGP cards anymore). 

[http://support.dell.com/support/edocs/systems/dzuul/specs.htm](http://support.dell.com/support/edocs/systems/dzuul/specs.htm)

I have no idea on why it is asking for a bootable floppy, I've had no issues with booting on the 4100s I've used. That was using older linux distros though.

---

