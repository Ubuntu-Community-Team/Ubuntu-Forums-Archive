---
title: "New Install, new machine by a newbie"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by lgbpop on 2005-10-10
Hi, I want to install Ubuntu Hoary on a machine I just built.  The machine has 2 HDDs, 460GB total in a RAID-0 JBOD (maximum storage) configuration.  I already have 98SE and XP installed on drives C: and D: and wish to install Ubuntu on drive E: . (see attached screenshot.)  I have partitioned the drives using Maxtor's MAXBlast software.  Drives D: through I: are virtual partitions.  Will Ubuntu stay within drive E: as it's set up (20GB, FAT32) now?  What parameters/options do I choose during setup to avoid its changing or formatting the existing setup?  I tried a practice run on an old Compaq w/PII, 64MB RAM/8GB HDD but got lost with the terminology, and the Compaq just didn't seem to have the minimum install requirements--haven't been able to get it to run.  Sure could use some advice, thanks in advance.

---

### Post by Lord Illidan on 2005-10-10
Hi...
I am not sure whether Ubuntu can be installed on a RAID machine.. That is why I am bumping it up...

---

### Post by mlomker on 2005-10-10
> I am not sure whether Ubuntu can be installed on a RAID machine.. That is why I am bumping it up...

It'd be easier for me to take a look if your attachment were a jpg/png file.

Software RAID (the RAID built into motherboards) generally doesn't work because you need linux drivers and the mobo manufacturers don't offer one.  You can buy a hardware RAID card from [3Ware]("http://www.3ware.com/products/serial_ata2-9000.asp") for about $320 that works great.  

Compaq's SCSI RAID controllers work right out of the box with Ubuntu.  I have Hoary running on an older Proliant 2000.

---

### Post by lgbpop on 2005-10-10
Hi, sorry about the attachment.  The VIA RAID on this Abit board is SCSI also.
[COLOR=red][http://img428.imageshack.us/img428/8729/clipboard010da.jpg]("http://img428.imageshack.us/img428/8729/clipboard010da.jpg")[/COLOR]
The RAID-0 JBOD only treats the 2 HDDs as one large drive, it's not back-up like a RAID-1; would that make any difference?  I can check Abit's website for Linux drivers.  If they had the drivers, would they be installed during or after the Ubuntu install?

---

### Post by mlomker on 2005-10-10
> The RAID-0 JBOD only treats the 2 HDDs as one large drive, it's not back-up like a


My understand is that JBOD makes each drive appear separately, whereas RAID1 appears as one large drive (striping).

>  If they had the drivers, would they be installed during or after the Ubuntu install?

Why not just boot up on the CD to see if things are recognized?  If they aren't then you'd need to Ctrl-Alt-F2 over to a terminal to load the driver before continuing with the install.

---

### Post by lgbpop on 2005-10-10
I may be wrong, but Windows (both OSs) sees the JBOD as one large drive, while the BIOS and POST show both drivers separately.  I saw in another post here that choosing the drive comes rather late in the download so that doesn't worry me; as long as Ubuntu stays within the established drive I'll give it a go and find out.  I've already loaded so many programs that having to do it all over would be a major pain--that's my only concern.  Just waiting for the CD to come in the mail.  I tried the liveCD version already, it'll be a learning experience for sure.  Where would I find a list of the various key combo functions?

---

### Post by mlomker on 2005-10-10
> JBOD as one large drive

Cool.  I've had laptops for years and my servers are all HP/Compaq RAID5, so that's all new to me.


> Where would I find a list of the various key combo functions?

That varies by what you have installed, so it's hard to generalize.  There are commands at the command-line and different ones once you load gnome or KDE.  KDE's control panel allows you to set a lot of them.

I only know a fraction of them and learn a little more every day.  There aren't any books about Ubuntu, as far as I know, so general books on linux (especially debian versions) are where you can pick up some tricks.

---

### Post by lgbpop on 2005-10-10
Pretty new to me, too--last machine (still running great, just too slow) was an HP Pavilion 6636 I bought in '99.  Here's a BIOS shot showing both HDDs.
[[IMG]http://img448.imageshack.us/img448/1282/dscf03053sb.th.jpg[/IMG]](http://img448.imageshack.us/my.php?image=dscf03053sb.jpg) Anyhow, I'll just try loading it in the machine and go from there.  (Here's the direct link if the image doesn't show here.
[http://img448.imageshack.us/img448/1282/dscf03053sb.jpg](http://img448.imageshack.us/img448/1282/dscf03053sb.jpg))

---

