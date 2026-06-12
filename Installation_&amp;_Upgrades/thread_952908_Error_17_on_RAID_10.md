---
title: "Error 17 on RAID 10"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by ab_t on 2008-10-19
Hi, I'm trying for the last couple of days to get around an installation issue.
I have 1 SATA HDD not in RAID, and 4 HDDs on RAID 10 (0+1), with onboard RAID (ICH10R).
I'm booting from the first drive (not in RAID). After some strugle installing Windows (didn't recognize the floppy and I had to make a Windows disk with the driver included) now I have problems with the linux install.

Historically, I used mainly PCLinuxOS (KDE, ease of use, fast) but my new MB has Atheros for LAN, and the driver I think it's included only on the kernel 2.6.27 (maybe also 2.6.25), and there no new PCLinuxOS. The minime version, install fine and has no issues booting, but I just can't install the LAN.

So I tried kubuntu; It does install fine, but at boot grub gives me an error 17: cannot mount selected partition. Selecting Windows from the same grub works fine. 
If I chose to go with what kubuntu recommended in the install, like splitting in half whatever partition he prefers (right now I have 3 primary and 3 extended, but I can adjust them as needed), he does manage to boot correctly (although combines the previous grub menu resulting a double length menu). I tried looking through the menus but I can't figure what's wrong.

Tried also with OpenSuse 11, and although it figures there is some sort of RAID, it cannot even install the grub menu (it does make it much easier than kubuntu to edit it though, but my technical skills are limited)

I suspect that the same problem is with Ubuntu or LinuxMint. How can I get around it? I don't get it why it has to be so difficult when PCLinuxOS minime which is more than 6 months old does it without any problems :mad:

PS. I'm trying Kubuntu 8.10 beta, the CD. Should I try the DVD?

---

### Post by ab_t on 2008-10-19
this starts to become "funny" now; I saw that PCLinuxOS just released the 2009 beta version, which despite being newer than minime, doesn't know to run from the IDE CDROM (happens when it doesn't know the driver for the ICH10R) just from the external DVD-ROM. Newer but less capable? :confused:
Anyway, has the kernel 2.6.26 and it doesn't detect the network :;

So, anybody has any ideas how can I solve it from Kubuntu or Ubuntu (I'm can use Gnome, Just prefer KDE, although in Kubuntu feels more like and afterthought)?
Thanks in advance

---

### Post by ab_t on 2008-10-19
Looks like I managed to solve it, although it really shouldn't be so difficult. If I was just a Windows user trying Kubuntu I would have been long time gone :(

So I installed PCLinuxOS 2009 beta, then I installed Kubuntu 8.10.
Thank god the Grub installed by Kubuntu included the previous grub set by PCLinuxOS and that it can be easily edited (with e): so I looked on the line for PCLinuxOS (which was booting fine) and figured it out where Ubuntu got it wrong:
- first, it was thinking that his partition it's actually the Windows one (hd0,0) instead of (hd0,2)
- second, on the command for init I had to add the partion location in front of it: **(hd0,2)**/boot/init ....

As I said, the KDE in Kubuntu feels more like an afterthought, basic functionality is missing but in the same time it doesn't have anymore what was taken out from gnome. As an example, I had to install kdesystem-utilities (or something like this) in order to create users, otherwise it just wouldn't work :mad:

---

