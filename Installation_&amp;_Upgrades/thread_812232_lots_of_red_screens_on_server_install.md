---
title: "lots of red screens on server install"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by 565Customz on 2008-05-29
i checked my disk and iso, and burned at x1 on a hardy OS

get lots of errors starting at 6% base sytem install starting with 

debootstrap warning
libslang2_2.1.3-2_i386.deb is corrupt
 
new box ---  *that ^ file*...couldnt be downloaded

followed by initscpritps, bsdutils_2, console terminus, sudo 1.6.9p10, tar/tar_1.19-3, taskel1.2.70, tzdata_2008b, upstart_0.3.9-2_i386, xkb-data_1.1.....each has its own error box and its own couldnt download warning.

then i get 

base system installation error (return value 1) 

check /var/log/syslog or see virtual console4 for the details


then i get 

base system install into /target/ failed
Install failed


and it goes back to the installer main menu...


it may have given a couple more screens but that is pretty much all of them..i hit the ok button to fast a couple of time...any ideas?  also this is the 6th disk from the 5th server and they have all done the same thing...

running a abit motherboard with th athalon 1800 processor ( i know right) new processor is coming lol

thanks guys

---

### Post by 565Customz on 2008-05-29
bump!! 
:popcorn:

---

### Post by prshah on 2008-05-30
> **565Customz said:**
> 
check /var/log/syslog or see virtual console4 for the details


Looks like a bad drive to me. Can you post the /var/log/syslog as suggested by the installer?

---

### Post by 565Customz on 2008-05-30
how am i going to do that? i have no os on the drive or anything

...its not the drive because i have three of them and two that i tried did the same thing. ( or are you talking about the cd drive???) im going to try unplugging all but the one big hd and reconfigure some stuff in the bios.

the two drives i tried are secondry master and secondary slave. the primary master (which doesnt have a slave) has windows pro on it and i want to leave it alone for my other computer im building.

also i tried my dvd reader writer which is the primary and it loaded form the disk,  but when it started installing it said the disk was missing. i put the disk in the secondary cd drive and i got that error.  should i make the secondary cd rom drive master and take the dvdrom out?

---

### Post by gdaddy on 2008-05-31
I have the exact same issue - also on Athlon 1800 - HP ML115

---

### Post by gdaddy on 2008-05-31
OK so I just downloaded a fresh copy, and retried install - works perfectly.

---

### Post by 565Customz on 2008-05-31
where did u download it....what server

---

