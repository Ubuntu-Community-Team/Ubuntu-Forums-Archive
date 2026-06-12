---
title: "installing 7.1 problem error?"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by jwxie on 2007-12-08
hey guys, new to to ubuntu
i did read the guide for installing ubuntu
but when i get to "based system installation, i got a error said cannot install"
so i went back to Partition my disk again, i thought it was the problem with that Partition 

anyway, i couldn't install it again

so i restart my machine, and did the same thing
and following appeared after i chose "install ubuntu"

i don't know what it mean, and plus something was really wrong

at the end of such loooong messages, i was able to enter the first step to install ubuntu, i think it was to choose a language

so i did. but each step took at least 2~3 minutes just to enter the next

before my first experience with "cannot install based-system", i was able to enter each step quickly, sometime within 20 secons, some steps required 1 min or so. but now everything had gone unexpected.

i'm using an old school machine  P3
two of the pic have my spec

---

### Post by jwxie on 2007-12-08
ps: can someone please move this to the correct place? i posted it wrong
sorry

---

### Post by Sef on 2007-12-08
Moved to Installation and upgrades.

---

### Post by Pumalite on 2007-12-08
> **jwxie said:**
> hey guys, new to to ubuntu
i did read the guide for installing ubuntu
but when i get to "based system installation, i got a error said cannot install"
so i went back to Partition my disk again, i thought it was the problem with that Partition 

anyway, i couldn't install it again

so i restart my machine, and did the same thing
and following appeared after i chose "install ubuntu"

i don't know what it mean, and plus something was really wrong

at the end of such loooong messages, i was able to enter the first step to install ubuntu, i think it was to choose a language

so i did. but each step took at least 2~3 minutes just to enter the next

before my first experience with "cannot install based-system", i was able to enter each step quickly, sometime within 20 secons, some steps required 1 min or so. but now everything had gone unexpected.

i'm using an old school machine  P3
two of the pic have my spec

Try:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
If ir doesn't work, go with a smaller distro like DSL or Puppy.

---

### Post by jwxie on 2007-12-08
i will try it later^^
ty
but i tried it one more time with my iso cd

still same error


and sorry if i didn't make my question clear..wonder for this soruce
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

do you want me to burn this iso?
PC (Intel x86) alternate install CD

i want to install my Ubuntu Server 7.1
i burned the iso too

---

### Post by Pumalite on 2007-12-08
You have 128 MB of RAM. Maybe you should try 6.06

---

### Post by jwxie on 2007-12-08
> **Pumalite said:**
> You have 128 MB of RAM. Maybe you should try 6.06


okay, i will try it^^
but i really have a question about those error
did it mean my ram or my hard disk has problem?
i'm dowloading 6.06 now^^
ty first

---

### Post by jwxie on 2007-12-09
OK
I TRIED 6.06 TOO
IT SEEMS it's a problem with either ram or HD

please check,
i experienced same case as the 7.1 when i install 7.1 second time

my first time did not have that error
instead it continued to step 1
but when i begin to install the based system, it appeared error

then i tried my second time with 7.1 and could not even partition, 
and now i tried 6.06, same error

please tell me how to clean, or fix this problem
i want to test ubuntu on this old school machine

---

### Post by Pumalite on 2007-12-09
Get Gparted Live CD. Boot from it. Delete your entire hard drive. Make new partition of your whole hard drive formatted ext3. Make 10 Gb partition for'/', 1 GB for /swap. Now install again; this time going Manual and using partitions already made.

---

### Post by Pumalite on 2007-12-09
You might have a problem with your hard drive. Use TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd:[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by jwxie on 2007-12-09
hellol again, ty for your great replies

i have 2 questions so far

i went to the test-disk link you gave me, and i found the Gpart Live CD
and i download the latest, yes
then i will use the iso cd and boot it, and do as you want to do
okay, but 1st question:
i have 82 gb, what should i do with my other 70gb?


second question
test disk ,which verison should i get?
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
should i perform test disk before i boot my Live CD?

---

### Post by Pumalite on 2007-12-09
It wouldn't hurt to check your drives first. The rest is for /home. (make that partition too.

---

### Post by jwxie on 2007-12-09
ty again
let me make sure this before i do anything

check disk
or go straight to Gparted Live CD
then i make 10Gb for /
1Gb for /swap
and the rest make it as /home

right?

---

### Post by Pumalite on 2007-12-09
Yes

---

### Post by jwxie on 2007-12-09
hello again
i just tried to boot my Live CD
and i chose the first one, auto-config
later on i receivce error too
so i reboot again, and tried boot #3 on first HD
didn't work either

i thought i was suppose to enter like the following screenshots
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
but i don't, because i didn't even finish install the 7.1 based system, so what can i do?

man, sorry and thank you very much for your patience with me, solving this problem

---

### Post by Pumalite on 2007-12-09
Yes

---

### Post by jwxie on 2007-12-09
> **Pumalite said:**
> Yes

um..??
sorry...so what is"yes":lolflag:??

---

### Post by Pumalite on 2007-12-09
Your /home partition. Check your drive before doing anything else and report your findings here.

---

### Post by jwxie on 2007-12-09
> **Pumalite said:**
> Your /home partition. Check your drive before doing anything else and report your findings here.

sorry again
but Mr. Pumalite, you know i'm new to this software too

well, i boot the live cd again
and i went for "auto-config and frame buffer"

and here are the screenshots i took

when it checked my config i believed, it showed that "letting udev process events" is **[COLOR="Red"]!!, so there is a probelm[/COLOR]** (in screenshot)

---

### Post by Pumalite on 2007-12-09
What Live CD are you booting?

---

### Post by jwxie on 2007-12-09
> **Pumalite said:**
> What Live CD are you booting?

The Gparted Live CD you told me to download
the latest verison from its official site

---

### Post by Pumalite on 2007-12-09
Check your drives first with TestDisk.

---

### Post by jwxie on 2007-12-09
okay
but which verison
linux?which linux?
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

#  dos.png Dos/Win9x, zip
# win.png Windows NT/XP/2000/2003/Vista, zip
# linux.png Linux, tar.bz2
# macosx.png Mac OS X, tar.bz2
# rpm.png Linux RPM
# rpm.png Linux SRPM

---

### Post by Pumalite on 2007-12-09
Whatever is convenient for you. If you are running Windows now; then, for Windows.

---

### Post by jwxie on 2007-12-09
> **Pumalite said:**
> Whatever is convenient for you. If you are running Windows now; then, for Windows.

i first my old machine first run windows
now i tried to install ubuntu linux
so i chose windows?
but that windows OS  is corrupted too, that's why i wanted to use this machine to use Ubuntu

---

### Post by Pumalite on 2007-12-09
Where are you posting from? Whatever OS you are using now; that is the format you download.

---

### Post by jwxie on 2007-12-09
BUT Pumalite, the problem is that I couldn't even get into Ubuntu, because the base-system installation failed
so how do i perform a test disk if the file is not iso, or any kind of image-based file that you could perform via booting the image-CD

---

