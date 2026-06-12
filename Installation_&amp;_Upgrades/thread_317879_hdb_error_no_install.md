---
title: "hdb error no install"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by ESPOiG on 2006-12-13
hey all my new comp is failing to install kubuntu well it wont boot the live cd at all, the specs are in my sig. heres the error i keep getting about 1 min into the boot screen loading

[1719716.164000] hdb: ide_intr:huh? expected NULL handler on exit
[1719716.212000] Buffer I/O error on device hdb, logical block 177902

now in my knowledge this means there is a sector or a block on the hdd that has an error, but see i have 3 hdds and im not sure which one it is. i dont want to pull the comp apart and start unpluggin hdds straight away i want to know if anyone knows about this problem or has any idea about what it could or what i could do. so far i have tried formattin the drives in NTFS and FAT32 and tried booting gParted but that failed because i have no screen??? so yeh x wouldnt load. im not sure what i should do now is there a program that could tell me which hdd this hdb one is in windows because i had to fall back to it, i tried partition magic but that fails at telling me the hd* so im not sure

---

### Post by hutxubix on 2006-12-13
Hello,

I was going to post almost exactly the same problem. What I get when I try to boot with live CD is:

[17179723.336000] hdb: ide_intr:huh? expected NULL handler on exit
[17179723.384000] Buffer I/O error on device hdb, logical block 357564

and if I wait, it keeps repeating and repeating.

A funny thing about this is that it already happend to me with Ubuntu 6.06 and I gave up and installed Debian without any problem at all, so I don't think it is a problem of the computers.

Another funny thing is that my computer is similar to yours: 

AMD ATHLON 64 X2 3800+ 2x512k S939
M DIMM DDRAM 512MB PC3200 NANYA
PB SIS 756 MATX ASR-939S56-M A R USB2 DDR400 S939
HD IDE-ATA133 200.0GB SAMSUNG SP2014N 7200RPM

Well, I really would like to install ubuntu. Does somebody have an idea?

Thanks.

---

### Post by ESPOiG on 2006-12-13
lol yeh it is just the number that changed at the front and it keeps repeating over and over again :S... yeh can anyone help us??

---

### Post by ESPOiG on 2006-12-14
anyone??

---

### Post by hutxubix on 2006-12-14
Hello again,

I've tried the 64bit version and, at least, the installer works (I didn't installed because I hadn't time, but I will do soon). So I think that, your as, the best solution is to move to 64bits. What do you think about it?

---

### Post by ESPOiG on 2006-12-15
i got it to work im runnin kubuntu 6.10 right now :D... what i did was

1. win xp installed
2. partition magic
3. made sure all my drives/partitions were formated as something (ntfs)
4. ran defragmentation in accessories i think
5. restarted computer put in cd :D
6. got to boot select
7. selected the safe graphics mode boot and it worked fine

it had no problem with my drives, hope this helps it worked for me

---

