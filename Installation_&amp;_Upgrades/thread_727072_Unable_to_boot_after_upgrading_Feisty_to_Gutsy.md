---
title: "Unable to boot after upgrading Feisty to Gutsy"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by RickKnight on 2008-03-17
I performed the Feisty to Gutsy upgrade on my desktop PC. The upgrade hung at 2%. After a couple of hours I killed the process and restarted it at a terminal. This time it completed successfully. I tried to reboot my PC but now all I get is a BusyBox shell and a message that the hard drives don't exist. I get this message...

Check root= bootarg cat /proc/cmdline or missing modules,devices: cat /proc/modules ls /dev

ALERT! /dev/sdb5 does not exist. Dropping to a shell.

Then I get the Busy Box banner and prompt

(initramfs)

I've tried editing /boot/grub/menu.lst and changing the drive from id to path but I get the same message, just a different spec for the same drive. My system is intact and it is upgraded, but for some reason the hard drives are not being found or started. I can still boot my previous Feisty kernel so I can try to repair the problem, I just need to know where to start. Any idea what I can do to solve this problem?

Thanks again,
Rick

---

### Post by mmichalik on 2008-03-17
at the (initramfs) prompt, just type the word reboot and press enter

that should get you going.

---

### Post by RickKnight on 2008-03-18
> **mmichalik said:**
> at the (initramfs) prompt, just type the word reboot and press enter

that should get you going.

Thanks Mmichalik, but that just rebooted the PC to the same error.

Rick Knight

---

### Post by mmichalik on 2008-03-21
Rick,

Did you ever get past this?

I have been swamped this week and haven't had time to look back in here.

---

### Post by RickKnight on 2008-03-21
> **mmichalik said:**
> Rick,

Did you ever get past this?

I have been swamped this week and haven't had time to look back in here.

No, I'm still trying to figure it out. Fortunately, I can boot to a prior kernel and get full use of my machine, but I would like to solve this. I know something is going to break using an older kernel with 7.10.

The new kernel does see my SCSI tape drive and my USB memory stick adaptor, just not Hard Drives. Do you have any other suggestions?

Thanks again,
Rick

---

### Post by mmichalik on 2008-03-26
man, i have been looking for some thing to help out with this for days and I'm coming up with nothing. if you boot the old kernel, go to a terminal from the desktop and type sudo apt-get update does it tell you you have broken packages?  If so, what happens when you do a sudo apt-get install -f?

I know this sounds weird because your error seems to be more of a grub issue then a package / OS issue but you did say that it died at 2% during the upgrade and I wonder if anything is just 'not right', ya know?

You could also try the rescue command from the initramfs prompt but, I don't have much experience with that.

If you have been able to fix it, let me know what you did.  I'm interested in figuring it out.

---

### Post by RickKnight on 2008-03-27
Mmichalik,

I'm still having this problem. I've run 'sudo apt-get update' and it runs without error, and without finding anything to update. I've also tried 'sudo apt-get -f install' and that also completes without error. I don't think the problem has anything to do with GRUB, but I've tried 'sudo update-grub' and 'sudo grub-install'. Neither solved the problem. I've also tried 'sudo update-initramfs -c -k 2.6.22-14-generic'. That also did not provide a solution. It was suggested, by NoOp at [email]ubuntu-users@lists.ubuntu.com[/email], to download the Gutsy Alternative install CD and re-run the upgrade from that. I will try that this weekend. I'll post the results here and at [email]ubuntu-users@lists.ubuntu.com[/email].

Rick

---

### Post by mmichalik on 2008-03-28
Cool.  I hope it works for you and I wish I had better answers for this......

Don't forget to backup your important files before you re-do the upgrade.

---

### Post by RickKnight on 2008-04-04
Trying to re-upgrade did not fix the problem, in fact it indicated that the system was up to date and no upgrade was needed.

I have made some progress though. I think the problem is an incompatibility with my Via VT82C586 chipset and libata. I have added 

via2cxxx
generic
ide_disk
ide_cd

to /etc/initramfs-tools/modules and ran

$ sudo update-initramfs -c -k 2.6.22-14-generic.

After a reboot I can now see my CDROM and DVD drives. They were not being started prior to this.

Do you, by chance have Via VT82C586 chipset?

Rick Knight

---

### Post by RickKnight on 2008-04-05
I hate to reply to my own post here but...

I just Downloaded and burned the Kubuntu 8.04 Desktop iso. I booted with the Live CD mode and ALL of my drives are available, and as /dev/hd devices, not /dev/sd. Just 20 or so days until 8.04 is released and I plann on being an early adopter.

Rick

---

### Post by RickKnight on 2008-04-09
MMichalik,

See my bug report here [https://bugs.launchpad.net/bugs/212042](https://bugs.launchpad.net/bugs/212042). This seems to be a bug with the Via IDE / PATA drivers introduced in Gutsy. It has been fixed in Hardy. 

Rick

---

### Post by RickKnight on 2008-04-11
MMichalik,

Found a solution. First, I rebuilt the Gutsy kernel to add support for the PATA_VIA  module. After the rebuild was complete things still didn't work. Snooping around a bit more I found this kernel parameter "all_generic_ide". I added this parameter to the kernel statement in /boot/grub/menu.lst. I rebooted again and this time it worked. My system booted properly and my drives now show up as SCSI devices (/dev/sdxn and /dev/scdn). Then I tried to boot the original Gutsy kernel (without pata_via) with this kernel parameter but it did not boot. So the solution seemt to be...

rebuild the Gutsy kernel with PATA_VIA support
install this new kernel
modify menu.lst adding "all_generic_ide" to the kernel parameter for the new kernel  
reboot.

Hope this helps
Rick Knight

---

