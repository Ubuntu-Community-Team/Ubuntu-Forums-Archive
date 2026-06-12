---
title: "[SOLVED] Its always windows that breaks"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Sabar on 2007-12-21
Hia guys. well tonight I am starting the reformatting and general clean up of my Alien.

I have been running a duel boot computer for almost a year now and I can honestly say I have been real happy with Ubuntu. In fact I even got my hands on an old dell just so I could run a totally Linux system.

Unfortunately I have to admit on my main computer I have to duel boot even though I only ever go to windows on very rare occasions.

Now here is my problem.

Last time I reformatted I did just as I was told to do. put in windows followed by Ubuntu.

Everything went great until I noticed that windows didn't see my second hard drive. ( which in windows speak was always D

Ubuntu of course worked perfect.

Now here I am upgrading to Gutsy and I figured I would try to fix windows by reformatting. I have two drives C and D. how ever now D is called H

the only options I have on my resource CD are to delete partition and install can I delete partition of H to make it D again? any ideas how to fix this? If I do delete it how do I get it from unallocated  to formated NTFS with out installing Windows?

If my ramble is making no sence please let me know thank you
thank you every one 

Sabar

---

### Post by heatpumpcontrol on 2007-12-21
I believe that MSFT site has some help on this. You can do all of those changes in the registry or something like that. 

OH wait.... 

Right click My Computer -->Manage -->Disk Management.

Right click on the drive you want to change and unassign the drive letter first then do same thing and  assign the drive the letter you wish it to have... done

---

### Post by Sabar on 2007-12-21
Well I just finished the installation of windows and here is the part I dont get. Windows is not even seeing my second hard drive. the last time I tried to fix this ( please notice tried ) Under device manager It see's my second drive but no were else.

This just isnt makeing any sence to me. although I am going to try what you said heatpumpcontrol, and thank you for your responce

---

### Post by heatpumpcontrol on 2007-12-21
> **Sabar said:**
> Well I just finished the installation of windows and here is the part I dont get. Windows is not even seeing my second hard drive. the last time I tried to fix this ( please notice tried ) Under device manager It see's my second drive but no were else.

This just isnt makeing any sence to me. although I am going to try what you said heatpumpcontrol, and thank you for your responce

seems like Windows isn't assigning a drive letter to your partition/hd for some reason. Try doing it manually as mentioned before and see what happens then.

---

### Post by zero-9376 on 2007-12-21
what type of partition is on the second hard disk, windows will only read ntfs and fat, you can us disk management to see the partitions on the disk and whether or not windows reconises them

---

### Post by heatpumpcontrol on 2007-12-21
> **zero-9376 said:**
> what type of partition is on the second hard disk, windows will only read ntfs and fat, you can us disk management to see the partitions on the disk and whether or not windows reconises them

Gosh forgot about that.. since only using linux now..... lol. Well using VirtualBox and viewing ext3 partitions only as shared folders so at that point it doesn't matter.... Good one.

---

### Post by Sabar on 2007-12-21
OK I went to disk manager like I was told. I tried to reassign a letter how ever that was not an option so I deleted the drive, which was an option. then I went to my computer and yahoo it was there even with the proper letter tagged to it. now at this point I tried to open it which i couldn't do so i tried to format it and was told basically something must be trying to use it.

So now here I am with the resource CD in the drive. I  just deleted the partition ( D Drive ) and repartitioned it. ( the whole thing as D drive ) going to see what this does

Thanks for the help guys cant wait to see what happens from here

Oh PS the drive is NTFS

---

### Post by Sabar on 2007-12-21
Well I just restarted the computer and tried to open drive D. I was promptly told that the disk was not formatted so I clicked OK to start formatting it. and lone behold it actually started formatting the drive!!

OK guys looks like I may be on the right track. you know I was thinking of doing this earlier but I was just to scared that I would mess something up. how ever its not done yet and I haven't saved anything to that drive yet so I guess we will see. 

Thanks for the responses every one, glad to know I can find people willing to give Rednecks  like me a helping hand. I cant wait to get all this done so I can get Gutsy on my Alien. like I said in my original post I only use windows for a few things. or it wouldn't be there at all. god knows they're forums are not as easy to use as these are. Thanks again 

Sabar

---

### Post by twist2b on 2007-12-22
are you running xp or vista? if its xp... then just remove xp and use virtual box :P way better for you i promise..... also you can download alcohol 52% free version and create a virtual drive called D:
that just might fix the problem... or have one called G:
in theory you can have ALOT of drives.... so losing one isnt that bad... just make another :P and add the important stuff that makes it read CDs and DVDs...

---

### Post by Sabar on 2007-12-22
What I finally did was delete the drive then I put my resource CD in and deleted the drive in set up re deleted the drive and set it so the whole thing was a new partition. when that was done I went back to my computer went to open the drive and got an error saying to format it. left the computer format it and now it looks like everything is working good.

boy Ubuntu has spoiled me I have to look up Windows drivers. 

Thanks every one
Sabar

---

### Post by heatpumpcontrol on 2007-12-22
> **twist2b said:**
> are you running xp or vista? if its xp... then just remove xp and use virtual box :P way better for you i promise..... also you can download alcohol 52% free version and create a virtual drive called D:
that just might fix the problem... or have one called G:
in theory you can have ALOT of drives.... so losing one isnt that bad... just make another :P and add the important stuff that makes it read CDs and DVDs...

Yes, I would recommend this option!!! Works great. Follow twist2b's advice. You won't regret it. Also, if you have some apps that you can just run in wine then use it for your once in a while Window's apps that can run in wine.

---

### Post by Sabar on 2007-12-23
Running a virtual machine wouldn't be a bad idea if I wasn't married . I think she would kill me. its been a year now of running mostly Ubuntu and she still asks when I am going to stop "experimenting"

---

