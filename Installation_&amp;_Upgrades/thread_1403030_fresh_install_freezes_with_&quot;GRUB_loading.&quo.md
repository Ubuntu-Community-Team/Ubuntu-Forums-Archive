---
title: "fresh install freezes with &quot;GRUB loading.&quot; and nothing more"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by amityak on 2010-02-09
Hi all

I got a second hand IBM NetVista with a Pentium 4 and some few gigs of RAM. from looking inside the box seems like everything is pretty much in place and original. Few installations didnt even load, an old windows xp cd it tried didnt work either. the only this worked was the alternative cd of keramik koala for i386.

it recognized the hdd and installed everything, no error message (except for not recognizing the network because i will be setting it wireless) succesfully installed, cd pops out. reboot and then it start beeing funny

it takes some time.... a minute maybe and the at once i see just

```
GRUB
```

then nothing ...

another minute passes and then all of a sudden a new word appears so what i get is

```
GRUB loading
```

nothing happens, another minute passes and a new dot comes along

```
GRUB loading.

```

and the cursur blinking on the next line. there i stop to recognize any activity...

does anyone have any clue what might be the problem ?

very much thanks

Amit.

---

### Post by amityak on 2010-02-09
okay... some more info
i tried putting in an old live cd of 8.10
it starts loading the live cd and then gives the following:

```
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter help ...

(initramfs) [   67.568102] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   67.568173] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   67.568178]        res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   67.568291] ata1.00: status: { DRDY }
```

then it waits a while and gives out the same with different time stamps

can anyone please explain what does is mean ?

---

### Post by amityak on 2010-02-09
a live cd of 7.10 gives a similar error. it start looking like a hardware problem aber which? the hard drive should be irrelevant i think for a live cd right ?
memtest i was running for about an hour it found no errors but it could go forever, i will run it tomorrow before i go to uni so i dont have to sit and wait for it. 
i start considering homer simpson's dr. television method (i.e. slamming it read hard until it works.. hehe)

so... for any ideas i will be thankful

---

### Post by amityak on 2010-02-09
after reading in some other post i took the hdd out, trying again to run the live cd. no error messages. but its still not loading. now just a blank screen with the curson blinking on first position

---

