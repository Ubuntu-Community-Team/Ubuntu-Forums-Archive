---
title: "windows reinstallation on a linux machine?"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by killer62491 on 2010-10-01
i didn't realize how much trouble my laptop would give me w/o being dual booted with windows XP, and now i've finally decided to reinstall windows on a separate partition, which i have yet to create. the reason i 'need' a separate windows partition is to contain and play my games on, which WINE is acting up on me worse and worse with each new release... hence my reason for two partitions being necessary. im positive i want to use a windows partition for all my games, while keeping my work on the ubuntu partition, crazy though it seems, with all those good fps/WINE-runnable (actual ones that work) MMO's. although i do have enough data space for probably just barely the few good open-source games i actually like. anyone have any ideas on how to *repartition* my already fully partitioned ubuntu HD, without needing to format, which will, of course delete all of the ubuntu contents? i have seen talk of a program called GParted, but haven't ever used it, so i'll look into that for a bit.
thanks beforehand ubucrew!

---

### Post by sikander3786 on 2010-10-01
Post the output of

```

df -h

```

for a better idea of your disk space and partition setup.

---

### Post by killer62491 on 2010-10-01
heresthe output, and i've never used close to half of the whole darned thing...
austin@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   31G   72G  31% /
none                  371M  280K  370M   1% /dev
none                  375M  240K  375M   1% /dev/shm
none                  375M  188K  375M   1% /var/run
none                  375M     0  375M   0% /var/lock
none                  375M     0  375M   0% /lib/init/rw
none                  108G   31G   72G  31% /var/lib/ureadahead/debugfs

---

### Post by sikander3786 on 2010-10-01
Boot into an Ubuntu Live CD, use gparted to shrink the "/" partition and free up some space for Windows. Create a new NTFS partition in the freed up space. Install Windows in it and then restore Grub2 for dual booting. See point # 13 in this how-to.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This will also help.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by killer62491 on 2010-10-01
where is gparted? will it be in the booted .iso, or outside of it? and is it simpler to just simply run it via terminal once booted?
just for easier reference once i'm done, also so i can more easily hide little things from certain people who shouldn't even know about said 'little things'.....
also, what do i do once gparted is active in order to "shrink" the "/" partition?

---

### Post by sikander3786 on 2010-10-01
It is present in the live CD. You can type gparted in a terminal or by pulling up the Run Application dialog by using Alt + F2 and typing in it. It also appears under Applications > Accessories I think.

I couldn't understand 'little things' statement. What did you mean by that?

You'll see the options to shrink the partitions as in any other partitioning software.

---

### Post by killer62491 on 2010-10-01
that statement was a test... the fact you noticed means you're a candidate for a neuro-atypical diagnosis. just something to start a conversation, i guess...
enjoy that little tidbit while i get this rolling.

---

### Post by sikander3786 on 2010-10-01
neuro-atypical diagnosis? Whats that? I think I should Google it :-)

---

### Post by killer62491 on 2010-10-07
a neuro-atypical diagnosis is a less biased way of saying "autistic"... which in a sense i am a "high-functioning autistic", meaning i can function as well as a neuro-typical person, yet i still display many attributes of the autism spectrum of disorders. its an interesting thing... especially seeing as how almost everyone in modern society could be considered a high-functioning autistic in some way or another...

p.s. sorry i didnt post back on that right away. got caught up in the work i do, and ended up being very involved in it for the last few days. feel free to post back whenever, as i always check up on old posts within the forums here.

---

