---
title: "Different Dual Hard Drive Question"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Jerksticks on 2010-02-10
Hey this is my first post, so hello to all who pass through this thread!. 
 
I'll get to the point.
2002 512 MB computer with 20 Gig C Drive and 60 Gig D Drive.
 
All the music/videos/papers etc from college up to now are on my D Drive on that computer. I use a new laptop to surf the web, but I do all my filesharing on the old pc. It has XP on the C drive and crashes all the time; usually I reinstall XP and it wipes out the C but not the D drive. My XP disc is scratched and won't finish the install, but it did erase my C drive completely; D and all its files intact.
 
Good news, time to try Ubuntu. The install process prompts me about doing the complete erase, and then shows me the two drives along with free space. I'm wondering if I select the smaller drive, will it still erase the larger D drive as well? What Im not sure about is whether I actually have 2 hard drives or just 1 big partitioned one. And what does the free space represent?
 
Thank you in advance to any who help, and looking forward to a life of Linux.

---

### Post by lindsay7 on 2010-02-10
Start up your computer with the ubuntu cd installed in the drive.  Chose the start option that says trail or something to that effect.  Do not chose the install option yet.  Go to the top of the screen and look on the menu bar click on system/administration and go down to the listing to Gparted.  Click on that.  This will let you see the drive or drives that are on your machine.  If you only have one drive it will be known as sba if you have two drive there will be an sdb. If there is just one drive it will be partitions like sda1, sda2, ect.  Same for the the second drive if there is one.  Make note of the drive and partition numbering.  When you get ready to install you can choose which drive to install ubuntu on and also which partition for that matter. During the install you will get a graphic depiction of the drive or drives and can choose from there. There is also a manual option too.

---

### Post by Mark Phelps on 2010-02-11
To be absolutely safe, simply disconnect the "data" drive and boot with only the other drive connected -- and then do the install.

After that is done, reconnect the "data" drive and boot.

Ubuntu will allow you to mount the "data" drive by selecting it under Places.

---

