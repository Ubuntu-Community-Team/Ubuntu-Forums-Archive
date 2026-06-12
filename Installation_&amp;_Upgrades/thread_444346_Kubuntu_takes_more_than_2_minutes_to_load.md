---
title: "Kubuntu takes more than 2 minutes to load"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-15
Just installed Kubuntu 7.04 on an IDE drive.
I first disconnected from mainboard my SATA drive with WinXP just to make sure Kubuntu installs everything on the IDE drive alone.

Everything seems fine and I still ONLY have this IDE drive connected, however when I start my PC it gets to the "Kubuntu" blue sign screen and sits there for a long time, the blue bar starts moving just about close to 2 minutes, then I finally get the login screen.

Why does Kubuntu sits with the loading blue bar close to 2 minutes?
There's gotta be something to correct or improve this.

My IDE drive is a 40GB drive.
Primary master    =CD is master and DVD is slave
Secondary master=IDE is the only drive connected, jumper set to CS (cable select)
3rd master              = not configured
4th master              = not configured      

Any thoughts on this please??

---

### Post by Topsiho on 2007-05-15
That booting takes so long can be caused by a slow processor, and/or a lack of RAM. You did not mention these specifics for your computer. You' ll need more than 256 MiB RAM, more is far better.

Another possibility is that the boot program is looking for something that it can' t find, and is trying again and again, until it gives up and proceeds.

Type dmesg in a terminal and see if you can find out what that thingy is that it tries to find in vain.

also:
you write:
"My IDE drive is a 40GB drive.
Primary master =CD is master and DVD is slave
Secondary master=IDE is the only drive connected, jumper set to CS (cable select). 
3rd master = not configured
4th master = not configured"

This puzzles me. You have two IDE connectors, on which you can attach two drives each, totals 4 drives.

On the first IDE you can have two drives, a Master and a Slave.
On the second IDE the same.
In your words these would be the primary Master an primary Slave on the first IDE (IDE0)
And on IDE1 that would be the secondary Master and secondary Slave.

Third and fourth Masters just don' t exist!

So with this information you could probably find out what is wrong in your setup :)

Hope this helps ..

Topsiho

---

### Post by geek2330 on 2007-05-15
I have a Pentium 4, 3.0GHZ and 512MB Ram.
It's a very good and fast PC.

I really think that the problem is the jumper, it is setup as Cable Select, when I get home I will try to change it to master and see what happens.

I will explain later with better description so you don't get puzzled with my question...

---

### Post by geek2330 on 2007-05-15
Well.....I changed the jumper to "Master" and now it is worst.

The Kubuntu screen appears and takes a very long time and the blue bar never moves, then an error displays:

[COLOR="Red"][B]/bin/sh: can't access tty; job control turned off
(initramfs)[/B][/COLOR]

What am I doing wrong, do I need to change grub just because the jumper setting change, and how??

---

### Post by geek2330 on 2007-05-15
Guys, I changed the jumper back to CS "Cable Select" on the IDE drive, now I am back in business but with the same issue that I started this thread....takes too long to boot up...

Please help...!!

---

### Post by wpshooter on 2007-05-15
My guess would be that you need to make the jumper change before you install the O/S.

I NEVER use cable select.  I always set drives as master and slave.

If it were me I would put the hard drive on PRIMARY as MASTER & I would put DVD on SECONDARY as MASTER & CD-ROM as SLAVE.  I would always put my hard drive on the PRIMARY socket.

Also, I would say that perhaps your hard drive may be part of the problem.  You say it is 40gb.  What is the spindle speed ?  If it is less than 7200rpm, then maybe that is contributing to the problem and then 2 mintues might not really be consider slow under those circumstances.

Good luck.

---

### Post by geek2330 on 2007-05-15
Thanks wpshooter,

I wonder what would happen if I switch the cables on the mainboard, meaning if I change my HDD to the primary and then the CD/DVD to the secondary channel as you mentioned.....

Should that force me to reinstall the OS.

The reason the CD and DVD are on the primary chain is because my original drive is a SATA (which is unplugged right now....) so I think SATA doesn't count on this primary/secondary connectors, SATA uses a different connector on the main board.

Before I make the switch, having the IDE on the primary chain and the CD/DVD on the secondary chain: can someone please quickly confirm if that's gonna cause trouble for Grub to load the OS properly? I want to hear some options and opinions before I move further..:( 

Thanks guys for the support....!!!:-k

---

### Post by geek2330 on 2007-05-16
bump.....please help...!!

---

### Post by geek2330 on 2007-05-18
RESOLUTION: after reinstalling Kubuntu 7.04 I was still having the same performance when botting up.

After many tests I found that if I leave a CD in the cdrom then Kubuntu boots fine, WAYYYYY much faster....!!!

The CD can be balnk media or not, doesn't matter...!!!!

Can someone explain this?? :confused::confused::confused:

.

---

### Post by handuy on 2007-05-19
I have the same problem and When i put the blank cd in the drive and start UBuntu it load super fast too. 
BUMP !!! for answer

---

### Post by Topsiho on 2007-05-19
Seems like the boot settings are such that the boot program is looking for a CD in the drive. If it is not there it looks and looks for it until the time out, and only then continues. So you know now where to look to solve this problem.

Topsiho

---

### Post by geek2330 on 2007-05-19
Looks like a bug to me, don't you think??

---

### Post by armandas on 2007-07-18
I attached a bootchart image, which shows what happens in boot-time.
I use Kubuntu 7.04 on:
[LIST]
[*]ASUS A6000
[LIST]
[*]CPU: Intel Pentium M 740, 1.73 GHz;
[*]RAM: 1024 Mb;
[/LIST]
[/LIST]
I have no cd in my cd-rom, but theory, that Kubuntu checks for a cd looks like a possible problem. If anyone has any solutions, I would be very happy to hear them ;)

Thanks!

**UPDATE:** when I removed "quiet" flag from boot options, I noticed that loading "restricted drivers" and "hardware drivers" takes the most of time. Still have no idea how to improve boot speed.

---

