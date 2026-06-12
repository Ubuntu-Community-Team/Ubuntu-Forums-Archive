---
title: "Upgrade Failure"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by mayavi2011 on 2012-01-14
Hi,  I tried to upgrade my system from 11.04 to 11.11 and I now can't login to access my existing files (but I can login as 'Guest' which is less than useless).

I have tried many things without success.

If I do the 
     ls /home 
Sometimes I get thecorrect response

But if I try to change the password all I usually get is 'unrecognized user' .:confused:

Have I screwed my system and am I about to lose 1TB of data?

Any suggestions?

I am  still a of a novice with Ubuntu and I would like to stick with is but this problem is starting to leave a nasty taste in my mouth.:(

---

### Post by dino99 on 2012-01-14
This might help:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/)

---

### Post by mörgæs on 2012-01-14
Buntu is great - only problem is that people are encouraged to upgrade online, which can be risky, to say the least.

More advice in the link in my signature.

---

### Post by mayavi2011 on 2012-01-14
Thanks for that, but I have already tried those suggestions.
The problem is that whilst ls /home gives me my user name, passwd insists that that username does not exist :-(
I don't know enough to be able to go back to a previous version.
So I'm really looking for some very specific help on just what to do.
Being a newby/novice does not help :-(

---

### Post by bluexrider on 2012-01-14
the first response would be YOU HAVE DATA BACKUP....RIGHT!.

Question is the critical data. Is it stored in your "/"home folder? If so are you able to move it. 

Using a LIve CD/DVD boot into Ubuntu. Check the size of the "/"home folder . Using Gparted or another partitioning tool shrink the Main Partition as to leave a slightly larger space than that of your current  "/"home folder. 

Format the new partition to EXT4 and move the data from "/"home to the new partition.

Now reinstall the Ubuntu distro to the shrunken partition.

That would be my plan. What you choose to do is yours.

---

### Post by ryadav on 2012-01-14
i stopped upgrading after i've messed up my system to useless a few times!!!

if you got /home on a separate partition you might be able to install the latest release and get up and going
however i would still backup

if you are able to use another PC, take a look at SystemRescueCD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
it will allow you to boot into an existing system and perform backup of vital file and folders, 
you can also partition the drive and or format if you want

---

### Post by mayavi2011 on 2012-01-25
Thanks for all your comments; but the problem has now become a little clearer. I will list the salient points of my system and problem which should address the various points raised (and please remember that as a novice/newbie my ignorance of linux/ubuntu is profound):

[It has been suggested that perhaps I should be starting a new thread 'rescuing files from a crashed RAID installation' - but I will continue in here in the short term].

 1) My system consists of a 500GB drive for the operating system and application files.
but; and here's the rub:-

2) All data is stored on two RAID 6 arrays; (however, for technical reasons only one array is connected at present).

3) It would appear that during the last upgrade process, using live CD, instead of installing on the 500GB HD (as it should have); for reasons I don't understand it would appear to have attempted to have used both the single 500GB drive plus one or more partitions on the connected RAID array :confused:
(I accept that all these problems may just be due to my ignorance :( )

4) The result of all that is that I can no longer access the RAID array even if I run a separate live CD session and (due to ignorance ?) I cannot open a terminal window (in either ubuntu 11.10 or fedora) to paddle around in the file system. :( 

However, I am now trying SystemRescueCD, I'll let you know the outcome.

p.s.
Before I try the SystemRescue CD, I decided to try again to install ubuntu 11.10 from the live CD; interestingly enough, the live CD only now accepts the RAID array for installation but does not see the 500GB drive :confused:
But if I just run the live CD it only sees the 500GB drive and cannot see the RAID array :sad:

I think confused is the best way to describe me at the moment.

Thanks
Brian

---

### Post by mayavi2011 on 2012-01-26
Further to my previous message:-

1) I tried SystemRescueCD - unfortunately my hard drives are ext4 and the version of SRCD I downloaded would only open ext 3 but not ext4 :(

2) I then tried RIPLinux_13.7, but I could not get it to run, so then I tried PartedMagic_2011_12_30  and joy of joys :)  PartedMagic can see all my hard drives (including RAID arrays) and nearly all my files :D

3) However, due to my abysmal lack of knowledge of linux/ubuntu I have no idea of where to find four(4) critical files:- namely  firefox history; firefox bookmarks; thunderbird address book and thunderbird mail (inbox and sent).
But if I can locate those 4 files etc, I can just copy all my stuff to other drives, reformat and do a clean install of ubuntu :D

So the question now becomes, where do I find those files etc and more importantly how do I copy them :D

Thanks again,
Brian

---

