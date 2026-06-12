---
title: "cannot install ubuntu 10.04.1 i368"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by chene on 2010-09-25
greetings,

I'm trying to install ubuntu 10.04.1 i386 from CD to a blank WD 1TB drive.  The WD HD is totally new, there is no existing partition on it.  The purpose of this is to have a linux-only desktop.

I've downloaded 10.04.1 ISO and burnt it to both a blank CD and blank CDRW.  I've also loaded it to a USB drive.  ALL failed to boot:  I get the error message of:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(8,1)


After google a bit about the message, it appeared to be a GRUB/ACPI problem.  So I did the following (which didn't help)
when the purple screen just appeared, press ESC to bring up the ubuntu menu

press F6 to enable other options

I have tried:

acpi=off
noapic

but still end up with the same kernel panic error message.

my hardwares are:

Asus A8N-VM CSM
Nvidia 8600gt
WD 1T black
everything else is on-board

any idea of what I can do to install ubuntu?

any help is very much appreciated,

---

### Post by mrhhug on 2010-09-25
ok so basically your giving ubuntuforums a clean slate to start with? excellent, your descriptions were also excellent by the way.

im thinking you have a funky partition somehow (possibly refurbed drive)

lets get into a partition util and see what it brings up, do you have anything that will boot that has a partition util??? like fdisk?

you can download the UBCD here [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

### Post by coffee412 on 2010-09-25
Boot the cd again and when the menu comes up choose to run it from cd. Then when it finally loads open up a term window and post the output of :

> sudo fdisk /dev/sda

- choose option P I believe for "print partitions"


---

### Post by chene on 2010-09-25
from the time of my 1st post until now, I've tried to boot the computer with windows xp, which booted just fine.  I have then formatted the 1TB WD Black as one big partition during the XP's installation and restarted the ubuntu installation process.  Still, I ended up with the same error message.

I've also tried the ubuntu alternative installation CD, and still ended up with the same error message.

I'll see if I can boot into linux prompt and use dd to erase the 1st byte of the HD.

---

### Post by chene on 2010-09-25
unfortunately the live-session won't run.  I ended up with the same kernel panic error message.


> **coffee412 said:**
> Boot the cd again and when the menu comes up choose to run it from cd. Then when it finally loads open up a term window and post the output of :

---

### Post by chene on 2010-09-25
I've also tried to install ubuntu 10.04.1 onto an old 200GB PATA drive and ended up with the same error message.  So I think it is fair to say that it wasn't due to the weird partition on the HD (the 200GB had an valid NTFS partition) and it is on the 10.04.1 CD itself.

perhaps I'll try the 10.04 next.

---

### Post by mrhhug on 2010-09-25
> **chene said:**
> unfortunately the live-session won't run.  I ended up with the same kernel panic error message.

you need to delete the volume/partion on that disk , im not sure how it got there since you said it was a new drive.

you into windows? ok that'll work for now. right click on "my computer" hit manage - now find your 1tb drive and just right click on the partitions and delete everything (they are empty right its a new dirve) - with will delete anything on that drive so BE CAREFUL!!!!!!!!!!

i also think that you might have an error on you booting drive.. i thought u said this was a new drive and this was a linux only desktop?

> I'm trying to install ubuntu 10.04.1 i386 from CD to a blank WD 1TB drive. The WD HD is totally new, there is no existing partition on it. The purpose of this is to have a linux-only desktop.

whats goin on? disconect(physically) the old drive and try booting then from the live cd then, it'll prolly work.

---

### Post by chene on 2010-09-26
sorry I should have been more specific.

I have 2 HDs at my disposal, but only 1 is connected to the PC at any given time.  I've an old 200GB PATA drive with an old version of ubuntu 8.04 on it, the other is the WD 1TB black that I'm trying to install 10.04.1 onto.

with only the 1TB WD Black connected to the PC, I booted the computer with an XP CD.  The XP CD booted just fine when I went through the XP installation as far as the creating the HD partition.  I did this, as you suggested, that there might be an invalid partition on the 1TB.  Using the XP's installation process, I created a 1TB partition on the WD Black, terminated the XP's installation process, and restarted the ubuntu installation.  Still, I ended up with the same "Kernal Panic" error message.

With the 1TB WD Black connected still, and booted the machine with ubuntu 10.04.1, as soon as I see the purple screen I pressed ESC which brings up the ubuntu menu.  I choose the "run from CD", i.e. the live-session, instead of "install to HD".  Still, the live-session won't boot either: ended up with the same "kernel panic" message.

I then repeated the process but with the 200GB HD connected instead of the 1TB; but still end up with the same error.  That's why I think we can assume that there is something wrong with the ubuntu 10.04.1 i386 CD.

any help is very much appreciated,

---

### Post by coffee412 on 2010-09-26
Go into your bios and check the hard drive settings. Some bios have a setting to change the controller settings. I dont remember exactly but there is a setting for IDE or something like ACHE or similar. Make sure it says IDE. Then give it a try.

---

### Post by chene on 2010-09-30
an update:

looks like it was a hardware problem.  A faulty PSU caused instability in RAM which in terms caused the ubuntu installation process to be corrupted.  I've since replace the PSU and was able to install ubuntu successfully.

thanks to all who helped,

---

### Post by mrhhug on 2010-10-01
please mark as solved

---

### Post by chene on 2010-10-01
With all due respect, I marked the thread 10 seconds after my previous post; which in term, was 9 hours ahead your remark.


> **mrhhug said:**
> please mark as solved

---

