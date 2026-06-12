---
title: "GRUB doesn't see Windows 7 after installing Ubuntu 12.04"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by gonzalobb on 2013-03-06
So, this is my first time installing Ubuntu on my hard drive, and I'm running into some problems.

Until a couple of hours ago, I had 4 partitions in my hard drive: XP, Vista and 7 installations, plus a data partition. I backep up the XP and Vista partitions which weren't of any use lately, and booted a live-usb with Ubuntu 12.04.

On the "Install 12.04 LTS" partition manager thingy I deleted the XP and Vista partitions (which where sda1 and sda2 on the partition table), leaving around 260gb of free space. There, I made 3 partitions: 8gb for root, 4gb for swap, and 80gb for home.

I then proceeded to install Ubuntu, hoping to be able to move back and forth between 7 and Ubuntu, but GRUB doesn't seem to recognize my windows installation. I read some forums, and tried two things, neither of which actually worked:

 1. I added a # to GRUB_HIDDEN_TIMEOUT=0 in /etc/default/grub to at least be able to see the GRUB screen when booting, and effectively, Windows 7 wasn't there.
 2. I ran boot-repair from my live-usb, but it didn't solve the problem either. Anyway, I got the boot info at least, which I'm linking right away: [http://paste.ubuntu.com/5589763/](http://paste.ubuntu.com/5589763/)

So, this is my family computer, and I'm probably getting killed in the morning if I don't sort this out. Any advice is truly, truly appreciated. Thanks in advance!

---

### Post by Mark Phelps on 2013-03-06
When you install either Vista or Win7, when another older Windows version is already on the drive, the default is for the installer to add the new boot loader files to the OLDER Windows partition -- which, if you upgraded to Vista from XP, it added the boot files to the XP partition.

When you removed that partition, you removed the Win7 boot loader files.

I dual-boot a lot and made sure I created a Win7 Repair CD -- so I could use that to fix these problems.  With that, I don't need to run boot-repair, so I can't tell you why that didn't work.  Someone more experienced in using that will have to help.

Since you didn't create the Win7 Repair CD when you had a chance, one option is to create one now -- but you will have to pay for it.  IF you're willing to spend some money, go to the link below, download the ISO image you need, burn it to a CD, boot from that CD, and run Startup Repair three times, that's right, three times -- as it often takes all three passes to make the repairs:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

