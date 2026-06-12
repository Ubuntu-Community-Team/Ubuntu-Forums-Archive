---
title: "xubuntu first time user install help!"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by spankstar on 2006-11-08
NOOB ALERT!

i had just installed win98 on an old computer, and someone recomend i try xubuntu and use it as a server/storage.

i downloaded xubuntu-6.10-alternate-i386 from a link taht was sent to me. 

when i try to boot from cd it says, isolinux 3.11 debian... blah blah. cannot be installed, try cd2 or bios update

any ideas?

and how do i install new bios?

---

### Post by ReaderRat on 2006-11-08
It may be telling you that your BIOS won't "Boot from CD." Have you set the BIOS to boot from the CD?

---

### Post by jamesr on 2006-11-08
I am surprised that the boot programme recommends a BIOS upgrade unless the BIOS is very very old. So could we have details of the PC.

---

### Post by confused57 on 2006-11-08
> **spankstar said:**
> NOOB ALERT!

i had just installed win98 on an old computer, and someone recomend i try xubuntu and use it as a server/storage.

i downloaded xubuntu-6.10-alternate-i386 from a link taht was sent to me. 

when i try to boot from cd it says, isolinux 3.11 debian... blah blah. cannot be installed, try cd2 or bios update

any ideas?

and how do i install new bios?
Here's how to burn an iso to cd:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

May or may not be your problem...make sure to burn to cd "as an image", not as a data or bootable cd, and burn at a low speed(8x or less).

---

### Post by spankstar on 2006-11-10
to answer one question, it is an oooooooooold pc. (120mhz) 
so i think i might need a bios update

also, im pretty sure i burned the disc correctly (to answer another question).

how do i update a bios?¿

---

### Post by eeried on 2006-11-10
hello,

You may have difficulty running Xubuntu on your ooold PC.

You could try using Damn Small Linux (CD-Live) on your machine first. It's tiny anf light. It's a real Live CD, not a demo one like Ubuntu. Let's see if this Live-CD runs, if you can go about usual tasks (web, mail, office, music).
Alternatively you can try Puppy Linux (real Live-CD) but you do need some RAM since Puppy Linux loads into the RAM.

There's a light derivative of Ubuntu (Fluxbuntu), much lighter than Xubuntu, and i think better than Ubuntu Light but it's still in developement. Looks promising though.

How much RAM do you have? Maybe you can add some. Not too much because your config may not respond to too much RAM anyway. Some RAM sticks work better than others (I don't know why).

A bios upgrade (flashing the bios) is a risky business, if it fails you can end up with a destroyed motherboard. I wouldn't recommend it. Or ask a specialist to do it for you.

Anyway, you need to know and post all the details about your computer before you can get effective help.

cheers

---

### Post by jamesr on 2006-11-10
Being an old PC does not mean that you need to update the BIOS. The only reason to update a BIOS, is, if one is available that gives some hardware feature that is not available with your current BIOS, it does not affect the running of linux unless there was a bug the ROM code and that would suggest the BIOS / motherboard that comes from a fly-by-night operation. Also as previously mentioned > A bios upgrade (flashing the bios) is a risky business, if it fails you can end up with a destroyed motherboard. I wouldn't recommend it. Or ask a specialist to do it for you.
 is a very risky business and if it fails you end up with M/B that will not boot, Then you you will need to find copy of the original BIOS as a ROM.

I would also recommend SaxenOS, a linux distro that was designed to run on older PCs. GUI looks very windows like. The Base is Slackware (lite) so has a good history behind it. It needs 64MB of RAM but likes 128MB. Also the live CD functions reasonably well. Had a good writeup in TUX, I think.

The important factor in all of this is the amount of RAM available.

---

