---
title: "Trying to get dual boot going but can't install"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by biffspagnuts on 2011-09-10
Hi 

I have been having some problems with my Ubuntu install that I was hoping to get some help with.

I am trying to keep my windows XP and install Ubuntu (mythbuntu) on the same hard drive. The desktop is P4 HP Pavillion from 2003. I have been using it as a HTPC or whatever it's called. I have upgraded the grapics card to a Saphire HD3450 and added some more ram in hopes of playing some blueray/HD disks It doesn't work well in windows so I thought I would see how it does with Ubuntu.  And I just wanted to see what Linux is all about maybe build a new PC and do away with windows altogther. 

  I tried playing around with the partitions so now there are a total of 4 the two windows and I made two more for Ubuntu, which are 4GB (for the virtual memory?)  and the other is maybe 10GB. I am confused on how I should be labelling these with GParted. I have tried just about all of the choices with no luck. None of them let me get past the root file error below. 

Now I am trying to do this with Ubuntu on CD, and it will only boot from Cd after a lot of restarts. (Should I just pick up another harddrive to put Ubuntu on?) Most of the time it is just a black screen that only the mouse works in. I can get it to work more consistently if I start in the graphics safe mode, but the screen resolution is way off and super small. 

My big problem is with the installation itself
At this point when I try the install I can proceed to step 5 of 7  preparing the partitions. I keep getting an error that there is "no root file system defined" . I have no idea what I am doing wrong here. 

Any suggestions for a rookie?

Thanks

---

### Post by dabl on 2011-09-10
Don't bother labeling the partitions for Ubuntu.  If you were setting it up on its own hard drive for serious long term use, I would advise you to make separate partition for your user data and label it "DATA", but that is unnecessary for your purposes. In gparted, for the 4GB swap partition choose the "linux-swap" filesystem, and for the 10GB Ubuntu partition, choose "ext4".  Then choose "Apply" and you're done with that.

Then boot a Live or Alternate (my favorite) Ubuntu CD, and when you get to the part about partitioning, choose "manual", and then it will show you the available partitions and it will automatically find the swap partition, and it should automatically choose the remaining ext4 partition, but be careful and make sure it does choose the ext4 partition for "/" (the Linux filesystem root).

That should be all you need to get started.  The web is full of guidance, including this one which has a section on dual booting: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Blasphemist on 2011-09-10
dabl is right that you should go into "something else" which is the manual disc allocation option and you need to be sure to set the mount point for your linux partition to / (root). Does mythbuntu install like the other ubuntu's where you have the option to try ubuntu before you install? If it does, you could do a screen shot from gparted and get into these forums and attach it to a post. We could then look at your partitions. I'll also offer this great site for dual boot installation instruction.
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by biffspagnuts on 2011-09-11
Great I got going now guys. Thanks for the help and for the links

And Blasphemist I guess it's the same. I might of clicked on the button somewhere but in the live CD everything says ubuntu. I assume the mythbuntu comes later as some kind of add on?

---

