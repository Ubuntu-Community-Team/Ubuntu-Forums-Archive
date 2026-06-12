---
title: "Gtk-warning this process is currently running setuid"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by timbosity on 2008-02-29
HI,

I posted this problem over at the mint forum because thats what im trying out but there hastn been any helpful contribution so...

in short:

Decided to try out mint on my work desktop (Dell optiplex somehting or rather 512ram 80GB hdd, Pentium4 2.60Ghz, BUS 800MHz with XP pro). From gparted on the liveCD shrunk the 2 windows partitions (one system the other just files) and freed up ~25 GB to play around with. made an extended partition from the free space with two separate ~12 GB ext3 and a swap. This is where I then installed mint specifying in manual partition part of install that one of those ext3 was to be mounted as / and the other as /home with swap being detected automatically. no visible problems so far. Install finished successfully. restart with CD ejected (nice touch)... then:

i get this when the screen goes from Dell load to mint picture with the clock yoke in the background:
/ ----- pstk------------------rstk--- \
: :
: :
: :
: :
:0 5ffae. a :
:1 5ff8a. a :
:2 2c244. 4 :
:3 147. 9: 0: fffffff. 5:
:4 a. 1: 1: 1462. 5:
\--------------------------------------/

pressing enter twice brings me to the grub menu where  things look normal again:
linux kernel
linus kernel (recovery)
linux memory test

WinXP

WinXP loads fine and runs perfectly well. But when i go to linux:
 At first i couldnt go anywhere but the shell. Some kind of UUId problem which I appeared to fix by commenting out the UUIDs in /etc/fstab and uncommenting the sda5-6. 
After this got to the normal login for mint, entered user name and password and got the permission 644 error message for .dmrc file (which doesnt exists???). Appeared to fix that with a chmod 644 /home/user but then got the GTK+ setuid problem which I just havent been able to fix...

Cant find anywhere where it explains the problem or seems to fix it in a way which corresponds to my specific problem. 

Any help/advice/suggestions greatly appreciated

---

### Post by timbosity on 2008-02-29
Okay. So I just wiped everything clean and decided agaisnt mint (maybe therein lay the problem). Went with Xubuntu cos thats what I have on my laptop and overall im pretty happy with it.Same thing happens when it comes to login time re: permission error and then GTK+ setuid getuid problem. It sounds like this is a problem with the computer so... Could it be that Dell utility FAT16 bit at the beginning of the hard drive? There seems to be a problem with the fsck utility detecting long names or something or rather???
Anyone?:confused:

EDIT: At least now it becomes a Ubuntu problem :) maybe Ill get somewhere....

---

### Post by dstew on 2008-02-29
Sounds like something to do with the computer/BIOS/controller setup. You can look at the hard drive characteristics using the program [ hdparm]("http://linux.die.net/man/8/hdparm"). Maybe there will be a clue there. Do```
sudo hdparm /dev/sda3
```or whatever the device name is. Also, post the fsck error message to the forum. Strange problem.

---

### Post by timbosity on 2008-02-29
Okay. Ive gone and done a few different installs because 1 i didnt have the xubuntu CD with me and i wasnt going to burn another one and thought what the heck ill try out kubuntu in the meantime.
This happenned when i was installing at the manual part:

[http://ubuntuforums.org/showthread.php?p=4429072#post4429072](http://ubuntuforums.org/showthread.php?p=4429072#post4429072)

So i just cancelled and did the guided way and it worked fine and dandy and now i have kubuntu on my desktop. only problem is that I havnt really solved problem of having a separate / and /home partition and well mint still dont work...

So this thread is for how far I got after the manual install ie ignoring the message of the thread above and going on with the installation and the other thread could point to the original source of the problem. Maybe.

---

### Post by timbosity on 2008-02-29
oh yes and this is output from hdparm:

/code
/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 156250000, start = 0

/dev/sda1:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 112392, start = 63

/dev/sda2:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 50058540, start = 112455

/dev/sda3:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 21478905, start = 134753220

/dev/sda4:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 2, start = 50170995

/dev/sda5:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 20482812, start = 84180663

/dev/sda6:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 2104452, start = 132648768

/dev/sda7:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 32499369, start = 50171121

/dev/sda8:
 IO_support    =256 (???)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 9726/255/63, sectors = 1510047, start = 82670553
/end

---

### Post by timbosity on 2008-03-03
ok.

Just an update. Basically couldnt fix the problem. so i just wiped the extended partition clean and let ubuntu guided install work its magic on largest contiguous free space, not a bother. Still dont understand what went wrong ie why did it install fine like that and not with specific / and /home partition but hey, at the end of day i have linux at work so no more complaints... One day ill get a working / and /home partition, one day...

---

### Post by dstew on 2008-03-03
Thanks for the update.

---

