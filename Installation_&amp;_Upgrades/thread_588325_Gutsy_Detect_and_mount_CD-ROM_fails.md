---
title: "Gutsy: Detect and mount CD-ROM fails"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Impotence on 2007-10-23
I am trying to install Gutsy on a Infinity 557c [i cant find alot about this laptop] with a gma-4082n DVD-RW

When trying to install from the live CD it fails to boot so i tried to install from the alternate cd (i386).

when the alternate installer gets to "Detect and mount CD-ROM" it fails stating:-

"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Try again to mount the CD-ROM?"

The cd is definitely in the drive ;) i check the md5 of the iso and the integrity check passes when done on a different computer (it fails to find the drive when i try to run the self check from the infinity laptop).

I have been trying to find anything for at least 3 hours now (google and searching the forums) with no luck whatsoever, any help or suggestions would be greatly appreciated.

[OT]
before anyone asks, i got my username from the back of a packet of fags
[/OT]

---

### Post by thirunavukkarasu on 2007-11-01
At boot prompt press F6 and add the following parameter: "all_generic_ide" to the kernel line. In some cases it may help

Rgds,
Thiru.S

---

### Post by Impotence on 2007-11-12
thanks for the reply,

i actually went the long way around and installed 7.04 and upgraded to 7.10 but i will try it anyway when i get a chance and post up what happend for anyone else who might come accross this :P

thanks again thirunavukkarasu

---

### Post by buccaneere on 2007-11-12
> **thirunavukkarasu said:**
> At boot prompt press F6 and add the following parameter: "all_generic_ide" to the kernel line. In some cases it may help

Rgds,
Thiru.S

How to do this for a beginner?

Thanks

---

