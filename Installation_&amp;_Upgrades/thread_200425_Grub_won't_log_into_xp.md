---
title: "Grub won't log into xp"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by thaive on 2006-06-20
Greetings, i'm affraid i'm in a bit of a pickle.

Today i downlaoded ubuntu 6.06 and installed in on a clean hardrive and it worked fine, but i wanted to duel boot with my other hardrive which had windows installed, as it was disconencted when i did the initial install i simply reinstalled ubuntu again.

When i reinstalled ubuntu i had the windows hd set as the master and ubuntu hd set as the slave, after that installed fine it went through the normal reset but now gives me an error.

it trys to run grub 1.5
but comes up with error 21

i then changed windows to be the slave and for ubuntu to be the master and reinstalled ubuntu again.

now when i have both hardrives plugged in i get the grub loader and am able to log into ubuntu fine, but when i select the windows xp professional i get the following:

booting windows professional
root (hd1,0)
Error 21. Select disk does not exist.

and now i'm stuff - the windows hardrive does exist, it has all my current work on it and i can't afford to lose it - this is my first time using and other os and it was going really good this morning until this happened.

if anyone could walk me though (prefereably holding my hand) about how i might fix this that would be really great.

cheers
thaive

---

### Post by pellgarlic on 2006-06-20
for a start, i'm pretty sure windows will want to be on the "master" channel, so i would switch it back to that for starters...

you should also double-check that both hard drives are detected in the bios.

---

### Post by thaive on 2006-06-20
ok, basically i kep reading mor and ended up using a windows bootdisk to fixmbr, so now i windows loads :)

now i will be doing another instal of ubuntu - any suggestions this time on how i sohuld do that, who should be th master and who should be the slave? 

i know it was a silly mistake by me but i'ld rather not let it happen again - any comments are most welcome.

---

### Post by rcarring on 2006-06-20
Windows should be on the first hard disk and made Primary.

Ubuntu can be on any other disk, probably better to have it on a separate physical hard disk.

It's better to have the second hard disk as slave to the master disk than slave to the cd/dvd -rom.

---

