---
title: "ubuntu install help- new user"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by sleepydumbdude on 2007-03-07
I've been trying to install for the past 4 hours. I get to the point of Installing system and when it says Copying files... it gets to 26% and then goes nowhere. Its happened the past 4 times. Sometimes it freezes during loading linux kernel on the first screen but the copying 26% is the farthest I can get.

Its a P4 w 512 ram.. i forgot the other details of it, its a dell from a few years back..

Also if I try to do the check disc I get
[17179866.372000] hdc: timeout waiting for DMA
[17179871.376000] hdc: drive not ready for command

it just repeats that with different numbers

Should I redownload and burn a new disc or anyone know of an issue like this and how I can fix it.

---

### Post by Kateikyoushi on 2007-03-07
There is an option to check the disc, select it at the boot menu to try that first.

---

### Post by Sef on 2007-03-07
A few questions:

1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Have you checked the disk with the check disk option?

---

### Post by sleepydumbdude on 2007-03-07
I tried to check the disc and it just didn't do anything for awhile then I go 

Also if I try to do the check disc I get
[17179866.372000] hdc: timeout waiting for DMA
[17179871.376000] hdc: drive not ready for command

then some IO error

I burned with 4x
I forgot to do the md5sum but i just did it now and it says they are the same so thats ok

---

### Post by Kateikyoushi on 2007-03-07
Then try to disable DMA on that drive.

Boot from the cd at the menu press F6 then add this option to the end.

```
hdc=nodma
```

Or to disable DMA globally

```
ide=nodma
```

---

### Post by Vanye111 on 2007-03-07
> **sleepydumbdude said:**
> Should I redownload and burn a new disc or anyone know of an issue like this and how I can fix it.

I just installed for the first time last night (6.1) and had a similar issue when installing off the boot cd in my Pioneer DVD +/- RW  drive.  
I booted & installed off my other CD drive, and it installed fine. I have other issues, but it installed fine :)

---

### Post by sleepydumbdude on 2007-03-08
I burned a new disc using the exact methods it told me too and i get the same error. 
Question
On other forums I see that some people say something about the alternate install CD, should I try that method?
I'm downloading it now but its going to be like 2 hours til i'm finished, think I'm just wasting my time?

---

### Post by Kateikyoushi on 2007-03-08
Yes, the alternate cd installs in text mode and has a higher chance to set up a minimal system on your machine.

---

