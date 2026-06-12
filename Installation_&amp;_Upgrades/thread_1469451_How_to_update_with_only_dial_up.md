---
title: "How to update with only dial up"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Silvertones on 2010-05-02
I ordered the CD but I guess you can't update from that. I was gonna go to the library but they say it takes in excess of 4 hours. I guess the option is the alternate CD but there are a couple of options and not sure which one.

---

### Post by colintivy on 2010-05-02
Await a live CD from the likes of Linux Format and do a clean instal. It is all a keyboard job then,and no risk of corruption and time-wasting on a download. Get your /home on a separate partition if you have not done it already and a back-up copy of it on a USB stick as an insurance.


colintivy

---

### Post by Silvertones on 2010-05-02
So if I move my /home to a seperate partition and use the clean install I presume it'll function sort of like an upgrade?
I have a duel boot at the moment with XP. I'll search for a tutorial on how to move /home first before I install 10.04. If you can point me to that please do.
And Thanks

---

### Post by Silvertones on 2010-05-02
OK I succesfully created and formated a partition for moving the /home but now do I still use the live CD to move it or can I do it while booted up normally. The reason I ask is that I want the Internet directions in front of me so I can copy and paste terminal commands. With dial up I can't get on line with the live CD.
Is there a more graphical way to move it?

---

### Post by Silvertones on 2010-05-02
Moving the darn /home to the new partition is awfully cryptic to me. I see were I'll not loose some stuff but what about the confg files for wvdial, samba. Won't these get hosed with a fresh install even if /home is on another partition?
PLEASE help me move /home!!!!

---

### Post by Silvertones on 2010-05-02
Well it appears I moved it with one of the tutorials. When I used GParted I labeled the new partition Home. After that when I went to Computer I had:
1. Files system
2. Windows
3. Home
Showing the 3 major partitions
Once I went through the tutorial the one labeled Home is no longer visible in Computer. I think this is right. I now have a home folder & a home_backup folder in computer/filesystem. I think this is correct also cause the #3 Home had a folder called "lost&found" and so does the new home.
How can I tell though that home is actually on the new partition? When I right click on it the volume is unknown. BTW the used space + the available space matches the new partition size I set.

---

### Post by Artemis3 on 2010-05-02
Just so you know, downloading files and applying updates are two separate steps, which is not so obviously seen.

So you go to the library, and use update-manager. It will tell you to download 800MiB worth of data, that it will takes 6 hours, blah blah, just ignore and continue. After 2-4 hours (whatever they allow), cancel and leave, go tomorrow and repeat. The parts you downloaded are not lost and will continue downloading only the rest.

Eventually you will complete downloading all the files and can go on with the second part (its long, might as well do it disconnected). This second part is the one which should not be interrupted, but the first (downloading packages) part can be interrupted and resumed as many times as you need.

You can also upgrade from the Alternate Cd or the DVD. If your main language is not english, consider the DVD image (and its also a live cd).

---

### Post by Silvertones on 2010-05-03
I succesfully moved my /home folder to another partition. I verified this by using the live CD. I have 4-6 weeks before the CD comes from Canonical. At that point I'll decide whether to update or or clean install.
BTW a while back I had to DL 2G of a program that I'm a Beta tester for. It only took 2 hours. I should be able to DL 700meg in less then an hour.
I do have a question. When I do normal periodic updates it DL the packages and then immediately starts the install. If I do the upgrade how do I stop this from happening so that I can go back home and then do the install.

---

