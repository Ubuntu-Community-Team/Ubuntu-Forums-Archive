---
title: "Install failure"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Retired Old Coot on 2007-04-28
I have Ubuntu 6.06 on a CD provided by Canonical. I've used it to successfully install Ubuntu on an older laptop, so must assume the CD is O.K. Now I'm trying to do the same thing on my desktop, a seven year-old Compaq running W98SE (which is working O.K., no known issues, 128MB of RAM) but installation fails repeatedly.

BIOS is set to boot from the CD. When starting, I'm greeted with the Compaq logo and then the disk spins-up. About half the time, nothing happens except what seems to be a re-start with the process repeating itself one or two times. The other times, I get the Ubuntu screen giving me choices, and when I select 'Start or Install', the Linux Kernel loads and I end up with a full screen of white letters on a black background, ending with the following;

[  57.005276] <07> Kernel panic-not syncing: Attempted to kill init!
[  57.005415] _

The last character is a flashing cursor, but it will not accept any entries. At that point, the only way out is to use the power switch. 

I really want to get Ubuntu on this machine in a dual-boot mode. Can someone point me in the right direction? Thanks in advance.

---

### Post by rockyl on 2007-04-28
I tried to load 6.10 on a neighbor's laptop a few months ago. It never worked. It also had 128MB of RAM. I don't think that is enough.

Maybe try Xubuntu(?). I think it requires less.

BTW, none of the live CDs I have worked on the laptop - Knoppix, FC7 live, and maybe Mepis.

---

### Post by bulldog on 2007-04-28
Well,you probably won't succeed to install the live cd with 128MB of RAM.
It's not enough to run the live session.
You need at least 256MB and even then it won't be running like a sports car.

---

