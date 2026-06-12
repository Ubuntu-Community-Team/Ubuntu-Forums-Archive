---
title: "This is getting real frustrating"
date: 2006-05-20
forum: Installation &amp; Upgrades
---

### Post by climbdahill on 2006-05-20
Ok, so i've spent about 5 days trying to load ubuntu.  I had to format my drive, i installed an xp load, then i used remaining space to try and put ubuntu on.  I've had 3 bad burns on 3 different computers using 2 different sets of burning software.  I finally got a good one that the check cd-rom function on the intall likes (all others failed despite the iso's checking out).  Ok, so i'm installing i get past entering usnm and psswd and it starts installing some packages for install, i foget what the step is called, on the menu it's configure apt and it freezes at 25 percent.  Freakin a.  Do you guys think it might be my drive or something about my system.  Win installed fine so i don't think it's my hardware but who knows.  Can i trouble shoot his further?  Or should i assume a bad burn despite the cd checker liking it and try for a 5th burn on again another friends computer.  

Thanks for your help, this has been a very frustrating week.

---

### Post by climbdahill on 2006-05-20
PS, i trying installing 3 ties off this disk and it freezes at hte exact same spot, after installing base system and base packages, etc.

---

### Post by Sef on 2006-05-20
> i foget what the step is called, on the menu it's configure apt and it freezes at 25 percent

Have you used a live CD?  This will check if your hardware is compatible or not.  If it boots up, then likely you can install Linux with no problem.  

> Win installed fine so i don't think it's my hardware but who knows.

Windows can install fine, but not GNU/Linux.

> I've had 3 bad burns on 3 different computers using 2 different sets of burning software.

Once it took me about 6 times to get a good download.  Try using Bittorent.  It automatically md5sums the download.  

[http://www.bittorrent.com/]("http://www.bittorrent.com/")

What are your system specs?

---

### Post by climbdahill on 2006-05-21
Thanks for you reply!!

Yes, the live cd runs just fine.  My specs are an asus x-series mb, sempron 2400+, 512MB ddr, maxtor 200GB hdd.  Do you need more details?  So, i've downloaded the iso like 4 times and the md5 comes out correct every time.  Can the iso still be corrupted?  

Ok, so i've burned 4 copies of the install cd from different places.  When i start the install i check the cd integrity right away using the intall function and 3 of them pass.  However, one of them freezes as mentioned above in my previous post.  The other 2 pass, but then i do the install and they both freeze after the base install when installing other packages.  Then i go back and check the cd again after the install has failed and the same cd integrity test fails at the same file, (/pool/main/a/acpi/acpi_0.09-1i386.deb).  This came off of two different downloads.  Does this make sense?  The cd passes the test and then part way through the install, i run the test again and it fails?  

I've never had this much trouble installing anything else.

edit: This is getting hilarious, so i take one of the disks that failed and shutdown and then boot back up and go back into the intall process and do a cd integrity test and it passes, and then i install and it fails again.  What does this mean?

---

### Post by climbdahill on 2006-05-21
holy frick it worked.  A i tried one of those cds a third time and it worked! I got a full install yahhhh!

---

