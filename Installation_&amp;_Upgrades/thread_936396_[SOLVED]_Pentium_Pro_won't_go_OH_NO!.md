---
title: "[SOLVED] Pentium Pro won't go OH NO!"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Braytok on 2008-10-02
pardon my lame attempt at clever title.

So heres my problem.
I want to use an old Pentium Pro 200Mhz system to build a DNS server. Problem is, I can not install any version of linux that I have tried. among those tried are: Ubuntu 6.x-8.04, Xubuntu, Fluxbuntu, DSL, Slackware, SLAX, and a few others that I don't recall. This system does not have ACPI so naturally I get the:
```
no DMI BIOS year acpi=force is required to enable acpi BIOS
```
I tried acpi=off but the system just hangs with blinking cursor.

Have any of you successfully install any linux variant on a similar system?

I previously had this system running Win2k and after that I had it running pfSense both with no problems.

I am not above using a FreeBSD distro if any one knows of one that can run on this hardware.

-Bray

---

### Post by upchucky on 2008-10-02
try puppy linux, "usb/floppy sized version" if it works then you have a bit of homework to do to build a bigger customized linux version tailored for that machine, i'm thinking that geentoo will work.

---

### Post by snowpine on 2008-10-02
Hi Braytok, perhaps this tread will help you out:

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

I was going to suggest DSL, but it sounds like you've already tried that. :(

---

### Post by Braytok on 2008-10-02
Haven't tried either of those yet. I'll do that and post results.

---

### Post by Braytok on 2008-10-02
arggg! 2 hours of banging my head and still no go. I tried Gentoo and puppy, both to no avail. I get the same error and if I try acpi=off at boot the system hangs. Looks like I may have to try different hardware :cry:

This is indeed sad, I love this system with its integrated SCSI and all but I guess thats the way the cookie crumbles.

---

### Post by tgalati4 on 2008-10-02
What errors do you get with DSL?  Sounds like you may need a custom kernel for the scsi support, or at least load the modules at boot time.

---

### Post by Partyboi2 on 2008-10-03
Is it possible to update your bios?

---

### Post by cariboo on 2008-10-03
I would give the Ubuntu mini.iso a try and just install to the cli. It is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and then install the dns packages you need. It will probably not be a good idea to install a gui as I've found that older video cards are no longer supported by Ubuntu. One big problem might be the amount of ram you have installed. I have an old p75 with 128mb ram, running DSL, it runs quite well, except when I try to add any packages, I can go out for coffee and when I come back it is usually done. :)

Jim

---

### Post by Braytok on 2008-10-03
> What errors do you get with DSL?  Sounds like you may need a custom kernel for the scsi support, or at least load the modules at boot time.

I saw no errors with DSL, just a black screen and a frozen system.

> Is it possible to update your bios?

this is a 1996 Amibios on a P6SNS motherboard. I've had no luck finding a BIOS update for it, but I haven't really looked at more then half a dozen places either. I figure with a unit this old I'll be hard pressed to find one.

> I would give the Ubuntu mini.iso a try and just install to the cli 

Same error :(

at any rate, I just switched to a K6 233 bare bone unit I had laying around that will work better any way. The PentiumPro system used old 72 pin SIMMS. I only had 196 MB available even though it will take up to 756 MB. The K6 system uses PC100 so I get a little boost there.

I would still love to get the the PentiumPro system running though and I like DSL. I'm not quite "proficient" with custom kernels though so any advise would be welcome.

---

### Post by Braytok on 2008-10-03
Ok, so I've made a little progress.

I went back and revisited cariboo907's suggestion of trying Ubuntu mini. I no longer have the acpi issue but now I have a new one.

The install hangs with "no SMP motherboard detected" Bare in mind that this is a single Pentium Pro processor. I tried passing:

```
boot: nosmp
```

But I get the same error. any ideas?

---

### Post by oni5115 on 2008-10-03
Hmm, not sure if this helps at all, but when I was looking into a similar issue I discovered somewhere that some of the kernels were bugged.  They would search for the first ACPI entry - even if it was an invallid entry - instead of actually finding the first vallid entry.  So it would cause it to display that error.

Unfortunately, I never bookmarked the place explaining it with the code to potentially fix the kernel.  I figured actually modifying the kernel and recompiling was beyond my level of experience.

Regardless, using a later kernel version perhaps it might find it - maybe try a debian distro with the latest kernel version and see if that helps.

Not sure what to do about the nosmp issue - haven't run into that one yet.


On a completely side note: ^5 for playing wow on Ubuntu - I do it too.  :D

---

### Post by cariboo on 2008-10-03
Did you download a 64bit version by mistake? If you download a 32bit version you shouldn't have a problem with no smp support.

Jim

---

### Post by Braytok on 2008-10-03
I went back and checked just now. The link on the list claims that Hardy 32bit is 9.5 MB and Hardy 64 bit is 9.6 MB. I checked the ISO i grabbed and its 9.6 MB so its possible. But, when I downloaded the 32 bit version again just to be sure it was in fact 9.6 MB so I'm not 100% sure that I didn't get the wrong one the first time. However... I just burned my last coaster so I must needs make a quick run to get more. BRB...](*,)

---

### Post by Braytok on 2008-10-04
I give up.

Conclusion: Linux won't run on a PentiumPro.

Sadly winNT,98, and 2K will.

---

### Post by Vivaldi Gloria on 2008-10-04
> **Braytok said:**
> I want to use an old Pentium Pro 200Mhz system

...

I tried acpi=off but the system just hangs with blinking cursor.


I remember seeing this problem but not sure where. Probably in a launchpad bug report. Search it.

Try also these: 

[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by Braytok on 2008-10-05
I've tried well over 20 different Linux distros and I always end up with one of two problems.

1: passing acpi=off or acpi=force causes the system to hang
or
2: "SMP motherboard not detected" and the system hangs.
trying 
```
nosmp
```
does nothing
```
maxcpus=1
```
also does nothing.

In the hours I have spent submersed in google I have yet to come across any one that has successfully got any 2.x kernel to run on a single CPU pentium pro system. I have seen reports of success on multi CPU Pentium Pro systems though. 

at any rate I just went with FreeBSD and it works like a charm. :P

---

### Post by Braytok on 2008-10-07
Solved!:popcorn:

And I feel a little silly /sheepish grin

What I did to fix:

Using Ubuntu Mini .iso [Found Here]("https://help.ubuntu.com/community/Installation/MinimalCD")
At the boot: prompt enter:
```
install no apic nolapic acpi=off maxcpus=0
```
After that the install went flawlessly.

My two biggest problems were (a)not reading the tips from the install cd, and (b)I was using "maxcpus=1" instead of "maxcpus=0". I'm not entirely sure why using "0" worked and "1" didn't but it worked and I'm quite pleased.

Thanks to all for all the great suggestions, and I hope others can get some uses out of this thread.

---

