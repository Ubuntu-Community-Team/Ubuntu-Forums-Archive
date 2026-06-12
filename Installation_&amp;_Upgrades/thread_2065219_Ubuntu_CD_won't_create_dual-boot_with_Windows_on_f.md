---
title: "Ubuntu CD won't create dual-boot with Windows on first drive and Ubuntu on second dri"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by mantisdolphin on 2012-10-01
When I installed Ubuntu onto my second harddrive, that had Crunchbang on it, I overwrote Crunchbang and could no longer boot my machine.

So, Boot Repair Disk to the rescue...AND I got Windows back up and booting, but without a dual-boot. 

How do I get Ubuntu back into the boot-up list?  
Do I wipe the Ubuntu drive and start over?  Part of the problem is that Grub is setup to boot from that second drive when it's plugged in.

Here's my boot info summary:

=> Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks 
for (,msdos1)/grub on this drive.
=> No boot loader is installed in the MBR of /dev/sdg.

[Full summary here: [http://paste.ubuntu.com/1252850/]](http://paste.ubuntu.com/1252850/])

---

### Post by darkod on 2012-10-01
The ubuntu installer would have installed the grub2 bootloader. You just need to boot from the correct disk.

Did you try booting from sdb, not from sda?

---

### Post by mantisdolphin on 2012-10-01
I tried to boot from sdb, creating a boot partition there.  But I ended up with grub looking on sdb and not sda. 

Should I edit the grub2 config?

---

### Post by darkod on 2012-10-01
What do you mean by "grub looking on sdb"?

Grub2 is installed on the MBR of /dev/sdb, so you have to set BIOS to boot from sdb as first option.

The grub2 os-prober searches all disks for other OSs and creates the appropriate entries in the boot menu, regardless on which disk it is. So it doesn't really matter. Just so you know from which disk to boot.

Do you actually have a problem booting any OS or you are just confused that grub2 is on sdb?

---

### Post by mantisdolphin on 2012-10-01
"Do you actually have a problem booting any OS or you are just confused that grub2 is on sdb?"

I'm pretty sure I'm confused about something, and it may be the BIOS pointing to the right drive.  My understanding is that Grub writes to the MBR of the first disk (Win7 in my case) with a redirect to the Grub config file on the second disk (Ubuntu), which then posts the boot menu with available OS options.  Is that incorrect?  

From what I can make out of the boot summary from the Boot Repair CD (posted in my first post for this thread), Grub is on sdb and points back to sdb: "looks at sector 1 of 
the same hard drive for core.img. core.img is at this location and looks for (,msdos1)/grub on this drive."

"Grub2 is installed on the MBR of /dev/sdb, so you have to set BIOS to boot from sdb as first option."

If that's the case, and I'm not doubting your point, but why was I able initially to dual-boot with Crunchbang on the 2nd drive?  I didn't change the BIOS at all. I'm trying to think if I changed the boot drive option with Ubuntu's installer to sdb.  Would that make a difference? 

Thanks for the replies!!  :)

---

### Post by oldfred on 2012-10-01
I do not know if grub has changed its default or you may have clicked on something to change it to install to sdb.

Grub always used to install to sda, even when the BIOS promoted a flash drive used to install to sda. That of course created problems. Many suggested it install to the same drive, if more than one drive found, but I have not seen that posted as a change to grub's installer yet.

I have always suggested that the boot loader be on the same drive as the install, so when one drive fails you can still fully boot from the other. 

But years ago IDE systems often only booted from sda, and that was the standard way to install. Only newer BIOS with SATA capability or IDE/PATA drives with cable select allowed you to choose which drive to boot from in BIOS, not with really tiny jumpers on hard drive.

---

### Post by darkod on 2012-10-01
Hmm, I haven't done many installs on machines with multiple disks, and I always use the manual partitionig anyway where you control where the bootloader goes, so I can't be sure 100%. But I was under the opposite impression.

That windows bootloader was always installing on the MBR of the first disk, while ubuntu was trying to use the MBR on the same disk as the OS installed.

I have seen plenty of threads here where people installed ubuntu, rebooted and the computer booted windows directly. Because windows bootloader was on the first disk, and ubuntu installed grub on the ubuntu disk. How can I explain it if I claim that grub2 always installs on the first disk?

I think they might be trying to do that now with the latest 12.04, the grub2 to get installed on the first disk, to avoid people being confused when grub2 is nowhere to be seen after installing with multiple disks. But for me that would be a step back, not forward. I prefer if grub2 goes to the ubuntu disk during the auto installs.

Just boot from sdb and you're OK. :)

---

### Post by mantisdolphin on 2012-10-01
I changed the BIOS to boot off sdb and problem solved.

Thanks for the help!  :)

---

