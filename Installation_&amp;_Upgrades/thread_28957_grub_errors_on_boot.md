---
title: "grub errors on boot"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by jd142 on 2005-04-22
I have a monarch made AMD 64 3.400+ computer with 2 sata drives, 2 ide drives and 2 dvd recorders.

I booted from the Ubuntu 5.04 live/install dvd and it correctly detected all of my drives and partitions.  I installed grub on sda, which is the first sata drive and is my boot drive.  I correctly detected my windows partition and got everything right.

But when I rebooted, all I got on my screen was:

LI 0909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909


All down the screen.  It might not have been 09, it might have been 07 or something like that.  I can't remember and I'm at work now.

Any idea on what the problem might be?  I was able to install another linux distro that used lilo and it worked just fine.

Thanks

---

### Post by jdodson on 2005-04-22
[QUOTE=jd142]I have a monarch made AMD 64 3.400+ computer with 2 sata drives, 2 ide drives and 2 dvd recorders.

I booted from the Ubuntu 5.04 live/install dvd and it correctly detected all of my drives and partitions.  I installed grub on sda, which is the first sata drive and is my boot drive.  I correctly detected my windows partition and got everything right.

But when I rebooted, all I got on my screen was:

LI 0909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909
090909090909090909090909090909090909090909090909


All down the screen.  It might not have been 09, it might have been 07 or something like that.  I can't remember and I'm at work now.

Any idea on what the problem might be?  I was able to install another linux distro that used lilo and it worked just fine.

Thanks[/QUOTE]

yeah your master boot record is hosed somehow.  you need to reinstall grub.  you can do that from the install cd.  look for the rescue option i believe.

---

### Post by jd142 on 2005-04-22
[QUOTE=jdodson]yeah your master boot record is hosed somehow.  you need to reinstall grub.  you can do that from the install cd.  look for the rescue option i believe.[/QUOTE]

Ok, I just figured since the grub install on the cd hosed it up once, that running it again wouldn't be much help.

Thanks, I'll try that.

---

### Post by jd142 on 2005-04-24
Well, after a second re-install, this time grub did nothing at all, because my lilo install from Mandriva LE 2005 was left intact.  Ok, I thought, I'll just use lilo despite the horrible Mandriva theme.  But Ubuntu didn't recognize or detect my usb MS intellimouse explorer, so I had no mouse.

I think I'll go back to Mandriva for now on my home computer.

---

