---
title: "Advice on Dual Win/ubuntu boot and NTFS"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by sadams on 2008-07-02
Hi all,

**NOTE - previously posted in H/W & Laptops 
[http://ubuntuforums.org/showthread.php?t=841341](http://ubuntuforums.org/showthread.php?t=841341)
but I got no replies :-(
Maybe this forum is more appropriate?
All comments welcomed.

====

I already think I know what I'm (going to be) doing on this however it will be interesting to get validation/feedback here.. and may be of interest to others.

1) Intro:
I'm sourcing a new laptop for my dad. He's in his 70s and a long term PC user.. having used Windows since 3.x way back - yet he is not very techy and uses his PC these days for mostly "civilian" purposes (email, web, some officey-stuff). he also has a Palm pilot that he syncs to desktop (mostly to "backup" rather than to utilise the data on the PC).
I also have and use my palm on ubuntu and know the options/requirements.

He is no fan of windows and is already picked up that Vista is a crock of bloatware and to be avoided.
He is open to being switched to Linux and i intend to get him set up on Hardy.

2) The Laptop:
I became converted to the way of the Thinkpad a few years ago and I am recommending an R61 model for dad.
I have done some initial digging/checking and it seems this is a decent choice for relatively sane and happy ubuntu'ing.

**Anyone with specific warnings and horror stories regarding ubuntu/hardy on a Thinkpad R61 please shout now!

I will buy one with WinXP but intend to leave it on but ignore it... leaving it as an option should dad reject ubuntu (as if!)
I will install, configure, tailor and deliver the system to dad and conduct "handover training"

*Note: the intention is not to regularly dual boot - Win XP is there only as insurance if it turns out dad doesn't like ubuntu.. or some hardware or s/w really necessitates it in the future (both unlikely).

3) Filesystems and dual booting.
So.. the thing will have a 160GB drive.
I intend to partition it as..:
*examples assume a disk labeled hda - even if you know better and that it would really be an sda please just play along and imagine it were called this!

hda1 - WinXP factory install resized down to say 20GB (or so)
hda2 - ubuntu hardy - say 20GB
hda3 - SWAP - 2GB (2 x RAM) - overkill but caters for upgrades in the future
hda4 - "Home/General" files - the "rest of the disk"
hda5 - Thinkpad "hidden" recovery partition (assuming there is one, usually at the end of the disk)

I am intending to make the Home partition as an NTFS system "just in case" the data needs to be accessible from windows.

This is on the assumption that:
i) Mounting an ext2/3 filesystem in WinXP requires extra software to manage and creates work and a techy on hand to do it.
ii) Despite reservations about NTFS (and the bad taste it creates on a lovely shiny ubuntu system) it will have no material difference on a "general purpose" laptop.
i.e.
- any fragmentation issues can be lived/dealt with when the time comes
- no material performance issues reading/writing to the drive

So... any comments/suggestions/improvements?

Regards,
Steve.

---

### Post by scragar on 2008-07-02
you will need to create an extended partition or 2 to balance out the partitions you want, a hard drive may only contain 3 partitions, ignoring the contents of extended partitions(in which you can place 3 other partitions, meaning with 1 extended and 2 normal partitions you can have up to 5 partitions, but it then becomes impossible to add a new partition without first loosing some information, be warned about that.)

and 2Gb of swap is excessive, I have 1GB of ram, and my swap is only 512MB(and even then 20% usage is the most it's ever seen), unless you intend to use hibernate anything more than 512 will be overkill.

---

### Post by Kevbert on 2008-07-02
Hi.  Sounds good.
You may want to double your size for the Ubuntu partition, don't forget all the extra programs you may want will be installed there.
If you have a dual boot PC you can set grub to give a short period say 2 seconds when you can dual boot and Ubuntu will be the default OS anyhow.
Regarding the L61 you may want to read up on wireless configurations.
Which Ubuntu flavour are you going to use ?  Kubuntu has a great graphical interface.  If you can wait for Intrepid Kubuntu that is even better.
Good luck.

---

### Post by Pumalite on 2008-07-02
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installation_instructions_for_the_ThinkPad_T61)

---

### Post by scragar on 2008-07-02
> **Kevbert said:**
> Hi.  Sounds good.
You may want to double your size for the Ubuntu partition, don't forget all the extra programs you may want will be installed there.
can I quckly point out that with a different /home partition 20GB is overkill, you need around 2 or 3GB for the system,so no matter how many programs you install it's unlikly to reach more than 5GB, I've got 2 partitions on my first HD, each one 20GB,and even without a different /home partition around 60% of each partition is empty

---

### Post by Pumalite on 2008-07-02
Hardy reads and writes to ntfs natively. To see Ubuntu from Windows; install this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sadams on 2008-07-05
Hi Again.
Thanks for the various comments and links to info etc.
Some responses from me.

I understand about the extended partitions - I guess I was suggesting "logical partioning" rather than "real". :-)

I agree that 20GB for / is "overkill" - may well round it down. These days of many many GBs drives allows me/us to be quite blase about "wasting" several GBs!

I also agree that "*2Gb of swap is excessive*" too - see the comment above.

Regarding the option to mount ext2 FS on Win platform - I am/was aware of this but as the system will be remote/distant from me I think it will be better to not use that - just in case in the future a non-linux type needs to do any repairs or something - or some kind of MS upgrade "helpfully disables" any "non-standard" or "insecure" software! (You know those MS upgrades/patches!).


Re: "*Which Ubuntu flavour are you going to use ? Kubuntu has a great graphical interface*"
Hmmmm - at risk of starting a flame war ;-)
I will use ubuntu - as it has the wonderfully simple and usable Gnome interface - as opposed to the rather cluttered and far too Redmond-a-like KDE interface ;-)


So - overall nobody has given me any reason to NOT use an NTFS partition as the main home directory (i.e. for all user files/data) or suggested it is a bad idea.

Thanks again for the interest and comments :-)

Steve.

---

