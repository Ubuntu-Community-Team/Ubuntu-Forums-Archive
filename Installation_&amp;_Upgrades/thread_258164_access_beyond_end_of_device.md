---
title: "access beyond end of device"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by donmiguel on 2006-09-15
Hi you ubuntu-people!

Actually, i have installed Ubuntu a long time ago, but i don't know what i did (except installing the lsh-utils & glib-doc packages recently) that my ubuntu (or just the kernel) won't boot anymore.

If I try to start in safe mode there comes this message ever and ever again:

[#] attempt to access beyond end of limit
[#] hda3: rw=0, want=[some number], limit [some smaller number]

#=increasing number.

That means that i'm not even able to boot in safe mode...

I would be glad for any help for me solving this problem... i have no idea what can cause this weird error message, that it looks in a "sector" that doesn't exist..

Greets Michael

EDIT: sorry, misplaced this post a little bit, maybe an admin could move it one up in the hierarchy..thx

---

### Post by donmiguel on 2006-09-15
so, i booted from dvd & made an fsck on this hda3. it says that it is clean... unluckily it's the partition with the root file system! :( 

What can I do?! I'm clueless here, the and in the net there is already tons of wast (of information) .

Michael

---

### Post by Herman on 2006-09-15
Hello, donmiguel,
I am only guessing, of course, but your description of the error message makes me think of BIOS issues.
My guess would be maybe it has something to do with your computer's BIOS settings. There is a small battery inside our computers that keeps your computer's clock running when the power is off and keeps your CMOS (programmable part of your BIOS) preserved. Here is a nice brief link about the BIOS, [BIOS (Basic Input / Output System)]("http://webpages.charter.net/netw_1/bios.htm").
> [FONT=Verdana, Arial, Helvetica][SIZE=2][COLOR=black][FONT=Verdana, Arial, Helvetica][COLOR=black][FONT=Verdana, Arial, Helvetica][COLOR=black][FONT=Courier, Courier New][COLOR=black][FONT=Verdana, Arial, Helvetica][COLOR=black][FONT=Courier, Courier New][COLOR=black][FONT=Verdana, Arial, Helvetica][COLOR=black]If this battery loses power, then your computer can forget all settings, including hard disk drive settings.[/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/FONT][/COLOR][/SIZE][/FONT] How long has it been since the last time you replaced the battery on your motherboard for your computer's BIOS? Could that have something to do with the problem? How is the time in your computer, it the time always correct when you start up with the internet unplugged?
Here is a more detailed link about BIOSes, [The Definitive BIOS Optimisation Guide]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")
And here is a detailed link about BIOS hard disk drive size limits, [URL="http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm"]http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm

[/URL]I am just guessing here, so take this post with a grian of salt, but the BIOS is probably where I would begin looking to try to find out more about what this problem could be.
I hope this post will be helpful, 
Regards, Herman

---

### Post by donmiguel on 2006-09-16
Hi Herman.

Thanks already for your opinion.. i'm gonna take a look as soon i find the time (gotta study biochemistry). But the thing i wonder about: if there is sth misconfigured in bios, would that not affect my windows as well? because, now i am in windows xp, that works.

Thanks a lot!!!

Greets
Michael


EDIT
ah yeah: the battery question:
in fact, i bought this motherboard about 4 years ago and never changed it...

---

### Post by donmiguel on 2006-09-16
I have new info :)

I did a check now with the partition magic of the partition (said to be ext3) in question, and it gives me this error message in a seperate window:

Error #1201
Ext2 superblock contains illegal information

and in the "checking window" it is displayed:

Severity: Critical
Fixed: 
Number: 1212
Description: Inode %lu has an illegal block %lu

after this warning, the partition check is stopped.


As well if i'm trying to view the partition properties, PartitionMagic tries to get additional information (a progress bar shows the progress :) ) and then it stops at the same progression as the check and the warning pops up: Error #1212. Inode 0 has an illegal block 0


And I redid the fsck-test:
% sudo fsck.ext3 -fvn /dev/hda3

result:

a lot of weird thinks about inodes of specific files and the summary below

-----
/: ********** WARNING: Filesystem still has errors **********


  165605 inodes used (13%)
    5385 non-contiguous inodes (3.3%)
         # of inodes with ind/dind/tind blocks: 9907/176/0
 2213670 blocks used (88%)
       0 bad blocks
       0 large files

  133526 regular files
   13910 directories
    1327 character device files
    4185 block device files
       3 fifos
    1427 links
   12611 symbolic links (12340 fast symbolic links)
       6 sockets
--------
  167012 files


That's about it..puhh what does all that mean?!

---

### Post by Herman on 2006-09-17
It looks like you already know more than I do about running fsck, sorry about my battery guess being wrong too,
Regards, Herman :D

---

### Post by donmiguel on 2006-09-17
hey, not so fast.. i just restarted my computer after unplugging it from the power and network, and in fact, the time has a lag of a half an hour!!
maybe there is a correlation?!
i'd just be glad if someone knew how to interprete the results i've got.. hm
thanks herman

---

### Post by donmiguel on 2006-09-23
So really no one has an idea?? i'm really clueless here after a week of research.. :(

---

