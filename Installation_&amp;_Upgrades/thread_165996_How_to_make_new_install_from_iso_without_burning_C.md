---
title: "How to make new install from iso without burning CD?"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by minghai on 2006-04-25
Hi all,

    I love to try new versions of Ubuntu, Kubuntu and Xbuntu (new flights, betas, etc) but I'm ending up with tons of burnt CDs which I toss once a newer version comes out.  In the interests of saving the environment and money, is there any way for me to download the latest iso and do a clean install from it without burning a CD?  Do I need to create a partition and "open" up the iso there?  Thank you!

Ming Hai

---

### Post by lha on 2006-04-25
Take a look at the [wiki]("https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies").

---

### Post by minghai on 2006-04-25
The solution in the wiki requires floppy drives, unfortunately, my PCs don't contain any floppy drives.  

Ming Hai

---

### Post by matelot on 2006-04-26
Obviously you've discounted re-writable CDs, but I wonder if your BIOS will let you boot from a second HDD if the ISO could be unpacked to there. Just a thought. :-k

---

### Post by minghai on 2006-04-26
I haven't had good experiences with rewriteable CDs.  I've extracted the iso for Xubuntu 6.06 beta to a seperate partition and I'm trying to figure out how to setup a grub entry to boot from that partition.  Any advice?  Thanks!

Ming Hai

---

### Post by lha on 2006-04-26
[QUOTE=minghai]The solution in the wiki requires floppy drives, unfortunately, my PCs don't contain any floppy drives.[/QUOTE]

[QUOTE=minghai]I haven't had good experiences with rewriteable CDs.  I've extracted the iso for Xubuntu 6.06 beta to a seperate partition and I'm trying to figure out how to setup a grub entry to boot from that partition.  Any advice?  Thanks!i[/QUOTE]

That wiki page is still useful for you. :) Look for "Booting into the Installation". You don't need a grub boot disk as you already have grub on your hd.

---

### Post by minghai on 2006-04-26
Great I'll give the wiki a try.  Thanks!

Ming Hai

---

