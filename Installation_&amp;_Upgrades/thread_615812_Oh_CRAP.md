---
title: "Oh CRAP"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by shdw.puppet on 2007-11-17
I was upgrading to gutsy the other night and I lost power about halfway through the installation phase. Not A big deal I thought, has happened to me on windows. So I reboot and after the grub loading message I get something like this

Starting Up...
[numbers here] Kernel Panic (something about VFC not connecting to root on hd1)

I cant do anything from there. I retried thiss about 10 times. NADA. This is a HUGE problem and I kinda need to fix it very soon. I am running sounds for a play at school and all the effects, sounds, music, chasers, ques and everything else I need is on there.

---

### Post by Toadmund on 2007-11-17
Can you see the data on your hard drive if you boot up your live cd? 
If so your stuff is still there, which means if you have a spare partition, you can re-install ubuntu there (on new partition) and cut and paste your data over.
If no spare partition, put your data on a USB stick or external drive and re-install. And re-upload your data (songs, plays etc)

My opinion is your OS is borked, but wait for another opinion and tell us what you can.

---

### Post by wolfen69 on 2007-11-17
this will not solve your problem, but in the future, you might want to consider buying a good UPS. (uninteruptable power supply) it saved me a couple of times. and, BACK UP! if you keep valuable things on your main hard drive, also save them to another storage drive. live and learn.

---

### Post by Pumalite on 2007-11-17
Backup everything as a matter of good practice before  the install of ANY OS.

---

### Post by Toadmund on 2007-11-17
> **wolfen69 said:**
> this will not solve your problem, 
You mean to say the OP shouldn't bother to see if the data is still there?
I'd like the OP to stick the live CD in just to see.

OP? Hello...

---

### Post by Laserbeast on 2007-11-17
I concur, I'd say it's FUBAR.

If you have any data you need on it, I'm sure you'll be able to retrieve it. If burning all those data files you speak of are too much to put on multiple CDs or DVDs, hook up another harddrive and transfer it all. After that, reinstall :)

---

### Post by mellowd on 2007-11-17
Give the live cd a try. I've had the power go out in the middle of a partition operation and my drive got nuked

---

### Post by shdw.puppet on 2007-11-19
sorry its been awhile, I can now only use school computers.

The complete error message was

[     44.699547] kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

How do you access you hd from a live cd?
I haven't found a way to do this as of yet.

---

### Post by Pumalite on 2007-11-19
Get Knoppix Live CD (it mounts your drives/partitions automatically at boot:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by shdw.puppet on 2007-11-22
I finally fixed it.
I got all my data using knoppix and reinstalled with a shiny new 7.10 cd.
Im not sure why what happened happened, I suggest that in future releases, safeguards are made against total os breakage when upgrading. Windoze does it automatically, (albiet, crappily) so I think Ubuntu should at least have the option of making a restor point ICE

---

### Post by Pumalite on 2007-11-22
Knoppix is oriented to being a very good Live CD. Ubuntu on the other hand is a full featured OS oriented to the installation. You are welcome btw.

---

### Post by shdw.puppet on 2007-11-22
Many thanks Pumalite, you pretty much just saved my skin.
Yes, Knoppix is very fine and well, but I think Ill leave it to recovery or emergencies where I must have linux and a live CD is the only available option.
Thanks again

---

