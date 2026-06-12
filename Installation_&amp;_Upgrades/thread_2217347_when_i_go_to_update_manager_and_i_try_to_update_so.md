---
title: "when i go to update manager and i try to update software update it wont work help!!!!"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by joshua20 on 2014-04-16
so i boot up ubuntu for the first time ever      i wached some youtube videos that said to go to update manager to update software so i did that but when i press install updates a messege comes up saying this                  Not enough free disk space

The upgrade needs a total of 608 M free space on disk '/'. Please free at least an additional 469 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               so i thought that all i have to do is go into windows operating system and uninstall some things in there but i did just that and then came back to ubuntu and it still says the     same thing  I NEED HELP PLEASE

---

### Post by lisati on 2014-04-16
Deleting stuff from Windows probably won't be of much help with the amount of space available on your Ubuntu partition.

First of all, this might sound obvious, but have you emptied Ubuntu's trash yet?

Another thing to keep in mind is that temporary files are generally deleted when you reboot Ubuntu: sometimes this can help.

---

### Post by joshua20 on 2014-04-16
i did restart like 5 times how do you empty trash    i am a newbe PLEASE HELP ME!!!!!!!!

---

### Post by 23dornot23d on 2014-04-16
Open a terminal in Ubuntu and type in lowercase (DF -A)

**df -a**

then paste back what it shows you here please.

---

### Post by joshua20 on 2014-04-16
and one more thing when i try to download any thing from the ubuntu software center it says         Package operation failed    The installation or removal of a software package failed.

PLEASE HELP ME!!!!!!!!!!!!!!!!

---

### Post by joshua20 on 2014-04-16
it says command not found

---

### Post by 23dornot23d on 2014-04-16
df

space

-a

---

### Post by joshua20 on 2014-04-16
Filesystem       1K-blocks     Used Available Use% Mounted on
/dev/loop0         2721217  2706577     14640 100% /
proc                     0        0         0    - /proc
sysfs                    0        0         0    - /sys
none                     0        0         0    - /sys/fs/fuse/connections
none                     0        0         0    - /sys/kernel/debug
none                     0        0         0    - /sys/kernel/security
udev               1526216        4   1526212   1% /dev
devpts                   0        0         0    - /dev/pts
tmpfs               614316      864    613452   1% /run
none                  5120        0      5120   0% /run/lock
none               1535788      376   1535412   1% /run/shm
/dev/sda1         78148160 57853308  20294852  75% /host
gvfs-fuse-daemon         0        0         0    - /home/lordlundi/.gvfs
lordlundi@ubuntu:~$ `

---

### Post by 23dornot23d on 2014-04-16
Wubi install and 2.7 gig for the OS ........ am surprised it runs ........ its full already ..... 
not sure what you will be able to free up there ........ needs someone to answer this
that uses wubi


> 
/dev/loop0         2721217  2706577     14640 [SIZE=3]**100%**[/SIZE] /


That must be the minimum you can get it running in ........

Yet you have 20 gig free space on sda1 ........ not sure how you can get as much as 600 meg back .... but you may
Try looking at the link below ( there is some useful information there I think ) - until someone comes along that uses wubi 

[http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta](http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta)

---

### Post by joshua20 on 2014-04-16
what do i do about the  ubuntu software center it wont let me download anything???????

---

### Post by 23dornot23d on 2014-04-16
I have a feeling that you need to increase the size of the area you are working in but with not ever using a wubi install 

all I can do is point you to links to go read ........ this may be the thing you need to do here .........

[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

But read through it carefully .........

As I said previously .... needs someone who uses wubi to give you some sound advice ...... but from what I see
that install has run out of space because it needed to be much larger to start with ....... the above link
seems to give information on increasing it ....... 

But it says to make a backup if you do try this way ........

The software centre will probably only start working again if you can free some space up ........ but how much you need
is not clear ......


Try these commands first 

( maybe they will get you enough to get the software centre working - 

[COLOR=#ff0000]**but dont download anything else till you make plenty of room**[/COLOR] - possibly with the link I gave above - but check it out with others that use wubi

( I am surprised it did not warn you at 1 gig ...... the system used to say you are running low on disk space )

[B]sudo apt-get autoremove
[/B]
**sudo apt-get autoclean**

---

