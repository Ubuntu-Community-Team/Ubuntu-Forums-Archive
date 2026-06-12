---
title: "[SOLVED] PLEASE help"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by yogeshnachnani on 2008-08-06
hey ppl, although i DO know a lil bit about computers, i am not familiar with linux

i heard about ubuntu and thot of installing it

i got an 8.04.1 version iso and rebooted my computer

the 4 options came up and i chose to try Ubuntu without any changes to my comp

so, it begins loading the "linux kernel".. this goes to a 100% in no time

then, the ubuntu logo shows up, with a progress bar below it(too much detail, i know.. hehe)

so after bouncing about a bit, it starts seriously loading

after about 20 secs,the progress bar gets stuck
and my dvd drive shows no activity either(no flickering light)

then after waiting for 5 odd minutes,(hoping that it'll resume) i get the following msg : 

*// some lines with '*' as the beginning char.. all [OK]

*Loading hardware drivers
udevd-event[5693] : run_program : '/sbin/modprobe' abnormal exit
/etc/rcS.d/S10udev : 105 : usplash_write : not found
Segmentation fault
/etc/rcS.d/S10udev : 1 : usplash_wirte : not found
/etc/init.d/rc : 317 : usplash_wirte : not found
/etc/init.d/rc : 317 : sed : not found

init : rcS main process (5450) killed by SEGU signal
init : unable to execute "/bin/sh" for rc default : no such file or directory
init : rc default main process(6631) terminated with status 255


My config :
Desktop PC
Intel D Dual Core 2.66Ghz
Intel 945GNT motherboard
Nvidia GeForce 7300LE PCI-Express Card
160GB Hitachi SATA HDD
LG DVD/CD Writer

I used Nero to burn the iso image

I also checked the file for errors(one of the few options in the first menu)

PLUS i tried installing kubuntu and ubuntu 8.04.. nothing worked


please help.. my first guess is to try and install the 64 bit verion, but i just thot i'll run it by the experts first


P.S : i know its a ubuntu forum, but i got some problems with installing fedora 9 also..

---

### Post by Pumalite on 2008-08-06
Burn a new CD:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less, check CD integrity before install. Do not use CD-RW

---

### Post by yogeshnachnani on 2008-08-06
forgot to add this : also tried the md5 checksum and it matches

---

### Post by yogeshnachnani on 2008-08-06
hmmm... might try and burn at 4x.. any other suggestions?

---

### Post by mad_prince on 2008-08-06
i've tried 3 different images downloaded (kubuntu, twice ubuntu) and with all I had problems with installation, so I order my ubuntu at shipit and it works :)
If you have possibility borrow Ubuntu from friend

---

### Post by zvacet on 2008-08-06
After you burn it did you check disc integrity?

---

### Post by yogeshnachnani on 2008-08-06
yes i did check for the disc's integrity [first thing i did actually :) ]

---

### Post by yogeshnachnani on 2008-08-06
I did order for a cd b4 posting on the forum.. hope i get one soon.. but my main concern is whether theere is a h/w related issue .. :confused:

---

### Post by yogeshnachnani on 2008-08-07
39 views?? no comments?

---

### Post by Pumalite on 2008-08-07
Delete

---

### Post by semitone36 on 2008-08-07
How many different disks have you tried?

I would reburn a CD, but this time, set the burn speed down to 1x. Image files can be really touchy in my experience so its always good to be careful.  If a new disk doesnt work and the disk youre having shipped to you doesnt work then i would definately say its your disk drive.

---

### Post by |Eric| on 2008-08-09
seams like udev is crashing 
udevd-event[5693] : run_program : '/sbin/modprobe' abnormal exit

then you get a segfault as udev crashed
try loading from the liveCD 
you can also try the cat /var/log/system if memory serves
that is where system logs the boot (dmesg works too ) 
but just make shure your reading the crashed boot :P
you can try Alt+F1  & shift+pageUP to read what the message where before that point

---

### Post by oldos2er on 2008-08-09
How much RAM do you have?

---

### Post by yogeshnachnani on 2008-08-12
Thanku all for the replies... but i solved the problem..

ITS NOT MY DISK DRIVE...

It was in my bios settings...

I have a 945 motherboard(mentioned earlier) and a PCI E graphics card..

Will just tell u wat i did (for ppl who are interested :) )

I changed one tiny setting

In my bios setttings, i went to "advanced->chipset configurations->pci express configurations"

Here, i changed the "Compliance Test *" to <Disable>

(the * indicates a Word i cant remember)

I dont know how this setting got changed, since when i "loaded" defaults, this setting was set to <Disable>

Probably this lil tweak wil work for every1 having a PCI Express graphics card...

I request mods to take notice and post this suggestion somewhere where it'll be more useful.. Thanx to every1 who replied.. thanku :)  :)

:popcorn:

---

