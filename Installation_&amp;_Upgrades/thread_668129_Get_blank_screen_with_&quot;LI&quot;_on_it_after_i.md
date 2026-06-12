---
title: "Get blank screen with &quot;LI&quot; on it after install reboot"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by tauren on 2008-01-15
I just struggled to get Ubuntu 7.10 installed onto an older server system.  I couldn't get the ubuntu-7.10-desktop-i386 iso to work.  I was getting errors similar to the fd0 i/o errors described in this message:
[URL="http://ubuntuforums.org/archive/index.php/t-587168.html"]
http://ubuntuforums.org/archive/index.php/t-587168.html[/URL]

However, after using ubuntu-7.10-alternate-i386.iso and all_generic_ide, I got the text installer to run and went through the entire install process without problems.

Until the reboot at the end, that is.  When the system boots up, it does all the BIOS stuff, shows the SCSI drives, flashes something that I can't read, but that I think is more bios output, then sits on a blank screen with the letters "LI" in the top left corner and the cursor blanking after it.

I booted into rescue mode with no problems and looked at /boot/grub/menu.lst.  The default includes all-generic_ide, which I though might be missing. 

Any ideas what is going on?  LI isn't the start of LILO, I wouldn't think... But what does it mean?  And how can I get this thing to boot?

This is running on an Intel server board (not sure which model) with dual Intel PIII 800MHz cpus and two IBM 18GB SCSI drives, onboard intel graphics, with a standard IDE cd-rom.  I last had Fedora Core 5 with a graphical desktop installed on the system without any issues whatsoever.

Thanks,
Tauren

---

### Post by Pumalite on 2008-01-15
Memory and graphics?

---

### Post by Partyboi2 on 2008-01-15
> **[COLOR=#FF0000]Q.[/COLOR]** My Linux system says [COLOR=#6666CC]**LI**[/COLOR] while booting system and then boots procedure freezes or halts. How do I solve this problem?
 **[COLOR=#009900]A.[/COLOR]** LILO is a generic boot loader for Linux. This error means few things. LI characters indicate that LILO is having problems. It cannot boot the system.

Not sure how you ended up with Lilo.

---

### Post by tauren on 2008-01-15
> Memory and graphics?

I have 2GB of RAM (4 sticks of 512MB ECC).  Graphics is on the motherboard, so probably standard Intel.  The system was working fine running Fedora Core 5 desktop before I wiped it clean to install Ubuntu, so I wouldn't think there is a problem with memory or graphics.  What should I do to determine if this is the problem?

> **Partyboi2 said:**
> Not sure how you ended up with Lilo.

I did not use the same hard drives that I had FC5 installed on, but used some old drives that I had on hand.  I supposed LILO could have been on them.

However, that doesn't make any sense...  I used the Ubuntu alternate text-based installer and completely changed the partitioning on the both drives.  I set up a 255MB partition on both drives, set them up as RAID1 mirrored, and mounted /boot as ext3.  I also configured the remaining space on the drives as another RAID1 mirrored partition, set the mirrored space up as an LVM volume, and then created root and var partitions within the volume.  

I left a fair amount of the LVM volume unused so that I could add other partitions or alter the existing ones if necessary down the road.  Would that space not have been formatted?  Could LILO still be in there and being run somehow?  

I certainly didn't install LILO during the Ubuntu install.  And when I booted in rescue mode and mounted /boot, all the grub stuff was in there.

How should I solve this problem?

Thanks!

---

### Post by Pumalite on 2008-01-15
You could start from scratch. DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD to make your partitions. I guess you know how to install in a Raid Array.

---

