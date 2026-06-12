---
title: "Ubuntu 8.04 installation issue on Dell Optiplex 320"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by snthelion on 2008-07-13
Hi all
I am very new toe Ubuntu, have successfully installed ubuntu on 2 of my older machines

Dell poweredge rack server - 7-8 years old, works great
Dell Dimension tower desktop - 3-4 years old, celeron, 1gb ram
Both have PS/2 mouse and keyboard, and IDE drives.

I had no issues with both installations, then I wanted to put ubunty on my 3rd machine  Dell Optiplex 320, Pentium 4, 2 GB RAM, NO PS/2 ports just have USB mouse and keyboard, and has SATA disk drives. 

When i pop in the Ubuntu install cd (Desktop, both alternate and normal versions) it lets me select the language and after that it just hangs on blank screen. 

I looked thru many forum posts, removed the "quite" option (using F6) and added "pci=nomsi all_generic_ide" and some other "noacpi nolapic nodma all_generic_ide" and a combination of these. 

No matter what I do, I can't get beyond 
pnp: no ps/2 controller found

And it just hangs after that. 

I see that many folks have similar issues, but have not found a good response with a solution yet. 

Any help would be greatly appreciated.

---

### Post by VMC on 2008-07-13
> I had no issues with both installations, then I wanted to put ubunty on my 3rd machine Dell Optiplex 320, Pentium 4, 2 GB RAM, NO PS/2 ports just have USB mouse and keyboard, and has SATA disk drives.
Are all your drives SATA, including the dvd rom drive?

I have seen reports of trouble using dvd rom sata drives.

I have a Opliplex GX-270, with no problems. I do have IDE dvd rom drive though.

---

### Post by snthelion on 2008-07-13
The DVD drive is IDE, the harddrives are SATA.
As I said have successfully insatlled ubuntu on IDE and the issue is my optiplex 320 with SATA disks.

---

