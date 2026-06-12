---
title: "Two like distros multi boot"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by Klarsin on 2007-03-12
I have dapper on hda1 and edgy on hda5 and Mepis on hda2. I heard somewhere that you should'nt have the same distro on the same computer. (or L Mint).... Is this true? Or am I OK with my setup on different drives. Or does this have anything to do with using VMware?

---

### Post by dannyboy79 on 2007-03-12
this may have something to do with vmware or other virualization software but you can have as many os's on the same or different hard drives as you want. check out this link where a guy has a grub floppy booting over 100+ os's which is split between 4 different hard drives and 144 parititons. you're fine!

[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

I must also point out that windows does have a problem when booting from different os's from the same drive, you need to use the "hide" option in your menu.lst for it to work. see here: [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by gh0st on 2007-03-12
> **Klarsin said:**
> I have dapper on hda1 and edgy on hda5 and Mepis on hda2. I heard somewhere that you should'nt have the same distro on the same computer. (or L Mint).... Is this true? Or am I OK with my setup on different drives. Or does this have anything to do with using VMware?

I'm not an expert but I don't see the problem with having a multi boot system with different versions of the same distro. I've run multi-boot systems with 2 or 3 copies of XP and it never caused a problem, I don't see why Linux would any different.

Like I say I'm no expert but I think you should be fine as long as you don't get confused looking at the same names in the GRUB menu :)

---

### Post by gh0st on 2007-03-12
> **dannyboy79 said:**
> this may have something to do with vmware or other virualization software but you can have as many os's on the same or different hard drives as you want. check out this link where a guy has a grub floppy booting over 100+ os's which is split between 4 different hard drives and 144 parititons. you're fine!

[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

Wow 144 partitions???!!! I thought I was doing well with 9 :) 

Looks like you're pretty safe.

---

### Post by Klarsin on 2007-03-12
> **dannyboy79 said:**
> this may have something to do with vmware or other virualization software but you can have as many os's on the same or different hard drives as you want. check out this link where a guy has a grub floppy booting over 100+ os's which is split between 4 different hard drives and 144 parititons. you're fine!

[http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

In don't hav vmware, and this is a winless computer so I'm strickly linux here.

Jez, This is awsome stuff! The explanations for the 144 multi boot look pretty detailed, for all I know. I'm still trying to learn how to make my hda1 default boot. I'm in the process of learning more about grub, so the above link is a bit of a help.

I intended to use Ubuntu on two different partitions using hda5 only as a backup in case of a problem with hda1. In otherwords I would save my home folder from Ub hda1 to Ub hda5 now and then.I guess my only concern now is to watch out for my upgrades. I think I'm just about ready to upgrade to edgy so they both will be edgy.

---

### Post by louieb on 2007-03-13
I don't know how you have your GRUB boot loader setup. But you might want to take a look at what Herman has to say about dual booting Linux distributions by  chain loading  or using a configuration  file entry. I've used both and they work very well. [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

---

### Post by Klarsin on 2007-03-13
> **louieb said:**
> I don't know how you have your GRUB boot loader setup. But you might want to take a look at what Herman has to say about dual booting Linux distributions by  chain loading  or using a configuration  file entry. I've used both and they work very well. [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

This Grub page is great! I now know how to set up a default boot - very simple and  easy to understand explanations. I don't know if I'll need chainloading but who knows, if I stick with Linux long enough I might just be into that. Nothing like 100 or so distros, though.

---

