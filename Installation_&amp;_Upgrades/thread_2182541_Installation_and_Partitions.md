---
title: "Installation and Partitions"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by javirk on 2013-10-21
Hi, yesterday I decided to install Ubuntu 13.04 in my computer. I downloaded it and burned it into a CD. Installation started properly, but, when it got to the partitions part (I have windows 8 installed and I want dual boot), it says me I have no other OS. And if I have a look at what it tells me my partitions are, it says me I have 500Gb of empty space (the whole space of my HDD). I went to GParted with the LiveCD, but it says me the same. ANd also I have done this:
```
gdisk /dev/sda
```

Which I found [here]("http://www.linuxbsdos.com/2013/02/26/zap-gpt-data-structures-from-a-disk-while-preserving-existing-mbr-partitions/"). But it answers me as follows:
```
[COLOR=#000000][FONT=courier new]Caution: invalid backup GPT header, but valid main header; regenerating[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]backup header from main header.[/FONT][/COLOR]

[COLOR=#000000][FONT=courier new]Partition table scan:[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]  MBR: protective[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]  BSD: not present[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]  APM: not present[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]  GPT: damaged[/FONT][/COLOR]

[COLOR=#000000][FONT=courier new]****************************************************************************[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]verification and recovery are STRONGLY recommended.[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]****************************************************************************[/FONT][/COLOR]

[COLOR=#000000][FONT=courier new]Warning! Secondary partition table overlaps the last partition by[/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]33 blocks![/FONT][/COLOR]
[COLOR=#000000][FONT=courier new]You will need to delete this partition or resize it in another utility.[/FONT][/COLOR]
```

So I don't know what to do, If you could help me I'd be really grateful.

Bye!

---

### Post by TheFu on 2013-10-21
Read up on Win8 UEFI and Ubuntu.  I hope you didn't change anything. There are some mandatory pre-install steps.
Search for "UEFI Ubuntu" with your favorite search engine - something from *.ubuntu.com should come up. Read that page carefully.

Old guys like me are avoiding UEFI another few years. Thanks for being a beta tester!

---

### Post by javirk on 2013-10-21
Hi, I have both UEFI boot and FastStartup disabled. So I'm not sure if that's the problem, because the CD starts properly and I can use the LiveCD with no problem...

Thank you for answering!

---

### Post by oldfred on 2013-10-21
This will cause issues. Any partition type error and many partition tools fail. And this seems to be a common problem with not easy solution. Not use if sgdisk lets you modify last partitions end or not.

>  Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.



This is by the author of gdisk on same issue.
[http://askubuntu.com/questions/15037...n-overlaps-gpt]("http://askubuntu.com/questions/150378/how-to-fix-mbr-partition-prior-to-ubuntu-installation-a-partition-overlaps-gpt") repair gpt:
[URL="http://www.rodsbooks.com/gdisk/repairing.html"]http://www.rodsbooks.com/gdisk/repairing.html
[/URL]http://ubuntuforums.org/showthread.php?t=2179942
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

---

