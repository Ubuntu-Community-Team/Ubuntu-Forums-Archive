---
title: "install a RAID 1 + Encrypted server"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by FreekyEy3s on 2013-03-26
Hello all!

OKay, I'm sure I'm not the only one who wants to do this but everything I've read and done for the last 3 months hasn't worked so here I am. Hi!

So, I have made a basic home server before with ubuntu 10.04 just as 'Read/write accesss to all'.
Now I want to create a server to put in my office with:
RAID 1 (mirror)
My work and clients Data encrypted
Remote admininstration (so not have to plug a keyboard and monitor into the box everytime it get switched on after the weekend)
User/Group access restricted by passwords (and so if someone does the nick the box they can't get my data, at least not without some real know-how)

I have:
MSI MS-6547 ver 1
1 GB Ram (512 x1, 256 x2 DDR400)(likely upgrade to 2GB when when of the other PC's die)
Pentium 4 (2.6Ghz)
2 x 200GB SATA hard drive (when I get the damn thing to work I will add 2x 2TB drives)
Raid card for Sata SIL3114 (4Port)
ubuntu server 12.04 LTS i386
(as far as I can tell all the hardware has passed the scans I've given and the disc passed the checksum and integrity checks.)

I have read loads of guides and threads, bought a new RAID card (though I'll use software raid, apparently my other card wasn't supported, by anything) and still not manged to get this to work.
I plan on using Webmin for remote admin, but not had a working system to get that far and try it yet.

However, I am a complete novice at this and was doing this as a fun challenge (and as a more flexible alternative to our current NAS drive).
Now I'm just hoping someone could please point me in the right direction for a step by step guide to get this to work? I'm running out of coffee, and hair.

thank you in advance.

---

### Post by darkod on 2013-03-26
Looks like something like this can help you:
[http://hacksr.blogspot.com.es/2012/05/setup-ubuntu-1204-server-with-full-disk.html](http://hacksr.blogspot.com.es/2012/05/setup-ubuntu-1204-server-with-full-disk.html)

Note that the tutorial uses LVM which you don't need to use if you don't want to, and it doesn't use mdadm software raid which you do want to use.

I guess you will have to create the /dev/md0 raid1 device first, and then encrypt that device (like they encrypt sda2 in the tutorial). After that use that encrypted device for /.

If you want other mount points you will probably need more md devices since each mount point needs a separate md device, encrypted or not.

---

### Post by FreekyEy3s on 2013-03-26
Hello Darkod, thank you for that!

I haven't tried using LVM, but between your notes and that, I think it might actually be better.

So if I'm reading this right:
Initally create 2 partitons on each disk (say 300MB for boot and and the rest of the drive for LVM)
Then mdadm RAID 1 each of them
Md1 (300MB) will then be mounted as boot
Md2 (rest) will firstly be be encrypted (so it unlocks with 1 password, I like that), then LVM, then I can partiton the LVM to say 3GB for /swap, 10GB for /(root), everything else (my) /Data - as I want to keep my data seperate from OS.

This sounds great (and much easy than what I was trying recently), however, how will I be able to enter the password to unlock it on boot (as I don't want want to leave it running all the time)? Will I be able to do that over the network?

---

### Post by darkod on 2013-03-26
The installation part sounds right. As for the password part I have no idea how would you enter it on headless server. Try googling about entering encryption password on headless ubuntu server or similar.

---

### Post by FreekyEy3s on 2013-03-27
So a 'headless server' is one without a keyboard and mouse attached. I didn't realise. A whole new world of reading has opened to me.
Thank you Darkod!

I'll probably be back this weekend when I get the next thing wrong, but fingers crossed for now...

---

### Post by FreekyEy3s on 2013-04-10
OKay, still not working. I get a 'Disk Failure, insert system...' blah message.
So,  after convicing myself it can't be the way I installed it, I have now I  found out that my motherboard doesn't support boot from HDDs attached  to the PCI (SATA RAID) card (the previous card I used automatically set  itself as the primary boot device - though didn't like linux - this new  one has no such feature). I can't find a fix on-line for this, so gonna  go a cry for bit...

 BUT after that, can I just ask, is it  possible to attach 2 x IDE HDD RAID1 for /Boot, /Swap, /(Root) and put  (my)/Data on the PCI cards SATA RAID1 HDDs,  then still have the whole  lot encrypted with 1 passphrase to unlock/mount at boot?
Oh, and if it is, is there anything I should be wary of (e.g. if a disk fails, or when remote accessing).

thank you in advance.

---

