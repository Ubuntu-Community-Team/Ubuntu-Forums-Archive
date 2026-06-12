---
title: "Problems with CDROM while installing..."
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by Space.Clown on 2007-10-02
Hey everyone! I'm totally new to eveything Linux, but decided I would really like to try Ubuntu. I downloaded and burned Ubuntu Studio, and am working on installing it. I get up to 'Detecting Hardware to find CD-ROM drives', but then it can't find it or mount it or whatever. I have no clue what this means (I keep thinking, 'what do you mean you can't mount it!? You're running from it!!) or what to do about it. I did a search but couldn't find anything. Help would be greatly appreciated!!!

XOXO
~Malinda

---

### Post by Pumalite on 2007-10-02
What motherboard and BIOS do you have?

---

### Post by Space.Clown on 2007-10-02
I actually just got a new motherboard on Sunday. My dad installed it so I really don't know much about it, but the box reads: 

Biostar mainboard for intel processor
P4M890 chipset
P4M890-M7 SE
LGA775/FSB 1066MHz
SATA/RAID
PCI-Ex16/DDRII-533

Not sure what any of that means or if it is helpful...

Umm..what is the BIOS exactly? :confused:

XOXO
~Malinda

---

### Post by Pumalite on 2007-10-02
The BIOS might be the key in this situation. You access it at boot hitting: Esc or Tab or Del depending on the computer. There check that your CD drive is set to AHCI if Intel Motherboard. If you have a Raid Array, that might be a different headeache:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
(I noticed 'SATA/RAID')

---

### Post by Space.Clown on 2007-10-02
Okay, I just went and fiddled around with my computer in the other room. It seems to be set at 'auto detect' but there is no AHCI option, so that might not even be what you're referring to. Other than that, I can't find any other mention of the CD Drive, and I looked through everything in the BIOS. 

Thank you very much for taking the time to help me.

XOXO
~Malinda

---

### Post by Pumalite on 2007-10-02
If you have Auto but no AHCI that's also fine, but check if you have a feature such as IDE Cofiguration and check there too. Make sure you know if you have Raid or not.

---

### Post by Space.Clown on 2007-10-02
How will I know if I have RAID?

---

### Post by Pumalite on 2007-10-02
Usually at boot it shows up or you can access it with some key combination that is different for different motherboards. Consult your motherboard Manual.

---

### Post by Space.Clown on 2007-10-05
So I had a theory that I had a bad disk. After downloading and burning a few more copies from different sources, I finally got one that worked. I finished installing it a little bit ago. Unfortunatly, I ran into more problems. :( It got stuck at the loading screen for quite awhile, and then displayed this message:

```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty;job control turned off
```

I saw another post about this error, but it was for a liveCD and I didn't know if the answer to the problem would the same for an actual install. Plus I didn't understand any of the answers. :confused:

Help would be much appreciated,

XOXO
~Malinda

---

### Post by Pumalite on 2007-10-05
That's an error that seems to have as many causes as fixes. I'll give you a thread that you can review:

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

Some of the fixes include sticking a floppy in or an USB device. 

Good luck.

---

