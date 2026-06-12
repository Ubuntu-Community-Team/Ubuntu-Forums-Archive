---
title: "Ubuntu won't start after hard reboot."
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by araiguma2 on 2014-06-10
Hi everyone,

i hope you can help me with my problem as i am unsure how to proceed from here.

I installed Ubuntu 12.04 64 bit about half a year ago (iirc) on my Dell Vostro 3560 by executing the setup from windows and only had some minor issues with Wifi.

For a project i intended to install the [graph-tools python module]("http://graph-tool.skewed.de/download"). I installed all prerequisites with relative ease. However when issueing the 'make' command i encountered major freezing issues (mouse not moving, clock freezing for 20+ minutes). I figured there was no way around that and hard reset the laptop. Rinse, repeat, same error, hard reset. Figured i'd give it another shot before going to bed, fell asleep, next morning: Laptop frozen again, this time with black screen, hard reset.

This time when i started up Ubuntu i got into GRUB (which i didn't know about) and through some research found that i probably killed some part of my boot sector.

I then used the [Boot-Repair-Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/") which produced the following output: [Pastebin]("http://paste.ubuntu.com/7622019/")
Rebooting put me into GRUB again so i ran a chkdsk as recommended [here]("https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu").
This had no (to me) visible effect. And i consequently tried to apply the second advice on aforementioned link to no consequence (i could not find and found.000 or dir0000.chk directories). The C:\ubuntu\disks\root.disk file is still missing.

So now i'm all out of ideas. If any one of you could help me to fix this that would be super good. 

Alternatively if you could advise me on how to extract data from the  screwed up Ubuntu that would at least let me continue my work on Windows  Desktop using a VM.

Edit:Found a proper [solution.]("http://ubuntu-with-wubi.blogspot.de/2011/08/missing-rootdisk.html")

---

### Post by kc1di on 2014-06-10
Booting with a Live Ubuntu Disc should give you access to your files. and allow you to copy them to another disc. 

According to the Pastebin - your machine is EFI enabled and that may be a problem with boot manager if it's not set up correctly. 
see this [page.]("https://help.ubuntu.com/community/UEFI") 

others may be able to help more.

---

### Post by araiguma2 on 2014-06-10
Hi kc1di,

thanks for the advice. I was actually following another lead and by virtue of google-foo was able to find this sweet short tutorial that applied perfectly to my problem and solved it handily.

[http://ubuntu-with-wubi.blogspot.de/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.de/2011/08/missing-rootdisk.html)

Lessons learned:
1. Don't hard reset Wubi installations - or any for that matter.
2. Any given problem someone has already had and solved.

---

### Post by oldfred on 2014-06-10
Best never to reboot without remembering the elephants:
 
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.

Also wubi's last supported version is 12.04. It does not work with gpt partitioned drives which all new UEFI systems use.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by araiguma2 on 2014-06-11
Hi oldfred,

thanks for the resources. This is probably going to be the next step for me :) It's nice to know that a migration is possible. 

As a followup: How can i set a question to Solved? Or is that not necessary?

Thanks for your time.

---

### Post by oldfred on 2014-06-11
Glad you were able to recover your data. Backup is always a good idea as things happen.

Quick instructions on Solved are in my signature.
       Screen shots of Solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

