---
title: "Some Help would be much appreciated"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by clemcat on 2006-03-01
Hey all,

Like I have said in previous posts, this community rocks, and I know it will do it again with this question.

I have Breezy installed and running great on my laptop (an old P3 1.0 GhZ) that was donated to me, and I am trying to get in installed on my Home system. 

Unfortunately because of work (I must say I wish that the education system in America depended on something a bit better than MS) I must do a dual boot.

I know form my experiences with SuSe and RedHat I must have LBA Access enabled.  Here are my system specs, and if anyone can point mer in the right direction to get LBA enabled on my drives, I would greatly appreciate it.

System:
AMD 64 3000+ (Venice Core, no OC[-( , I have learned my lesson!)
1 GB Corsair ValueSelect DDR 400 RAM in Dual Channel Config
MSI K8N Neo 2 Platinum with the Award BIOS (1.9 loaded last night)
2 Seagate Barracuda 7200.8 SATA Drive (No RAID until I get a controller card,
                          yet another lesson, software RAID= BAD:twisted: )
Chaintech 6600 GT with 256 Mb on Board RAM

Like I said, I know I must get LBA enabled, but when I go into my BIOS, all I see for options under my SATA drives is [LARGE] or [AUTO].  Is there a different BIOS I could change to that would support LBA oon these drives, or does the problem lie in the fact that they are SATA (I am still a noob to SATA, my "boss" finally okayed the upgrade from IDE a little while ago, and oh yeah, for you guys who are'nt married, "boss" = wife).

Any advice that anyone can toss my way would be greatly appreciated.

Thanks,
Chris

---

### Post by clemcat on 2006-03-02
Bump, but trust me I am eagerly checking if there have been any replies that may help me as I am kind of stuck in a holding pattern right now.

I think the problem lies in the BIOS as I would venture to say that the new SATA drives would support LBA.  So, does anyone have an MSI K8N Neo2 that they have dual booting, and if so, what version of the BIOS are they using?

Thanks guys,

Chris

---

### Post by jibril on 2006-03-02
i honestly dont know what an LBA is ., I only now(12:22am 3/3/2006) got ubuntu to dual boot with ******** XP ... 

Sorry man

jibril

---

### Post by clemcat on 2006-03-02
Well,

I threw caution into the wind and tried it, I kept getting an "error loading operating system" after the Ubuntu install, so I thought I might as well start the Windows XP re-install (a low level format the night before made it so I really didn't care too much about doing this), and I missed pressing my any button when I was prompted to  "press any button to boot from cd", and when I looked up I saw the Ubuntu login screen\\:D/ .  

Quite odd I thought :-k , so I ejected the CD and shutdown Ubuntu so I could make sure it worked, and again I got the "error loading operating system" message, I did a quick ctrl+alt+del after I put the CD back in, and it loaded to GRUB.  

I am thinking that I am looking at a GRUB problem, I will investigate it more, but still advice and direction would be greatly appreciated.

BTW, LBA is "Large Block Access", sometimes computers that dual boot want this enabled (I don't know if this is a universal truth, but I have always had to do it in the past), and it is usually a motherboard setting.  My laptop needs to have LBA enabled in the BIOS or I get the "error loading operating system" message.

Any help would still be awesome.

Thanks guys and gals,

Chris

---

### Post by wrtrdood on 2006-03-02
Hmmm... it does sound like a BIOS issue.  Typically most recent systems default to LBA so I'd be surprised if that was it.  The LARGE designator is actually the LBA support you're looking for (...so why can't it just say that?... :P )

There may be some compatibility issues here.  Chase down the Large Disk HOWTO.  It may give you some things to check.

(nice avatar, BTW)

---

### Post by Bartender on 2006-03-02
Try setting to AUTO in BIOS.  Any half-modern BIOS (last six years at least) should recognize HDD parameters when in Auto w/out that horrible drill of manually setting up sectors, etc.

---

### Post by clemcat on 2006-03-02
I tried auto and large settings in the BIOS, and no luck, I will track down the Large Disk How to section, good advice (must be because he's a Broncos fan).
\\:D/

---

