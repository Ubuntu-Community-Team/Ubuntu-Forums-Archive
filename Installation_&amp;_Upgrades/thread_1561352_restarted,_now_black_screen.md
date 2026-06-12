---
title: "restarted, now black screen?"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by EvoFX on 2010-08-26
so i just installed 10.04 lts on my xp and did a complete wipe since i no longer need xp for this desktop. well it worked and when i restarted a got the black screen with the cursor. 

someone said to hit enter but it does nothing. and when i wait about 3 mins i get these erors and failed commands flooding my screen...

is there a way to fix this?

---

### Post by arubislander on 2010-08-26
There are several ways to go about it:

The first would be to just try the install again.
The second would be to try to read some of the errors and failed commands and google them, or at the very least search these forums (I find googling is more efficient. 
It would also help if you had at least listed some of the errors so the folks here could get an idea what we're dealing with.

Have a go at that and report back.

---

### Post by EvoFX on 2010-08-26
ok so i just put my jump drive in and it popped up as install ubuntu again? should i just install it again, or do i have to delete the older ubuntu?


here is also what i am getting when the errors come up

          exception emask 0x0 Sact 0x0 action 0x0 
 BDMA stat 0x65
 failed command : read DMA EXT
 cmd 25/00:08:e8:15:00/00:00:16:00:00/e0 tag 0 dma 4096 in
 res 51/40:00:08:e8:15:00/40:00:16:00:00/e6 emask 0x9 (media error)
 status: {DRDY ERR}
 error: {UNC}


(and for some reason i cant get my jump to boot up again..)

---

### Post by thegod_slayer on 2010-08-26
do one thing
insert your linux bootable cd and when the partitioner comes up delete all the current partions you have....
now create new partitions and install
hope it will work
please let me know if it works or not.....

---

### Post by thegod_slayer on 2010-08-26
exception emask 0x0 Sact 0x0 action 0x0

this means etx4 partition faliure

so i would advise you to create etx3 partition file syatem......

---

### Post by EvoFX on 2010-08-26
> **thegod_slayer said:**
> do one thing
insert your linux bootable cd and when the partitioner comes up delete all the current partions you have....
now create new partitions and install
hope it will work
please let me know if it works or not.....

i do not see where that is?

i am using a usb stick. 

sorry i am new to this so i am not sure were the partitioner comes up.


it seems that it installed but it just wont boot up from the harddrive that its on.

just does the classic black screen and mouse cursor. 
i have read into it but nothing seems to be working

---

### Post by thegod_slayer on 2010-08-26
okay 
while installing the screen where you choose to modify the partitions manually....
then a dialog box appears reading setting up partitioner....
this screen now shows all the drives that you had earlier and gives you option to delete and recreate the 
partitions.....
that is the partitioner table.....

well if you don't understand think i think you follow this link  

[http://www.unixmen.com/linux-tutorials/973-ubuntu-1004-lucid-lynx-step-by-step-installation-for-newbies-howto](http://www.unixmen.com/linux-tutorials/973-ubuntu-1004-lucid-lynx-step-by-step-installation-for-newbies-howto)

---

### Post by EvoFX on 2010-08-26
would it be fine to just erase the entire disk? since i have nothing but ubuntu on it? i have nothing that i need

---

### Post by thegod_slayer on 2010-08-26
yeah that would be just fine....
well if you are confused send me your harddisk size and ram size i will make a partition table for you......

do not get upset or frightened while learning linux.....

always remember here failures are the pillars of success....

---

### Post by EvoFX on 2010-08-26
odd, it works now. came up with some errors when booting, but it was to fast to read and now its loaded.

the only problem i have now. is that it has not detected my wireless adapter. so i cant connect to the internet. i just found my install cd. so should i use that to install the wireless card?

---

### Post by thegod_slayer on 2010-08-26
uuuuuuuu

i didn't understand what you said.......
i mean ubuntu detect wirless networks jsut like that......
mine did....
so i think you should switch off and on you wifi modem......
and try again
let me know..........

---

### Post by EvoFX on 2010-08-26
i mean the light on the back of my desktop isnt lit up showing that the wireless adapter is on. so did ubuntu install it when i switched over?

---

### Post by thegod_slayer on 2010-08-26
okay
look i have't worked on a desktop having wifi
mine was a lappy
just give me a few minutes i need some googleing

---

### Post by thegod_slayer on 2010-08-26
okay got it.......
got to synaptic packet manager....
 type  "broadcom"Right click on &#8220;bcmwl-kernel-source&#8221; and mark it for re-installation


then go back to hardware drivers and activate broadcom drivers.....


this should work

---

### Post by EvoFX on 2010-08-26
i guess its there, but its not enabled. i cant seem to find how to turn it on.

i am googling if there is a command to turn it on, since the network manager does not have an option for that


tried ifconfig wlan0 up

says permission denied

---

### Post by wkulecz on 2010-08-26
> tried ifconfig wlan0 up

try:

sudo ifconfig wlan0 up

---

### Post by EvoFX on 2010-08-26
doesnt work either


ignoring unknown interface wlan0=wlan0

is what comes up

---

