---
title: "Upgrading IBM thinkpad"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by ozraelised on 2007-04-05
Hi I am new tp Linux. I done some reading and now I wiish to upgrade an IBM Thinkpad R30 running a windows 2000 to ubuntu. I downloaded the software and copy it to a cd.
I rebboted the Thinkpad from the CD and I can see the ubuntu logo and the progress line moving from let to right it takes about 5 min' it come with"

[PHP][/PHP]BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in Shell (ash)
Enter 'help" for list of bult-in commands:

/bin/sh: can't access tty; job control turned off
(initramfs) [17179827.200000] irq 15: nobody cared (try booting with the "irqpoll" option)
[17179827.200000] handlers:
[17179827.200000] [<c02528e0>] (ide_intr+0x0/0x1f0)
[17179827.200000] Disabling IRQ #15[PHP][/PHP]


If this means anything to someone let me know. Also the irqpoll option I wasn't able to find any inofmration about that.

Need your help

thanks

Ozraelised

---

### Post by Spr0k3t on 2007-04-05
Which release are you trying to install (Dapper, Edgy, Feisty).  I have seen this before and found it was a problem with the disc itself.  I reburned the ISO on a different system and everything just started working.  So, try booting the disc on another computer system to see if there are any problems with the disc itself.  Then, create a new disc from the ISO and verify the checksum on the thinkpad.

Best o' luck.

---

### Post by ozraelised on 2007-04-05
Thanks for that - I am making the new ISO as we speak.
With regards to the releases available - where can I find information about that. I am new to all this - you can say 2 days old. 
What will be a good read to start and understand the versions and all the lingo?

Thank you for your reply I will let you know if it worked or not

---

### Post by Spr0k3t on 2007-04-06
An excellent place to read up on the information of all things Ubuntu is [http://ubuntuguide.org](http://ubuntuguide.org).  Has information regarding versioning and where to find the latest.

---

### Post by BlkPhoenix on 2007-07-07
I had this problem when I tried installing Hoary on my IBM.  In the end, you need to boot from the liveCD again (other posters have recommended that you use the "alternate" CD), when it gets to the bootscreen, hit F6 and at the end of the line of text you see on your screen enter:

irqpoll

That should finish the boot process

---

### Post by powermacj7 on 2007-11-11
I installed on my Thinkpad here is the trick. 
At boot-up you have to do the following type 
floppy=thinkpad pci=noapci

---

### Post by kalle99 on 2007-11-12
Could you be more specific?
Tried with parameters floppy=thinkpad pci=noapci with the same error:(

---

### Post by dgtldaydrmr on 2007-11-12
I have frequently run into odd issues using the live CD on notebook PCs.
I pretty much religiously use the alt CD now. (have you tried it yet?)

---

### Post by kalle99 on 2007-11-12
Thnx, but i would like to try it out before installing, e.g Use the Live function. Is this available on the alternate cd?
I found the problem!
It should be pci=noacpi, NOT "noapci" now it works fine, also had to enable floppy in BIOS.

---

### Post by powermacj7 on 2007-11-12
> **powermacj7 said:**
> I installed on my Thinkpad here is the trick. 
At boot-up you have to do the following type 
floppy=thinkpad pci=noapci

Sorry for the typo! Glad you got it to work....](*,)

---

