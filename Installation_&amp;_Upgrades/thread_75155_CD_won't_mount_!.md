---
title: "CD won't mount !?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by toujours on 2005-10-13
OK, so I downloaded the iso image this morning, burnt a CD, popped it in my drive and rebooted my PC.

[LIST]
[*]The CD booted and I chose standard install. Then I chose language and keyboard.
[*]Then the installer tries to mount the CD - wasn't it already mounted ??
[*]The installer says no, I can't mount the CD, maybe it's not in the drive...
[/LIST]

I try again a few times, then I abort and quit the installer.

Any ideas ?

I'll try burning another CD after downloading from a different mirror this afternoon, but would welcome feedback first if possible...

---

### Post by coopo on 2005-10-13
Did you check if the ISO had a correct MD5 sum?
If not look here [http://theopencd.sunsite.dk/md5.php](http://theopencd.sunsite.dk/md5.php)

---

### Post by the_crabe on 2005-10-13
Have you got 2 cd-rom drives ?
Here the installer only tries one of my cd-rom drives, even if the CD is in the other drive at boot ...
Hope this helps :-)

---

### Post by woodface on 2005-10-13
toujours, you are not alone. I have exactly the same problem with 5.10. It boots fine from CD and begins executing the installaer, but after selecting language, and keyboard layout it reports: 'Cannot mount the CD drive'. I had tried 5.10 preview and it had exactly the same problem, so I am not so suspicious of bad burn, having said that where can I find the correct MD5 hash for my ISO file?

I am trying to instal the released 5.10 AMD64 version from cd via ISO image.

Also, only 1 CD drive (AOpen dual layer DVD+-R).

Any ideas?

Thanks,
Wood

---

### Post by toujours on 2005-10-13
[QUOTE=woodface]toujours, you are not alone. I have exactly the same problem with 5.10. It boots fine from CD and begins executing the installaer, but after selecting language, and keyboard layout it reports: 'Cannot mount the CD drive'. I had tried 5.10 preview and it had exactly the same problem, so I am not so suspicious of bad burn, having said that where can I find the correct MD5 hash for my ISO file?

I am trying to instal the released 5.10 AMD64 version from cd via ISO image.

Also, only 1 CD drive (AOpen dual layer DVD+-R).

Any ideas?

Thanks,
Wood[/QUOTE]

Thanks for confirming. I downloaded a second iso image, this time using bittorrent. I burnt it and tried to reinstall with the same problem. I too only have one DVD/CD drive (NEC).

I'm using the 386 iso image

My motherboard is new though, it's an MSI RS482-IL with ATI chipset. I reinstalled Hoary just before changing motherboard, CPU (AMD 64) and memory. Could this be something to do with it ?

I'm going to run the MD5 checksum "just in case", but I have never before had problems downloading and burning CD images (Warty, Hoary, Mandriva...) . I use NERO under Windows, by the way...

---

### Post by toujours on 2005-10-13
This link talks about this problem too :

[http://www.ubuntuforums.org/showthread.php?t=71671&highlight=cd+mount+breezy+install]("http://www.ubuntuforums.org/showthread.php?t=71671&highlight=cd+mount+breezy+install")

That makes four of us...

---

### Post by toujours on 2005-10-13
OK, third time lucky !

I downloaded the AMD 64 image instead, burnt it and LO AND BEHOLD ! It worked... :eek: 

Now I have other problems, but these are taken up in another post... :mad:

---

### Post by woodface on 2005-10-14
toujours and others,

Ok, after a good nights sleep things have become clearer, coopo was right, the CD was bad, good ISO download, bad burn.

The same CD failed on another AMD64 pc, re-burning the ISO cured the problem for me.

Now to sort out the video problem...

thanks all,
Wood

---

### Post by AlexMartinius on 2005-10-25
I've got the same problem. I checked my iso using FastSum and the MD5 sum was correct, so I guess the cd is fine. I also tried another cd, which worked fine on my server, but on my other computer, it won't mount.

I've got 2 drives. A Plextor PX708a DVD-writer and a Asus DVD-rom drive. When I boot the install from the Plextor, everythin seems to hang after loading IDE support. Then I tried the other drive and the message about nog being able to mount the cd appeared.

When I installed Hoary a few months ago, I had no problem at all. But the Hoary installation won't run that well either. It mounts the cd, although it took quite long, but after scanning the disk, it seems to hang (I didn't wait very long, but at leest 2 or 3 minutes, I don't recall the installation being that slow when I installed Hoary last time).

Any suggestions what might be the problem?

---

### Post by AlexMartinius on 2005-10-25
I've burned a new cd, this time on 16x, since I remembered some cd's I burned wouldn't work on some hardware (not my own hardware, I've never had any problems, but you never know), but still the same problem. Well, almost the same.

I disconnected the Asus drive after I read somewhere that maybe having 2 drives could be the problem. It didn't work. But that time, I did get the message about being unable to mount the cd in my Plextor drive.

I still don't understand why the cd that worked fine when installing Ubuntu to my server won't work now. I thought about ordering a cd, but I don't think that would make a difference.

Just in case it matters, my motherboard is a Asus P4P800 Deluxe.

---

### Post by rexio8 on 2005-10-27
I've got a similar problem. I've got 2 drives. Teac Cdrw and Nec 3520 Dvdrw. Ubuntu live or instalation cd won't work. The computer boots from the cd, I can choose the language and the keyboard language but I get an error while detecting cd drives. I've tried to disconnect one of the drive but still the problem exists. The cd is fine cause it works on my dell laptop. My motherboard is also Asus P4P800 Deluxe and I think that something connected with it could be the cause but I don't have any idea what could it be. The bios settings seem to be ok. Please help.

---

### Post by AlexMartinius on 2005-10-28
Damn, this is confusing. I didn't see the second page of the threat until I posted. So this wasn't the wrong thread, I just didn't recognize it. So I'm still wondering if anyone would have any suggestions.

Now I see that rexio has the same problem with the same motherboard. Interesting. Maybe something with the IDE controller?

---

### Post by rexio8 on 2005-10-28
I've found a solution! Flash the bios to a newer version (1019). And everything works just fine!

---

### Post by Casethejoint on 2005-10-28
Same problem for me with Hoary. 

I never got an answer about this issue beyond:

a) check MD5, and;
b) burn at a slower speed/with different burning software.

Didn't work. Disheartening to see it's still a live problem.

--Case.

---

### Post by AlexMartinius on 2005-10-28
Installing Hoary was no problem at all here. Last time I tried, the installer was quite slow, but the first time (about 5 months ago,I guess) it was pretty fast. I'll update my BIOS soon and try again.

---

### Post by lhazfarg on 2005-10-29
On my new Mobo the problem with not mounting CD was solved, after I unchecked "advanced Mode" for IDE Controller in Bios setting.

---

### Post by toujours on 2005-10-29
Just an update.

I've been running the AMD64 version for a few weeks, but I'm finding it somewhat disappointing (lack of common packages, like flash, realplayer, WINE, etc, need to rebuild stuff - without success), so I thought I'd reinstall the i386 version.

This time I used a different browser and different burning software.

I get the same problem when it comes to mounting the CD.

AFAIK, it's NOT a checksum problem, it's NOT a burner problem, so therefore it's an UBUNTU INSTALLER problem...

If I understand correctly, the ISOs won't be updated to correct problems like this, so I can kiss goodbye to decent usable (i386 and not AMD64) Ubuntu on my PC...

:( :( :( :( :(

---

### Post by AlexMartinius on 2005-10-30
[QUOTE=rexio8]I've found a solution! Flash the bios to a newer version (1019). And everything works just fine![/QUOTE]
Thanks! I'm typing this message in Ubuntu 5.10, it worked. :)

---

### Post by kingjonrules on 2005-11-03
[CENTER]I'm stuck too. I am putting 5.10 on a machine with no other OS.
I have a burned installer disk and the installer just stops when the CD recognition bar gets to 86%. I am miffed.
Jon
:confused: :confused: :confused:[/CENTER]

---

### Post by Dave_Man on 2006-01-28
Hi
i'm having the same problem.
I updated my bios to the newest version my board manufacturer has.. but its from 2004! so I don't know.. maybe I should get something newer from another source.
anyways.. have exactly this problem.

Another thread where I put more info is here:
[http://ubuntuforums.org/showthread.php?t=121972](http://ubuntuforums.org/showthread.php?t=121972)

any sugestion would be greatly appreciated.
its kinda digruntling to have the same problem without a solution almost a year after the previous guys!

thanks.
Dave.

---

### Post by stemar on 2006-01-28
[QUOTE=Dave_Man]Hi
i'm having the same problem.
I updated my bios to the newest version my board manufacturer has.. but its from 2004! so I don't know.. maybe I should get something newer from another source.
anyways.. have exactly this problem.

Another thread where I put more info is here:
[http://ubuntuforums.org/showthread.php?t=121972](http://ubuntuforums.org/showthread.php?t=121972)

any sugestion would be greatly appreciated.
its kinda digruntling to have the same problem without a solution almost a year after the previous guys!

thanks.
Dave.[/QUOTE]

I had this problem and solved it by changing the BIOS setting of the IDE Controller from AUTO to Enhanced.

If you have already tried this with out success, let me know the make/model of your motherboard.

---

### Post by Dave_Man on 2006-01-29
[QUOTE=stemar]I had this problem and solved it by changing the BIOS setting of the IDE Controller from AUTO to Enhanced.

If you have already tried this with out success, let me know the make/model of your motherboard.[/QUOTE]

thanks alot!
I didn't find any IDE controller setting so I just messed around with anything pertaining to IDE and finally found what was working..
I had to change a setting from legacy to native.
something to do with SATA/PATA setting.
but hey.. it worked..
thanks alot!
dave.

---

