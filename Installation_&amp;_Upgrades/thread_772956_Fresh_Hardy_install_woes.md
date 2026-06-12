---
title: "Fresh Hardy install woes"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by 453 on 2008-04-28
I've toyed with Live CDs and USB before but decided I'd take the plunge with a full HDD install of Hardy, but I'm having just a few problems.  I'm trying to dual boot it with an already-there XP install.  Please bear in mind that I'm pretty much a linux newbie.

- The 8.04 ISO gives me an annoying BusyBox message when I try to either run it live or install it:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu12) Built-in Shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)_
```

This happens just after it loads the Kernel, and it sits there.  And just sits there.

- The 8.04 alt ISO does the same.  Both checked with MD5SUM, both fine.

- Tried installing Heron to a USB to install it from there, wouldn't work (wouldn't boot from the drive, went straight to XP.  I've used this drive to boot other distros, so I must be doing something wrong or Hardy doesn't like Flash Voyager GTs).

- I've got an old 7.10 Live CD and, oddly, it worked a few days ago but since trying to install Hardy it doesn't:  it hangs after loading the kernel with a black screen and my DVD drive makes chugging noises.  

I've a nice 10GB partition on my new 500GB hard drive just waiting for Hardy.  If you've any tips on how to get it there I'd be very appreciative.

---

### Post by Pumalite on 2008-04-28
Post your specs.

---

### Post by 453 on 2008-04-28
CPU:  AMD X2 5600+ (2.8Ghz)
GPU:  Sapphire 2600XT (256MB GDDR4 model)
Mobo:  MSI K9A Platinum
RAM:  2 Gig, DDR2 800

Can't quite remember the exact model of optical drive:  a NEC Optiarch of some sort.  Always figured they were pretty generic anyway, before this started.

No overclocking or other fiddling.

---

### Post by Pumalite on 2008-04-28
Graphics?

---

### Post by 453 on 2008-04-28
Like I said:

> **453 said:**
> 
GPU:  Sapphire 2600XT (256MB GDDR4 model)


Or are you looking for something else?

---

### Post by Invader Amoto on 2008-04-28
I've had this problem before and it turned out to be the cd drive. The kernel loads and the comp can read the cd but the kernel cant mount it. Does the cd drive work properly in windows? Because that's how i figured out something was wrong with the cd drive. I had to replace the cd drive.

---

### Post by 453 on 2008-04-28
> **Invader Amoto said:**
> I've had this problem before and it turned out to be the cd drive. The kernel loads and the comp can read the cd but the kernel cant mount it. Does the cd drive work properly in windows? Because that's how i figured out something was wrong with the cd drive. I had to replace the cd drive.

That crossed my mind, but it seems to work perfectly in XP.  I've loaded a DVD with no hiccups and there's nothing to suggest it ain't fine.  And I've no other optical drive to try it with.  What really confuses my is my machine's sudden refusal to load the Ubuntu 7.10 disk.  

Maybe I should have installed that when it was working and just upgraded, instead of waiting to do a full Hardy install...  :roll:

---

### Post by Pumalite on 2008-04-28
> **453 said:**
> Like I said:



Or are you looking for something else?

Sorry, my mistake. There are two things you can do. Some people are having success going into ther BIOS and changing AHCI or IDE to RAID. The other is the Alternate CD or Boot parameters:
noapic nolapic acpi=off, etc

---

### Post by 453 on 2008-04-28
> **Pumalite said:**
> Sorry, my mistake. There are two things you can do. Some people are having success going into ther BIOS and changing AHCI or IDE to RAID. The other is the Alternate CD or Boot parameters:
noapic nolapic acpi=off, etc

Thanks, I'll give the boot parameters a go.  When you say "noapic nolapic acpi=off, etc" where can I find the rest after "etc"?

---

### Post by Pumalite on 2008-04-28
Here:

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

---

### Post by 453 on 2008-04-28
> **Pumalite said:**
> Sorry, my mistake. There are two things you can do. Some people are having success going into ther BIOS and changing AHCI or IDE to RAID. The other is the Alternate CD or Boot parameters:
noapic nolapic acpi=off, etc

Thanks for the suggestions, but I've tried both and they're non starters.  

noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

Gets me just past loading the kernel: something flashes up (first word is "loading", the rest might be "please wait") and then I hit a black screen with a static underscore.  

My system didn't like switching native IDE to RAID either.  It skipped the Heron CD altogether, tried booting XP and restarted itself every time the loading bar appeared.

If I get time I might try installing an even older Ubuntu disk and then upgrade it to 8.04.

---

### Post by Pumalite on 2008-04-28
Just one note: the boot parameters are to be used alone or in different combinations. As for BIOS; XP does not like the change to Raid, but you can install and later revert it.

---

### Post by 453 on 2008-04-28
noapic et al. on their own lead to a plain black screen after loading the kernel.  Pressing keys makes my Numlock LED light up.  Hmm.

I guessed at being able to revert the RAID setting, but that seems to make the boot sequence totally skip my Hardy CD, so I can't even install it and then change my settings after.

---

### Post by Solrac924 on 2008-04-28
i'm having the same issue & i've tried freaking everything! (see [http://ubuntuforums.org/showthread.php?p=4828514]("http://ubuntuforums.org/showthread.php?p=4828514"))
this is really aggravating! i don't see any setting to switch to RAID in the BIOS. i'm thinking of installing Gutsy also but my freakin' CD didn't burn right. :(

---

### Post by 453 on 2008-05-01
Right, I've (maybe?) made a minor amount of progress.

If I boot it using the parameter floppy=off it doesn't freeze at BusyBox anymore, instead it gives me this error:

```
 [38.862540] Kernel panic: not synching : VFS : unable to mount root fs on unknown
-block (104,1)
```

I've seen a few other threads that have dealt with this but they've all been with an install already there, whereas I haven't managed to get Heron installed yet.

Anyone know how to get around this?

---

### Post by Solrac924 on 2008-05-06
little update:
after 3 unsuccessful tries of Hardy, i re-burned Gutsy at a slow speed & installed it successfully. It boots properly every time. i've downloaded all updates includnig the latest kernal. So now i've got Hardy finally. thing is, i have to boot using 22-14 cause 24-16 locks up half the time.

the thing i'm working on now is one of the CPU's being on 100% all the time. :?

---

