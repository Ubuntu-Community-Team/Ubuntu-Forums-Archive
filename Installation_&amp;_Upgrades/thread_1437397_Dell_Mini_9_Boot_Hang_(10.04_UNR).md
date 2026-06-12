---
title: "Dell Mini 9 Boot Hang (10.04 UNR)"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by sugarland2k on 2010-03-23
Dell Mini 9 Boot Hang
 Grub2
Dell Mini 9 Boot Hang


Running Ubuntu 10.04 UNR (Ubuntu Netbook Release) on my Dell Mini 9.  Every time I booted up, Grub2 would hang right before the logon screen and I had to hit "Enter" to continue.  

I found the following fixed this issue.  "Boot Problems:recordfail" 

Open the Grub file 00_header via

   gksudo gedit /etc/grub.d/00_header

Look for

 if [ ${recordfail} = 1 ]; then
     set timeout=-1
 else
    set timeout=${GRUB_TIMEOUT}
 fi

Change it to


   #if [ \${recordfail} = 1 ]; then
   #    set timeout=-1
   #else
       set timeout=${GRUB_TIMEOUT}
   #fi

Save the file and run

     Code: sudo update-grub

This solution was found at
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

Thanks for the fix! :p

---

