---
title: "How to solve GPT Problems during instalation."
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by joaquin4 on 2013-10-06
Hi guys,
I had this problem during my ubuntu installation, and it was a fight of two days, nobody could give me a solution in the IRC chat, So I found that srs5694 gave a solution to this in 2010, but was kind of old, and things had changed. For somebody new in Ubuntu and Linux, got pretty difficult to solve this. So I want to leave this Guide in a place where anybody could solve this.

[B]Describing the problem:

[/B]The issue comes when your computer comes with Windows 8 and operating systems that works with EFI and GPT and you try to install another operating system like windows 7, the bad way: Just deleting all partitions and formating the drive. The problem with this is that the hard disk still thinks that is a GPT drive but the tables are missing, and gparted and Ubuntu's installation just wont install on a "corrupt" drive, so it shows that the whole hard drive is empty. If you open Gparted in Ubuntu's live cd, it says:
```
[COLOR=#000000]Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.[/COLOR]
[COLOR=#000000]However, it does not have a valid fake msdos partition table, as it should.[/COLOR]
[COLOR=#000000]Perhaps it was corrupted -- possibly by a program that doesn't understand GPT[/COLOR]
[COLOR=#000000]partition tables. Or perhaps you deleted the GPT table, and are now using an[/COLOR]
[COLOR=#000000]msdos partition table. Is this a GPT partition table?[/COLOR]
[COLOR=#000000]<Yes / No Button>
[/COLOR]
```

[B]The solution without having to loose all your information and you previous install of Windows 7
[/B]Fortunately the solution isn't that difficult, but for a new ubuntu users it is not just trivial.
**1)** First go to Ubuntu's live CD/USB and just choose "Try ubuntu". Then go to to this link in the web browser (mozilla firefox) [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and write "gdisk" in the search box. Then choose your ubuntu's version (13.04 is "raring"). Then go to the bottom of the page and choose the version corresponding to your system architecture, In my case I had a x64 processor, so I choose amd64. Afther that, choose the download mirror and just double click on the downloaded file. It will open Ubuntu's software center and you can press the install button on the right side of the window. 
**2)** After installation you have to open "Terminal" that is found by clicking the search button on the right side bar and typing "Terminal".
**3) **After that type "sudo sgdisk --zap /dev/sda" without quotes. It might complain about partition problems, but it will still work.
> **"fcuk112"]
[COLOR=#000000] Be sure to use the --zap option, not --zap-all said:**
> 

4) The programs is really fast so you should be able now to continue the installation of Ubuntu and it'll recognize the other OS installed on the HDD,
[B]The easy and fast way of doing it (You loose all your information and previous installs of OS)
[/B]Just install ubuntu in the hard drive, it will format it and leave ubuntu installed in the whole hard disk (NOTE: You will lose all you other partitions due that ubuntu sees all the HDD as a single empty partition.

Hope this guide helps anybody.

---

### Post by oldfred on 2013-10-06
Because of a lot of those issues, Rod (same author as the one that created gdisk) created a separate program just to fix the issue of Windows only deleting the main gpt partition table when converting to MBR(msdos) and leaving the backup table. You can use gdisk & sgdisk, but fixparts is a bit easier.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

