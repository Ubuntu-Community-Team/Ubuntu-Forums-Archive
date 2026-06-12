---
title: "Heartfull of dread"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by orochiko on 2011-02-06
So I'm a new Ubuntu user, I've never really tried it before. I heard a lot of good thing so I wanted to give it a go. But I encountered a few problems. I've been a Windoze user for a long time and I didn't think I could be taken by surprise. 

First issue is that since I use windows 7, I had to install differently, rather then just starting the computer up with the disk. I had to do some pre-installing then restart and choose Unbuntu. 

When I try to download the full version it gives me an error. 
(process:430): GLib-WARNING **:get pwuid_r (): Failed due to unknown user id (0)

Also when I tried again downloading through the demon version, it told me to allocate my disk space. I have a external hardrive so i thought that I could install it on there and take Ubuntu with me where ever I go. Apparently since there is no DOS in my external, it didn't work. In the process I think I nuked my External Terabyte hard drive and I'm almost in tears. I tried installing on my normal drivers and it's still not working. I get my error. 

Some other questions I have, If i split my drive and allocate EX: 200g on each. Does that mean that both will run better? or slower?

Another question I have is after my external had a lobotomy I think I lost all my stuff on it. I'm on Windoze right now and it's not even recognizing it as a drive or anything, like it's not even there. Is there a way to reverse what I've done to my drive? Can I get all my photos and music back? I dread the worse >_<

---

### Post by mörgæs on 2011-02-06
Hi, welcome to the fora.

Many questions - let us take them one by one.

The best data recovery tool I know is Photorec:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Does this help you getting your files back?

---

### Post by ronnielsen1 on 2011-02-06
> First issue is that since I use windows 7, I had to install differently,  rather then just starting the computer up with the disk. I had to do  some pre-installing then restart and choose Unbuntu. 
You should still be able to boot from a live cd. I guess you installed through wubi? Is your bios set to boot from cd? If not, go to the link below:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

If this works and you are able to boot from the cd, then use the cd to check to see whether your files are still there. If not, then you'll have to use Photorec / Testdisk to get them back like Morgaes suggested.

---

### Post by orochiko on 2011-02-08
Good news I have Linux up and running. I'm very happy with it and I'm going to try out Photorec to see if i can get my files from my external hard drive. If so I would be so relieved. 

:D Thanks guys! You're awesome!

also if i ever wanted to partion more of my hard drive to linux is that possible?

---

### Post by mörgæs on 2011-02-08
You are welcome.

If you want to give Ubuntu more space, best is boot into Windoze and free some space from here. Boot the machine once more into Windoze to verify that it all works.

After that you boot into Ubuntu and expand the partition(s) using Gparted.

---

