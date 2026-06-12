---
title: "Format and re-install windows (GRUB!)"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2006-06-26
Hi all

I've tried searching for this but of course the keywords 'reinstall' and 'windows' throw up a slew of irritating 'why do you use linux when there's windows' and 'when did you finally ditch windows' and 'ubuntu sucks i'm going back' threads.

Basically I want to reinstall windows so it's nice and zippy again, but I'm fearful that in doing that it will screw up GRUB and replace it with the windows boot loader (ntldr?).

So how can I reinstall windows and maintain my current setup, i.e. dual-boot?

Cheers in advance!

---

### Post by Herman on 2006-06-26
Here are two ideas you can choose between for doing this.

One that not too many people use is to back up the IPL section of your Master Boot Record, and save the file to another device (media). The example describes usingr the 'Desktop Live/Install CD and storing it to a USB drive, but a floppy disk or an MP3 player or other small drive would be just as good.
*[Click here]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")* to read how to back up and restore your MBR.

The most popular method is to simply Restore Grub. *[Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub")* for some links to the Ubuntu Wiki about that. Under those on the same page is an illustrated example of how to use your Ubuntu Dapper 'Alternate Install' CD to restore GRUB using 'Rescue a broken system' (Recovery Mode). That way would be the easiest.
Regards, Herman

---

