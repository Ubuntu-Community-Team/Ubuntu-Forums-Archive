---
title: "Hardy Heron/Crunchbang Linux dual install"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2009-12-11
I just got a IBM Thinkpad 600X from a friend who doesn't need it anymore. It has Windows XP Pro on it. I'm pretty sure an older version of Ubuntu would run fine on it. I did take it for a test run with 8.04 and Crunchbang yesterday and they both ran fine.

Now. I'm currently installing 8.04 and am wondering if Crunchbang could share swap space???

If anyone has done something similar I'd appreciate a hand here?

TIA.

---

### Post by raymondh on 2009-12-11
> **emeraldgirl08 said:**
> I just got a IBM Thinkpad 600X from a friend who doesn't need it anymore. It has Windows XP Pro on it. I'm pretty sure an older version of Ubuntu would run fine on it. I did take it for a test run with 8.04 and Crunchbang yesterday and they both ran fine.

Now. I'm currently installing 8.04 and am wondering if Crunchbang could share swap space???

If anyone has done something similar I'd appreciate a hand here?

TIA.

Yes on swap.

Check the BIOS vintage.  Older BIOS' could only boot so much into an HD.  I think on pre-1998, the limit was 8GB.  Early 2000's, the limit was 136GB.  Beyond those you risk the ERROR 18.  

If you have the pre-98 and are limited to the 8GB .... the idea is to either install a /boot partition (about 100mb) in front of the drive or ..... install the OS within the 1st 8GB of the drive.  As for dual-boot, you may want to consider then a /boot partition.  Of course, all these is moot if your IBM BIOS vintage is of recent.

Regards,

---

### Post by emeraldgirl08 on 2009-12-11
Okay. 

My BIOS date is 1999. I'll try this anyway and if it gives me an error I'll throw my Windoze HD back in and do the flash.

So I have a RAM of 318. What size would be sufficient for SWAP? I will be increasing the RAM to it's 578MB max soon. I'm thinking I should make swap at least 620??? Would that work?

---

### Post by raymondh on 2009-12-11
> **emeraldgirl08 said:**
> Okay. 

My BIOS date is 1999. I'll try this anyway and if it gives me an error I'll throw my Windoze HD back in and do the flash.

So I have a RAM of 318. What size would be sufficient for SWAP? I will be increasing the RAM to it's 578MB max soon. I'm thinking I should make swap at least 620??? Would that work?

If you have the space to give-up, why not round-off swap to 1GB?  My rule on swap is 1.5X the amount of max installable RAM.  Again, this all depends on your hibernation and app-usage habits hence my suggestion to just round-it off to 1GB if you have the space to give.

You may want to reference read a /boot install.  Here, let's use Herman's site:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Regards,

---

### Post by emeraldgirl08 on 2009-12-11
It came with a 20gb 4200rpm Traveltortoise :P

I have an extra Western Digital 80gb 5400rpm here among my comp parts to spare. So I've allocated around lower 20gb to Heron. Separate / and /home. I also am going to do the same thing with Crunchbang. 

I hate to use up all the diskspace on HDD. You never know when I may need the extra space. Besides Dad isn't going to be downloading huge files anyway. He'll probably just be doing web browsing and wordprocessor.

I did double the max RAM the 600X can take. I've been looking on ebay for him and will get the RAM soon.

Thanks for the help Raymond. I'm installing right now so we'll see how this goes :)

Hmmm...wonder how big the updates are going to be :p

---

### Post by raymondh on 2009-12-11
> **emeraldgirl08 said:**
> It came with a 20gb 4200rpm Traveltortoise :P

I have an extra Western Digital 80gb 5400rpm here among my comp parts to spare. So I've allocated around lower 20gb to Heron. Separate / and /home. I also am going to do the same thing with Crunchbang. 

I hate to use up all the diskspace on HDD. You never know when I may need the extra space. Besides Dad isn't going to be downloading huge files anyway. He'll probably just be doing web browsing and wordprocessor.

I did double the max RAM the 600X can take. I've been looking on ebay for him and will get the RAM soon.

Thanks for the help Raymond. I'm installing right now so we'll see how this goes :)

Hmmm...wonder how big the updates are going to be :p

You're welcome.  Just remember (if you decide not to flash) if you get the error 18, you'll need to install root (/) within the 1st 8GB.  If you do plan to dual boot, consider a separate /boot instead.

I like crunchbang and Hardy.  I still am running those distro's / versions.  Coincidentally, I just finished right now installing MASONUX on a P3, 768MB RAM, 1997 vintage desktop for my  6 yr. old daughter.  Runs speedy .... and in some ways, more responsive that crunch.

Good luck ... happy ubuntu-ing.

---

### Post by emeraldgirl08 on 2009-12-12
Okay. I don't know whether or not I need to flash my BIOS. This is what I got after installing both OS'. I automatically get logged into Ubuntu. No Grub shows up to offer a choice.

_My menu.lst:_

```
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=030be7b3-57af-46de-9956-e69246f09aa2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=030be7b3-57af-46de-9956-e69246f09aa2 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=030be7b3-57af-46de-9956-e69246f09aa2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=030be7b3-57af-46de-9956-e69246f09aa2 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Note: There is no Crunchbang anywhere in that ^^^ Even after running sudo grub-update.

_My fdisk results:_

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x000b0a5a 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        1304    10474348+  83  Linux 
/dev/sda2            1305        2608    10474380   83  Linux 
/dev/sda3            2609        2748     1124550   82  Linux swap / Solaris 
/dev/sda4            2749        5356    20948760    5  Extended 
/dev/sda5            2749        4052    10474348+  83  Linux 
/dev/sda6            4053        5356    10474348+  83  Linux 

Disk /dev/sdb: 3999 MB, 3999793152 bytes 
98 heads, 33 sectors/track, 2415 cylinders 
Units = cylinders of 3234 * 512 = 1655808 bytes 
Disk identifier: 0x52a8513c 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               3        2416     3901952    b  W95 FAT32 
```

Anything look suspect in this? sdb1 is a flash drive.

---

### Post by snowpine on 2009-12-12
Did you use ext3 or ext4 for CrunchBang? Ubuntu 8.04 cannot "see" ext4.

---

### Post by emeraldgirl08 on 2009-12-12
> **snowpine said:**
> Did you use ext3 or ext4 for CrunchBang? Ubuntu 8.04 cannot "see" ext4.

used ext3 for both Ubuntu and Crunchbang.

---

### Post by raymondh on 2009-12-12
Also ...., you can try chainloading crunch

title       Crunchbang
root        (hd0,4)
chainloader    +1

That is if Crunch's root is in sda5.

---

### Post by emeraldgirl08 on 2009-12-12
> **raymondh said:**
> Also ...., you can try chainloading crunch

title       Crunchbang
root        (hd0,4)
chainloader    +1

That is if Crunch's root is in sda5.

Good morning Raymond :)

Yes the / is in sda5.

I'll give that a try.

---

### Post by raymondh on 2009-12-12
> **emeraldgirl08 said:**
> Good morning Raymond :)

Yes the / is in sda5.

I'll give that a try.

Just a side note before signing out and heading off to work .... I used to love in ahwatukee (beneath the radar mountain) area.  Good morning as well.

Will catch this thread this evening.

---

### Post by emeraldgirl08 on 2009-12-12
adding the chainloader didn't help.

Actually it won't go into Grub at all on startup. It get's ACPI forced and boots right to the sign in screen for Ubuntu.

It does mention something about BIOS and 1999. It also shows something about 2000. I'm thinking that the BIOS needs to be upgraded to something more recent than 1999. There is a BIOS upgrade that I have for the 600X. 

Only problem is you need a working battery to flash :oops: My battery is essentially dead. I was hoping there was a way to force the flash but am a little squeamish on doing that.

I'm just glad that Ubuntu at least starts up. I was teaching my dad how to use somethings on it. It has a Wireless B PCMCIA card that won't work with our router encryption. My dad is going to buy a G card next week so I can set him up with Pidgin and familiarity with Seamonkey. Seamonkey seems spunkier than Firefox.

---

### Post by raymondh on 2009-12-12
> **emeraldgirl08 said:**
> adding the chainloader didn't help.

Actually it won't go into Grub at all on startup. It get's ACPI forced and boots right to the sign in screen for Ubuntu.

It does mention something about BIOS and 1999. It also shows something about 2000. I'm thinking that the BIOS needs to be upgraded to something more recent than 1999. There is a BIOS upgrade that I have for the 600X. 

Only problem is you need a working battery to flash :oops: My battery is essentially dead. I was hoping there was a way to force the flash but am a little squeamish on doing that.

I'm just glad that Ubuntu at least starts up. I was teaching my dad how to use somethings on it. It has a Wireless B PCMCIA card that won't work with our router encryption. My dad is going to buy a G card next week so I can set him up with Pidgin and familiarity with Seamonkey. Seamonkey seems spunkier than Firefox.

I'm thinking BIOS won't go that far into the new HD.  But, you would've received an error 18 if you pushed it.

Is it still open for experimenting or has you dad already taken hold of the machine?  ***I've never tried this but who knows*** ....

The idea is to have both root (hardy and crunch) within the first 8GB

-  use same partitions
-  mount hardy root in sda1
-  mount hardy /home in sda5
-  mount crunch root in sda2
-  mount crunch /home in sda6

Of course, you can also separate /boot (250mb should be OK) and put that ahead of everything.  See Herman's tutorial.

Also, I apologize for the ahwatukee side note.  I used to live in PHX, in the ahwatukee area.  When I saw SW arizona in your sig, PHX just came into mind.  Oh well, no coffee yet during that moment to clear up the mind.

---

### Post by emeraldgirl08 on 2009-12-12
Don't worry about the Ahwahtukee sidenote :D

I live in the northern part of the state but have lived down south for awhile. Have relatives down that way also.

I'm thinking it is the BIOS bc from what I see the forced ACPI mode is for BIOS versions before 2000. Mine is 1999. The more recent version is from 2001.

I'll be back with more reliable information. I have some ppl I know for sure have an answer on 600X and their HDD capacities. I just got done installing internal Wifi into the 600X. The antennae was a just a little time consuming to install :P

---

### Post by emeraldgirl08 on 2009-12-15
Okay.

A little update. I found that the Crunch / and /home were in extensions. I am not too sure if that is the reason why crunchbang was not able to mount. I deleted the crunchbang partitions and am now going to post a screenshot of my current setup using a Jaunty LiveCD.

I should also mention that the error I was receiving while at GRUB menu was an Error 12 for people who may be reading my thread.

---

