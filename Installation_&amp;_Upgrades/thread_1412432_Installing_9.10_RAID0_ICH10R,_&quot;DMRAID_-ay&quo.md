---
title: "Installing 9.10 RAID0 ICH10R, &quot;DMRAID -ay&quot; fails to activate fakeraid."
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by Anhedonia on 2010-02-21
Hi All,

I havent really used linux much since about 6 years ago when i was playing with the server functions.

Ive searched and searched over these forums today and i think ive finally tried everything i can. Id like to avoid adding a forum post if i can but ive run out of steam.  :confused:

Im running 2x 500gb Seagate Sata drives. My motherboard is GA-EX58-UD5 with the latest f7 revised bios.

When i try to install from 9.10 DVD i386 i cant see my  ICH10R "fakeraid" As i would like this performance for my Vista x64 install i dont want to remove the "fakeraid".

So i goto the live CD and run "sudo dmraid -ay" and i get this error.

root@ubuntu:/dev# dmraid -ay
ERROR: isw device for volume "RAID" broken on /dev/sda in RAID set "isw_ccjcchchhd_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ccjcchchhd_RAID" [1/2] on /dev/sda
ERROR: isw device for volume "RAID" broken on /dev/sdb in RAID set "isw_ceebgdgjii_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ceebgdgjii_RAID" [1/2] on /dev/sdb
RAID set "isw_ccjcchchhd_RAID" was not activated
RAID set "isw_ceebgdgjii_RAID" was not activated

The way my drive is setup with the first RAID0 being 750GB , containing my Windows Vista x64 partition and a second larger 500gb storage partition.

The second "fakeraid" is setup as 180gb to contain my linux install.

Ive heard some people say without seemingly referring to individual circumstance "disable raid from your bios menu" , However as far as i know one boot like this and ive lost my Vista x64 partitions. Which would mean i would have to constantly change the setting?

Ive also tried deleting the 180gb RAID0_2 Stripe, however the ubiquity still wont see anything.

Thanks anyone for any tips you can give me, as im really looking forward to getting to know this distro :).

"sudo Dmraid -s" provides this response.

root@ubuntu:/dev# sudo dmraid -s
ERROR: isw device for volume "RAID" broken on /dev/sda in RAID set "isw_ccjcchchhd_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ccjcchchhd_RAID" [1/2] on /dev/sda
ERROR: isw device for volume "RAID" broken on /dev/sdb in RAID set "isw_ceebgdgjii_RAID"
ERROR: isw: wrong # of devices in RAID set "isw_ceebgdgjii_RAID" [1/2] on /dev/sdb
*** Group superset isw_ccjcchchhd
--> Subset
name   : isw_ccjcchchhd_RAID
size   : 976768256
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_ceebgdgjii
--> Subset
name   : isw_ceebgdgjii_RAID
size   : 976766208
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0




Mr Anhedonia.

---

### Post by darkod on 2010-02-21
I didn't understand how exactly you have your raid array set up. You would usually have only one array and then it's reported as single device onto which you create partitions and install the OSs.
Are you trying to use raid0 and raid1 sets?

Have you also tried using the alternate install cd? Sometimes it can work with raid better than the live cd. In fact, the alternate cd is recommended for RAID and/or LVM installs although on 9.10 the dmraid package is included on the live cd too. It wasn't on 9.04.

Even though the package is included, did you try running

sudo apt-get install -y dmraid

anyway? Maybe it will make a change.

PS. And I guess you've double checked the BIOS raid settings to make sure the array isn't actually broken right?

---

### Post by Anhedonia on 2010-02-21
Darkod> Thanks for the quick reply!
 
Ive setup two raid arrays, for no other reason then organization. I did image my Vista install so if having only one RAID0 array fixes the problem i can reimage, however id rather not try unless it definately will.
 
I tried the alternate install cd as well, unfortunately no luck there.
 
Ive double checked dmraid by uninstalling and reinstalling it then trying to "dmraid -ay" with the same result.
 
The intel fakeraid BIOS shows both the raid stripes as fully functional, and they are visible within the vista disk manager and also the intel matrix software.
 
When i shutdown/reboot the live cd or the installer, the intel fakeraid shows nothing, shutting down the main power then turning back on again fixes this.
 
Mr A.

---

### Post by darkod on 2010-02-21
Unfortunately, I don't have enough experience with raid to know if a single array can help at all. It might be something also related to the exact controller model/chipset.
I'm not sure what to try next because you're obviously doing the right steps. :)

---

### Post by Anhedonia on 2010-02-21
Yar i am following the right steps >.< lol.
 
As far as i know this model is fine with ubunutu for fakeraid.
 
A.

I gave up and wiped my vista install. However this is never solved.

---

