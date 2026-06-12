---
title: "I can't install ubuntu"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by SaToNiO on 2006-11-08
i want to install ubuntu or kubuntu but i can't. with vmware it works but when i try to use the cds directly i can't. ubuntu can't mount the installation cd-rom. why? with vmware works perfectly

how can i install it?

i have:
kubuntu 6.06 livecd (i installed it with vmware)
ubuntu 6.06 livecd (i installed it with vmware too)
ubuntu 6.10 alternate (i checked third step ends correctly)

with the first two cds i got i/o errors when livecd is loading, the errors appeared after Uncompresing Linux... Booting the kernel. with the alternate cd i got the error 'No se pudo montar el cd-rom de instalación', that means that it couldn't mount the installation cd-rom.

why have i to do to install ubuntu?

sorry, my english isn't very good.

---

### Post by SaToNiO on 2006-11-09
no ideas??

---

### Post by bulldog on 2006-11-09
You have to boot from cd to install Ubuntu.

So you have to set your cd-rom as first boot device in your BIOS
Then restart your computer with the live cd or the alternate cd in your player.
Then boot the cd and install Ubuntu.
There's nothing to mount.

---

### Post by SaToNiO on 2006-11-10
it isn't true... i have cd as first botting device... that isn't the problem... now, with DVD ubuntu 6.10 Desktop, i deleted splash from param list and i got:

[17179572.556000] ACPI: Getting cpuindex for acpiid 0x1
[17179638.780000] Buffer I/O error on device hdb, logical block 0
[17179701.100000] Buffer I/O error on device hdb, logical block 1
[17179763.420000] Buffer I/O error on device hdb, logical block 2
[17179825.736000] Buffer I/O error on device hdb, logical block 3
[17179888.056000] Buffer I/O error on device hdb, logical block 4

that data was written by me to a paper and then wrote, so it can have errors.

More ideas??

---

### Post by justin whitaker on 2006-11-10
You know, I've never done an install in Spanish. Did you try something as simple as installing in English?

Also: did your CDs and DVDs check?
Also: did you try 6.06.1 Alternate?

---

### Post by SaToNiO on 2006-11-10
with Desktop i tried to use live in spanish but it doesn't work, all as spanish.

cd check doesn't work. it appears the same as using the first option (start or install ubuntu) with splash.

why to use 6.06.1 alternate??

---

### Post by SaToNiO on 2006-11-10
nothing?? :(:(

---

### Post by SaToNiO on 2006-11-10
i need help :(

---

### Post by bulldog on 2006-11-10
Yes you do but what can we say?

If you boot from the live cd you've got errors,but installing in vmware is going well.

It should indicate there's some kind of error with your hardware when you try booting the live cd.

Have you the possibility to try another cd-rom player?
I can't be of more help to you,I'm sorry.

---

### Post by SaToNiO on 2006-11-11
no, i can't

---

### Post by wpshooter on 2006-11-11
Have you tried cleaning your CD drive ?

---

### Post by SaToNiO on 2006-11-11
how can i do that?

---

### Post by lofgren on 2006-11-11
You can by a cd that you use which cleans the optics of your CD rom drive.

So, you are using the same machine to boot the live CD with?
If it is in a VMware session it works, but if you boot it from power on, it fails?

That's weird and doesn't make sense :(

---

### Post by lofgren on 2006-11-11
> **SaToNiO said:**
> 
why to use 6.06.1 alternate??

Alternate uses a text-based installer.

I guess we'd also hope and assume that the 6.06.1 is slightly more up to date than the 6.06 installer - therefore works on more hardware and overcomes issues or bugs that the 6.06 installer might have had.

---

### Post by SaToNiO on 2006-11-12
it's the same machine, lofgren.

but i can't start that installer with livecd, it stops at 'mounting root file system', and then i got those i/o errors.

with 6.10 alternate cd it stops mounting installation cd-rom, o i think it's the same problem, and if it isn't fixed in 6.10 i think that in 6.06.1 isn't fixed. I don't want to download & burn more cds because i think it won't work.

sorry but i haven't said the true versions i have, i have checked the cds and the versions and i have:

Ubuntu 6.06.1 "Dapper Drake" - Release i386 <- desktop
Kubuntu 6.06.1 "Dapper Drake" - Release i386 <- desktop
Ubuntu 6.10 "Edgy Eft" - Release i386 <- that disk is alternate, not desktop
Ubuntu 6.10 "Edgy Eft" - Release i386 <- desktop dvd.

---

### Post by bulldog on 2006-11-12
Is your computer stable in daily use?
Because you get this weird i/o errors when you boot from cd.

Do you have another flat-cable,the one which connects your cd-rom player with the motherboard?

You can even try to connect your cd-rom player to another port on the motherboard to see if it helps.   

My first reaction would be faulty RAM,but than again you should have more trouble.

---

### Post by SaToNiO on 2006-11-12
I think that pc is the most stable i have ever used.  I will try to re-connect the cd-rom to another port (if i find it) tomorrow. i don't know if i have more flat-cable.

---

### Post by dorath on 2006-11-12
> **SaToNiO said:**
> it isn't true... i have cd as first botting device... that isn't the problem... now, with DVD ubuntu 6.10 Desktop, i deleted splash from param list and i got:

[17179572.556000] ACPI: Getting cpuindex for acpiid 0x1
[17179638.780000] Buffer I/O error on device hdb, logical block 0
[17179701.100000] Buffer I/O error on device hdb, logical block 1
[17179763.420000] Buffer I/O error on device hdb, logical block 2
[17179825.736000] Buffer I/O error on device hdb, logical block 3
[17179888.056000] Buffer I/O error on device hdb, logical block 4

that data was written by me to a paper and then wrote, so it can have errors.

More ideas??

I'm getting the same type of error, but on hdc and different logical blocks.  The optical drive works fine in XP, but the HDD is new so I'm running some diagnostics on it.

---

### Post by lofgren on 2006-11-12
Is it an old(er) CD/DVD rom drive?

I found posters with similar issues here: [http://ubuntuforums.org/showthread.php?t=201086](http://ubuntuforums.org/showthread.php?t=201086)

One person got around it by burning at the lowest speed possible.

As for the Vmware working.. my best guess is that it uses an emulator that has a greater tolerance for the errors you are receiving - ie: longer timeouts on reads etc, OR, it "buffers" in the virtual device, rather than using the CD/DVD's hardware?!

---

### Post by SaToNiO on 2006-11-13
> **lofgren said:**
> Is it an old(er) CD/DVD rom drive?

I found posters with similar issues here: [http://ubuntuforums.org/showthread.php?t=201086](http://ubuntuforums.org/showthread.php?t=201086)

One person got around it by burning at the lowest speed possible.

As for the Vmware working.. my best guess is that it uses an emulator that has a greater tolerance for the errors you are receiving - ie: longer timeouts on reads etc, OR, it "buffers" in the virtual device, rather than using the CD/DVD's hardware?!

logical blocks in that problems are much higher than mines. One of my disks was burnt at lowest speed (2x) (dvd) and the problem persist.

The errors I posted here were shown very slow, from first to last more than five minutes passed. and there are only 5 logical blocks, so i think longer timeouts on reads aren't.

---

### Post by lofgren on 2006-11-13
How about burning a CD at 2x?

---

### Post by doobit on 2006-11-13
I really recommend using the alternate install CD in text install mode (not OEM). It works in most instances where the live CD install will not.

---

### Post by SaToNiO on 2006-11-13
i also have alternate cd (6.10) and it doesn't work, it appeared an error mounting installation cd-rom after a while after selecting the keyboard type.

---

### Post by juantovarm on 2006-11-13
I suggest you install 6.06 alternate cd in text mode. It doesn't take too long to download, about 3 hours (broadband). cd's are cheap. There have been many posts about 6.10 installation problems, so stick to 6.06. I have installed Ubuntu, Xubuntu and Kubuntu on quite a few machines and when the live cd doesn't work, the alternate does.

Juan

---

### Post by CarolynR on 2006-11-13
I am a new user and just received the 6.06.01 by mail. I put it in an emachine 400i that I only have dos access to and had the same error showing on my screen:  


Buffer I/O error on device hdc, logical block 0 

Busy Box v1.01 (debian 1:1.01-4ubuntu3) Built-in shell (ash) Enter "help" for list of built in comands.

bin/sh can't access tty: job control turned off

---

### Post by drtvasudevan on 2006-11-14
> **CarolynR said:**
> I am a new user .....

bin/sh can't access tty: job control turned off

joining the club
;) 
my system has dualcore duo processor and 965 intel chipset.
there is a problem with this config and there is a separate wiki keeping track of it.
just from curiosity i tried the live cd.
i get this msg : bin/sh can't access tty: job control turned off

it is so with ubuntu kubuntu 64 bit version of these two.
the alternate cd starts ok but ends up not detecting the cdrom

well waiting till things are fixed......

---

### Post by juantovarm on 2006-11-14
CarolynR, did you receive the live install cd or the alternate cd? Sometimes the live cd encounters some problems...If you haven't tried with the alternate, i suggest you do just that. Download it, burn an iso image and run it in text mode not oem
Hope it helps

---

### Post by CarolynR on 2006-11-14
Thanks, I did receive the live CD and by reading posted threads,  thought I would try the alternate CD download. I assume it is in the downloads. Thanks for your help.

---

### Post by lofgren on 2006-11-15
> **CarolynR said:**
> Thanks, I did receive the live CD and by reading posted threads,  thought I would try the alternate CD download. I assume it is in the downloads. Thanks for your help.

Don't forget to check if your ISP has a local mirror - mine did! :)
Saved heaps of bandwidth and my quota.

SaToNiO - any progress?

---

### Post by SaToNiO on 2006-11-15
yes, now the grey connector on ide cable don't work. or at least i can't connect it correctly... and the black works ok, because if i connect the black on the cd-rom it works (the cd-rom drive and not ubuntu). tomorrow i will buy a new flat cable because i think i had broken that one.

I have also donwloaded 6.06.1 alternate and it doesn't work (i have tested it before breaking the ide cable).

no more ideas?

---

### Post by bulldog on 2006-11-15
You must have your hardware fully functional,than try again.
We all want to help but if your hardware is failing we can't.

---

### Post by SaToNiO on 2006-11-15
my hardware was fully functional two or three hours ago.

---

### Post by lofgren on 2006-11-16
> **SaToNiO said:**
> 
I have also donwloaded 6.06.1 alternate and it doesn't work (i have tested it before breaking the ide cable).
no more ideas?

Did you burn the iso to CD and at what speed?

I haven't seen the error myself, but searching for it turned up a lot of info suggesting it was hardware related. Burning at the slowest speed possible and or replacing older drives has worked for the others.

---

### Post by SaToNiO on 2006-11-16
problem solved!!! after breaking the ide cable yesterday, i bought a new one and ubuntu works!!!

thank you all for helping me!!

---

### Post by bulldog on 2006-11-16
Yeah,nice to hear you solved your problem.

Now install and let us know how it goes.:D

---

### Post by SaToNiO on 2006-11-16
now is copying files 60% :)

---

### Post by SaToNiO on 2006-11-16
is working ok :)

thank you all

---

### Post by lofgren on 2006-11-17
Excellent - enjoy

---

