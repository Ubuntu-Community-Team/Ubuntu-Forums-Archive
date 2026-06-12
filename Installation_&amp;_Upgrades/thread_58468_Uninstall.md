---
title: "Uninstall"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by RaY2DaY on 2005-08-20
Hi all,

Hope someone can help..... how do I uninstall Ubuntu (or any other linux distro for that matter). I am running two HDD's - Ubuntu is installed on the slave HDD. Win XP no longer sees the HDD as it has been formatted by Ubuntu.
I would like to uninstall Ubuntu & use the slave HDD as a windows disc. How do I uninstall & reformat the HDD so that Win XP can see it again??

All help will be appreciated.

RaY2DaY

---

### Post by heimo on 2005-08-20
You don't need to uninstall Ubuntu - no more than you would have to uninstall Windows before installing Ubuntu over it. Use disk manager or fdisk to delete partition and create new windows partition on it, assign drive letter and format. Start->Run->diskmgmt.msc (IIRC). This is not a place for Windows installation help, but hopefully this helped you.

---

### Post by RaY2DaY on 2005-08-20
Heimo,

Thank you,

I can't believe how easy it actually is!!

---

### Post by heimo on 2005-08-20
[QUOTE=RaY2DaY]Heimo,

Thank you,

I can't believe how easy it actually is!![/QUOTE]

No problem. Sad that you're leaving (I assume you're), but do check back every six months, will you? :) At least keep Live CD near.

---

### Post by RaY2DaY on 2005-08-20
Leaving....in a manner of speaking.

To be honest the whole Linux thing (as an OS) has not really grabbed me that much - a pure "ease of use" issue with me - if I install XP it's a no brainer, all the drivers are there, if not then the drivers I need are provided by the hardware manufacturers etc. Silly things like an HP all-in-one - no driver available on Linux- I can get it to print, but not to scan, nor can I use the GUI for fax / speed dial. Defeats the point of spending R2 k on a printer all-in-one if I can't access half of the functions. Canon LBP800 printer (my workhorse printer) no drivers available!! On the software side - I have an MS Access database that integrates tightly with MS Exel forms for user input in order to output data & results - no open source software is compatible - in essence this is mission critical to me as this is what I earn my living from, therefore I am forced to rewrite (you gotta be kidding - the current project took a year to get where it is - tried and tested and STABLE) or stay with MS Office. 
I realise none of this is an Ubuntu fault, just an inherent problem with converting from MS to Linux (inherent as I see it anyway).

I have both Live CD and install CD - am installing a third 40GB HDD to give Impi Linux a try (Bracing myself for the flaming :) ) May well partition it into 2 & install Ubuntu as well.

I am a fervent supporter of open source (where I can put it to good use) and punt my Smoothy and it's mods to all and sundry - (take this as a punt :) ) - check it out at [Smoothwall Project](http://www.smoothwall.org) .

I was merely concerned as to how to retrieve my disc after installing a Linux distro.....seasoned user in some forums, newbie in others.

RaY2DaY

---

### Post by heimo on 2005-08-20
Thanks for elaborating. :) Appreciated.

---

### Post by RaY2DaY on 2005-08-20
Hmmm, 

By the way.......

Forgot to mention that after formatting the slave HDD I had to edit the MBR.....

Just rebooted the system and HELLO!!! Grub load error 17!!

Easily fixed from Recovery Console though - FIXMBR and FIXBOOT got it sorted!

RaY2DaY

---

### Post by Velox Letum on 2005-08-20
For future reference, if you wish to access your NTFS partition from Linux (do read-only, otherwise its messy). Also assuming hda1 is your NTFS partition.

```
sudo mkdir /mnt/ntfs
sudo mount -t ntfs -o umask=0222 /dev/hda1 /mnt/ntfs
```

This is how I access all my word documents, MP3s, etc.

---

