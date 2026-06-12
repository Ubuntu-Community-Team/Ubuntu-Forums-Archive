---
title: "Synopsis of installtion problems with ubuntu 7.10"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by levent20 on 2008-03-14
Ok i will make a overall synopsis of my experience with ubuntu so far....

1. it seems to be a very good OS with a lot of features that will suit me.

However....

2. i install on my external hard drive under instructions from various posts and unmount the drive, change the groot to (0,0) , the root to (0,0) and boot from usb first and all is good for the first ten minutes.

Then the system kind of freezes if i leave it idle(do nothing). sometimes firefox prints input/output error, other times just attempts to load but nothing happens. that is the case with other programs as well!!!

Tried to follow the gpmartison post (forgive me if i misspelled his name) but in the second line of his instructions after the mkdir i type mount something and it tells me that only root can do that.... sorry for not providing more details,but my knowledge is kind of limited also.

 (dabrugo's post also will try again one last time, but i don't know what the results will be)

If anyone knows more about please help,
Dell inspiron 6000
2gb ram
x300 ati
external seagate drive 120gb

for more info see relevant posts under my name

Thanks,
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:
Levent20

---

### Post by levent20 on 2008-03-14
Halo again, 

Probably found the solution.

Read a newspaper article that said that seagate new drives don't support linux.... what can i say...

Anyway a guy there printed the following...

download sdparm from the synaptic package manager and in a terminal....
sdparm --clear STANDBY -6 /dev/sd[your device]

So far so good... cross fingers.
Thanks,
Levent20

---

