---
title: "Win7 dual boot - does not detect main hard drive!"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by winter123 on 2010-02-23
A few weeks back I was trying to install this (alongside windows 7) and no matter what I tried it would not install. I tried both 9.04 32 bit and 9.10 64 bit. Each screen (language, keyboard, etc) took about 20 minutes to load, and when I finally got to the install it always stopped at about 2/3 percent, giving some type of I/O error. No matter how many times i reburned and redownloaded. (old [thread]("http://ubuntuforums.org/showthread.php?p=8780310#post8780310") if you're curious)

I eventually gave up but then realized I had an old xbox hard drive hooked up that I cannot boot or read or do anything. It was set as hard drive 0 in windows hard drive manager or whatever. So I unplugged it. Now my windows drive is drive 0, and I have a second internal drive.

I finally got back to installing this. I avoided the graphical installer at first because it was so slow, opting for the alternate cd. It went fast but when I tried to partition it was unclear to me which disk i was partitioning. Doesnt matter because when i clicked ok, it froze at 0% for 30 minutes so i had to do a hard restart. Windows ran the disk check, etc, etc, I checked the disk management in windows and it was just a single windows partition as it should be.


So I tried the graphical cd again instead. It goes really fast through the screens now, HOWEVER it will not detect my drive 0 windows drive! Just my second internal drive which of course I can't install on without wiping the entire thing. I have installed kubuntu 9.04 dual booted with windows xp on this exact hard drive, over a year ago successfully, so I don't get it. What do i do??

---

### Post by winter123 on 2010-02-23
I read on another thread that i should check my bios settings. I changed something like SATA ide, i dont remember, but all i got was a grub prompt when i restarted. Sooo I booted the BIOS again and clicked "restore fail safe settings". It fixed it. I tried the kubuntu disk again, clicked install, and instead it gave me lines of text with percentages and what it was doing. It showed two errors "[   75.something] end_request: i/o error, dev fd0, sector 0" and "[   87.something] end_request: i/o error, dev fd0, sector 0". And then it booted the live cd, I clicked install, and it still can't find my HDD.

 I have a linux test tomorrow so i wanted to get the thing installed but it looks liike that's not gonna happen. I really should not be dicking around like this so I'd really appreciate any help you can give!

---

### Post by wilee-nilee on 2010-02-23
Did you shrink W7 with the W7 disk manager leaving a open space for Ubuntu to format. Sorry if I haven't read all the information and you have addressed this.

---

### Post by winter123 on 2010-02-23
> **wilee-nilee said:**
> Did you shrink W7 with the W7 disk manager leaving a open space for Ubuntu to format. Sorry if I haven't read all the information and you have addressed this.

I was going to do this... however it doesn't seem necessary as the graphical installer does this for you. If you think shrinking windows 7 would make the installer recognize my hard drive I will do it, but it makes no sense to me why that would help.

Drive shows up in windows 7 disk manager, shows up in bios, but install disk just can't detect it. Very frustrating.

EDIT: Oh, fd0 is a floppy drive, so that should have nothing to do with my issue... I will disable it in the bios at next restart anyway, never plan on putting a floppy drive in here.

---

### Post by winter123 on 2010-02-23
Tried the alt 9.10 x64 cd again. I chose manual disk partitioning instead of the guided. It displayed my hard drive (OMFG!!!). It took a bit to figure it out but i am currently installing and I have high hopes (but given my past history they are likely to be shattered). Completely arbitrarily chose 50gb space, which the cd automatically split in 48gb /, 2gb swap. I hope that is ok... I have no idea. I have 4gb ram so id hope i never need the swap anyway.

Will change this to solved if and only iff this installation completes... *crosses fingers*

---

### Post by winter123 on 2010-02-23
Text based installer and manually changing the partitions worked. Have it up and running. So if anyone else has this problem that's what I'd recommend. 

Dunno how to change topic to solved, but i guess it is solved... by myself.

---

### Post by wilee-nilee on 2010-02-24
> **winter123 said:**
> Text based installer and manually changing the partitions worked. Have it up and running. So if anyone else has this problem that's what I'd recommend. 

Dunno how to change topic to solved, but i guess it is solved... by myself.

Glad to see you have it working. The reason I suggested the W7 partitioner is that is what everybody recommends to not bork W7; then have to do a repair. I have used the W7 partitioner to resize a xp partition on the same HD, and the Xp program started without a disc check. I have never seen this happen, XP is notorious at least in my very limited use as needing a disc check if the partitions are resized.

I have used the W7 virtual partitioner without fail on several occasions.

---

