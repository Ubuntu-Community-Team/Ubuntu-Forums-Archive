---
title: "Karmic installer doesn't see my SATA HDD"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lucretius on 2009-10-23
The Jaunty installer does not see my SATA hard drive. When I get to the step where the partition manager runs, it comes back with no results. There is just a blank menu (running alternate install CD)

Here are my system specs

AMD athlon 3000xp
MSI K7N2 Delta Motherboard
1TB hitachi sata HDD
1Gb ddr 333 ram
256mb nvidia 7600gt

The motherboard has a built in Promise 376/378 sata controller

When using the desktop live cd the drive is recognized but I still can't install to it... it crashes with a ubiquity error.

I have managed to install jaunty on this machine... so I cant see why karmic wont play nice.

---

### Post by earthpigg on 2009-10-23
have you tried the alternate install cd?

---

### Post by Lucretius on 2009-10-23
yes... this is where the problem shows up...

there is just a blank screen with

"undo partitioning changes"
"finish partitioning and write changes to disk"

nothing more

this is after "activating sata devices"

---

### Post by Lucretius on 2009-10-23
just tried the jaunty alternate cd... it does not see my drive either..

going to try intrepid now

---

### Post by Lucretius on 2009-10-23
okay... i've tried a different sata drive after having no luck with 3 previous ubuntu distro's 

It worked first time... wtf

so thinking my drive was a duff I tried it in a windows machine as an external..

windows recognised it first time and everything on it.

So I have a drive I can access and use via eSATA... but can't install ubuntu to as it can't see it

not sure what to do... is this possibly a problem with the drive still? it's not very old.

---

### Post by earthpigg on 2009-10-23
since it works with Windows, one way to rule out this possibly being a linux problem would be to use Unix.

[http://en.wikipedia.org/wiki/Pcbsd](http://en.wikipedia.org/wiki/Pcbsd)

---

### Post by Lucretius on 2009-10-23
I think it might be a problem with my promise controller...

windows will not install and I tried 2 sepertate sata drives with the same results..

it does not see the drive capacity. and wont boot from it.

---

