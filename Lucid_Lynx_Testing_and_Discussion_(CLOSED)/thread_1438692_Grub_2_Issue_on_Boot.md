---
title: "Grub 2 Issue on Boot"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Doctor Mike on 2010-03-25
There appears to be an issue about how the grub 2 bootloader is working. Not what I'd call a bug (program appears to be working the way it's intended), but what seems to be an oversight.

Bothe IDE: sda1 (XP) sdb1 (Ubuntu):

Did the update for the grub 2 today, but because of the way it had screwed up my windows installation the last time I decided to physically disconnect the sda drive just in case. Was not possible to complete the boot process. So I thought maybe the update will address that issue and I have image backups of everything, so what the hell.

Got a confirmation dialog box (could be more noob friendly) that allowed me to confirm exactly where I wanted to install grub 2... Very good. But, looking at the details provided by the confirmation dialog it seemed that unique hardware identification would only be used for the setup of the grub 2. If a hardware change occurred after, completing the boot process might be problematic.

So, after the update I confirmed that both OSs were working properly I then did a reboot with sda removed to see if there would be a dynamic response that would allow the boot process to complete. It did not. Got stuck on the Ubuntu screen with the dots running by forever.

I could think of several reasons why I might want to disconnect a drive (or I might have a drive failure) where I would like ready access to my Ubuntu install.

Can't really say if this is an issue of grub 2 not passing an argument to the OS or the OS being unable to adjust to a configuration change. However, I think it's grub 2.

---

### Post by dino99 on 2010-03-25
Hello Doctor,

my grub hurt me :roll:

as you dont tell all the story, its hard to know if you have grub-legacy (grub1) or not. When you have unplugged then plugged the other hdd, grub2 has not cow power to see it, you need to do an grub-mkconfig & upgrade-grub.

In case grub1 is still there, first remove/purge it before doing the commands above.

---

### Post by Doctor Mike on 2010-03-25
> **dino99 said:**
> Hello Doctor,

my grub hurt me :roll:

as you dont tell all the story, its hard to know if you have grub-legacy (grub1) or not. When you have unplugged then plugged the other hdd, grub2 has not cow power to see it, you need to do an grub-mkconfig & upgrade-grub.

In case grub1 is still there, first remove/purge it before doing the commands above.Sorry, grub 2 is installed only on update to a new version or new install at the moment. Before updating to the lucid beta1 I had plain old grub. Please see this link about what happened:

[http://ubuntuforums.org/showthread.php?t=1434121](http://ubuntuforums.org/showthread.php?t=1434121)

I don't wish to reconfigure the grub every time I make a drive switch and it's hard to do if you can't boot.

Did not uplug one drive and plugin another just unplug sda1. Was not a problem when running grub 1 on 9.10 karmic.

Grub 2 is only installed on Ubuntu drive (currently sdb).

In addition: I sometimes drop in another drive with another OS and some hard to find older utilities. IDEs don't always play nice together so I have to switch Ubuntu to master sda and additional drive to slave sdb. These kinds of things were possible before grub 2.

---

### Post by dino99 on 2010-03-25
now i'm thinking about:

how bios load your hdd, which one the first ?
how hdd are plugged on motherboard (master/slave)?
how fstab is built, with label or uuid ?
is mtab match fstab ?

if uuid are used, and now all might be configured with uuid, each time we plug/unplug a device then uuid change.

---

### Post by Doctor Mike on 2010-03-25
> **dino99 said:**
> now i'm thinking about:

how bios load your hdd, which one the first ?
how hdd are plugged on motherboard (master/slave)?
how fstab is built, with label or uuid ?
is mtab match fstab ?

if uuid are used, and now all might be configured with uuid, each time we plug/unplug a device then uuid change.
What I see as making sense in the future is unique hardware id associated with the specific OS installed on that hardware.

Doesn't seem to make sense to have either grub 2 or OS looking for files on sdb when only sda is installed. So grub 2 and or OS look for sdb because the association between hardware and software is only generic? I don't know, but this seems to be the case. If there were a direct relationship between grub 2 boot option, hardware, and OS copy we wouldn't need a confirmation dialog box when updating or installing grub 2 and any changes a user desired to do later on could be done from in the system. This is assuming that each software copy could be identified as unique.

---

