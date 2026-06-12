---
title: "Impossible to install Ubuntu on a Lenovo ThinkCentre S50 ..."
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by marginal39 on 2010-08-30
Hello everyone.

I am trying to install the latest version of Ubuntu on a Lenovo ThinkCentre S50 8183 PC.
And it's not the first time.
I tried a previous version a year ago without success as well.
The Ubuntu logo comes up and the white and red dots below it start scrolling for a minute and after that, the PC freezes.
I have windows 7 installed on this machine now, but need to install Ubuntu as I acquired a NEC SuperScript 1400 Laser Printer recently, and windows 7 does not support it.

Please help.

---

### Post by jmore9 on 2010-08-31
Hello !

I am running Ubuntu 10.04 right now on a IBM Thinkcentre 8183.  I had zero problems installing using the defaults.  It installed the Intel video stuff automatically and the Internet worked right off the bat.

maybe i can help you get yours running where to start ?

---

### Post by jmore9 on 2010-08-31
Are you using the 10.04 distro install disk ?  Also how did you format your hard drive ?  Are you trying to dual boot ?

---

### Post by marginal39 on 2010-08-31
Hello [jmore9]("http://ubuntuforums.org/member.php?u=45721") and thank you for your reply.
I wish you could help me.
The problem is, I know about computers a lot and still have not solved that problem.
Maybe I should run a memory test ???

Thanks.

---

### Post by jmore9 on 2010-08-31
You said you have windows 7 installed, so your memory should be working.

Again what are you using to install Ubuntu from ( cd or dvd ) which version of Ubuntu ?

Did you just install with the defaults then tailor it as you need to ? 

And finally are you dual booting , how did you set up your hard drive as far as formating goes ?

---

### Post by marginal39 on 2010-08-31
I am installing it from a Ubuntu 10.04 LTS CD.
The installation freezes before I can format the HDD, choose defaults or not, or dual boot.
I wanted to get the screen where I can choose what partition to install on, and/or format and make the two partitions, one  "/" and another one "swap", but it freezes before that moment.
Maybe the problem is in my DVD ROM Reader?

---

### Post by jmore9 on 2010-08-31
I use GParted Live cd for all my hard ddrive resizing and partitioning.

I would suggest that you download and burn yourself a copy.  It makes partitioning that much easier.

You could also try downloading the dvd version and burning that to disk and using it.

Did you do a check install media at the beginning of the install ?   Maybe your cd is bad ?

---

### Post by marginal39 on 2010-08-31
I'll try using the GParted Live CD.
I have not check the install media at the beginning, but this is the second CD I am trying so ...

Thanks.

---

### Post by marginal39 on 2010-08-31
I ran a memory test and it shows I have 199 Mhz DDR 399 Memory inside.
And while reading the PC's manual I noticed the memory is supposed to run on a 333MHz bus speed.
Couldn't this be the problem?

Thanks.

---

### Post by snek on 2010-08-31
Tbh it sounds like your harddrive is not recognised properly.
Somehow I doubt it's the RAM, especially on laptops it's not really possible to overclock or anything so I wouldn't worry about that too much. If windows 7 is stable I highly doubt that's the problem.

If you really, really want to make sure there's no weird encryption on the harddrive which is not letting you install/format you might want to try KillDisk. It sounds a bit more scary than it really is, it basically just wipes the harddrive. **Of course this will erase ALL data, and if you let it do multiple runs you won't be able to get it back either**.. I've just noticed that sometimes Windows and other partitioners do weird things to the drive, and I've had luck using KillDisk to wipe it and then repartition using the OS's default partitioner. Especially tools which resize partitions are known to do weird things to the partition table.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by marginal39 on 2010-08-31
Thank you for the input [snek]("http://ubuntuforums.org/member.php?u=103322"), but it really turned out to be the memory.
Not only it is not the right type of memory, but it showed errors while being tested.
BTW, my PC is a desktop.

Thanks.

---

### Post by snek on 2010-09-01
Oh lol, my bad... I think I confused your post with someone else's and assumed you had a laptop. Glad you figured out the problem though.

On another note, your Windows installation may be corrupted without you noticing due to the faulty ram. I've once experience this problem at a client's house, Windows would install fine but be really unstable because he had set his ram values wrong in bios. Even after setting them right it wasn't stable, because the installation was corrupt. Only fixed it by reinstalling Windows with correct ram settings.

---

### Post by marginal39 on 2010-09-01
A faulty RAM is not going to help for sure :) ...

---

