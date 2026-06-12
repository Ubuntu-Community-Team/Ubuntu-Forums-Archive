---
title: "Preventing bootloader from auto installing"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by krasnit on 2010-05-03
I installed Windows 7, Vista, Hackintosh, and Ubuntu 9 on separate hard drives, and with only the specific install hard drive connected during install. In other words, there was no boot manager on any of the drives once all were connected to the computer.  I would use the BIOS to select the drive to boot up.
Well folks, I booted the Ubuntu drive this evening, something I did only once before a few months ago to see what Ubuntu was all about.  When I left Ubuntu this evening and went back to boot up another drive, the Grub boot loader was everywhere.  Windows 7 and Vista start OK, but not my Hackintosh which will not boot at all.  I can fix the mbr on Win 7 and Vista, but Hackintosh has to be re-installed it seems, and that was not an easy thing to get configured.  

The Grub installed itself just by booting up Ubuntu. Is there any way to prevent Ubuntu from doing this?

If not, sorry folks, but I must consider Ubuntu nothing more than a glorified virus that messes up all my hard drives, and it will be gone... forever.

---

### Post by louieb on 2010-05-04
Don't know what you did - but GRUB does not go about installing itself on every MBR in sight.  It certainly would not do that automatically just by booting to Ubuntu Linux.  

Just out of curiosity please get and run the   [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  and put the results.txt in your next post.  - Information provided by the script will help get things straightened  back out. 

 :D yea well grubs will eat grass too. - the organic cure for that is nematodes.

---

