---
title: "Ubuntu dvd burner"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by rich79 on 2008-01-05
Hello,

I have a dvd burner samsung. 

on ubuntu 7.04 it works fine. on ubuntu 7.10 not. 

Can not burn and can not read from it. 

what may I do??

I have only one cd rom. it is master. I change IDE to secondary no good.

thank you in advance,
Ohad

---

### Post by PmDematagoda on 2008-01-05
Post the result of:-
```
cat /etc/fstab
```

---

### Post by mc4man on 2008-01-05
I checked back on your other post to see if you dmesg from live cd and  noticed you 
> I changed the ide slot to secondary place and changed the jumper on the dvd burner. 
I'm assuming that prior to this current problem you never messed with the cable, jumper setups, ect. so I'd put it back to the way you found it. Wouldn't hurt to describe your setup anyway.
In all likelihood you _had_/ will have 2 ide ribbon cables coming from motherboard - 1 (from primary ide) to hard drive connected with last terminator on cable and a 2nd (from secondary ide ) connecting to your samsung - again with last terminator (master position). If so set the jumper back to master.
i don't know enough to decipher dmesg except for the obvious though seeing your cd/dvd -rom at hda doesn't look right, and an earlier post in that thread
> Unable to mount the selected volume.
mount: special device /dev/hda does not exist 
you should follow thru and let PmDematagoda help you, if it was me I'd boot up the 7.04 cd , install feisty, burn a gutsy live cd, and do a fresh gutsy install

---

