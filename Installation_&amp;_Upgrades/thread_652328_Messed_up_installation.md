---
title: "Messed up installation"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by laxguy on 2007-12-28
Ok, so I've been having some trouble with this new Gutsy install (7.10). Previously I had Fiesty installed on a small 8 gig hard drive, but i got a new hard drive for christmas so i wanted to install the new version on this nice new harddrive...but I'm having some trouble...

I burned a nice new CD, and it didn't work.. it brought me to this screen that said BusyBox 1.1.3 etc.. I've seen posts on here about it so I'm guessing you guys know what comes with it, but the posts i've seen haven't related to mine.

I can't even get to the actual OS because the BusyBox thing takes over and i can't get past it. I tried burning 2 more LiveCDs and they all do the same thing. I have also tried to use the alternate CD, and that just confused me to death, it looked like it was working (slowly) until i got to the partitioning part, and then it froze..

If you need any more imformation let me know, and I'll see what I can do to provide it. (Note: I'm still kind of a linux newbie, but I'm trying to learn) Any help is much appreciated.

---

### Post by Pumalite on 2007-12-28
Try to boot a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
And post: sudo fdisk -lu
Also: lshw
From the terminal

---

### Post by laxguy on 2007-12-28
ok..soo....i burned a knoppix livecd and i booted up all fine and it worked great, but i couldn't get on my wireless network therefore i couldn't post the results of those two tasks....they also wouldn't save in openoffice..so i couldn't get the info back... i don't know what else to do..

---

### Post by taurus on 2007-12-28
Try to burn the CD at a slower speed like 4x instead of the default speed.

---

### Post by laxguy on 2007-12-28
i did that with one of my many CDs..same thing..

---

### Post by Pumalite on 2007-12-28
From the Knoppix Terminal, post:
sudo fdisk -lu
lshw
You don't need connection to the Internet or Open Office.
Do you know how to find the Terminal?

---

### Post by Pumalite on 2007-12-28
What are your specs and what iso are you using?
You might need the Alternate CD.

---

### Post by laxguy on 2007-12-28
i did use fdisk, but it didn't make sense to me, so i was assuming you would want to know what it said...and thus i would need the internet to post it.

i have tried the ubuntu 7.10 iso two times, the alternate CD once, and now this knoppix cd (the only one that worked was the knoppix)

---

### Post by Pumalite on 2007-12-28
I hope you can somehow get wired to the Internet while installing with the Alternate CD, because that might work.

---

### Post by laxguy on 2007-12-28
the alternate CD started t work until i got to the part where i need to partition my drive..then it just froze on me...and i had to stop

---

### Post by Nebutron on 2007-12-28
It may be helpful to have more info about your system.  What type and size of hard drive?  What CPU?  What memory?  Graphics card?  That may give some people much smarter than me some ideas.

---

### Post by Nebutron on 2007-12-28
> **laxguy said:**
> the alternate CD started t work until i got to the part where i need to partition my drive..then it just froze on me...and i had to stop

What portion of the disk did you set it to partition?  Are you trying to set up a dual boot?  If so, I would recommend allocating at least 40 gigs to Ubuntu.

---

### Post by laxguy on 2007-12-29
i have a 120gb Western Digital hard drive that has vista running on it, and i recently got a new 80gb WD hdd (both HDD are SATA if that helps), that im trying to put ubuntu on. i have a Intel Celeron D (3.46 ghz) processor.. 1 gig of RAM and a GeForce 8400 graphics card.

I didn't even get a chance to tell it what to partition because it froze up..

---

### Post by halw on 2007-12-29
Try downloading the live cd version of gparted and see if you can format your new drive with that.

---

### Post by Pumalite on 2007-12-29
If you are using Vista, you have to allocate space for Ubuntu with the Vista partitioner first; otherwise Vista will no let you run anything in that computer.

---

### Post by Nebutron on 2007-12-29
> **laxguy said:**
> i have a 120gb Western Digital hard drive that has vista running on it, and i recently got a new 80gb WD hdd (both HDD are SATA if that helps), that im trying to put ubuntu on. i have a Intel Celeron D (3.46 ghz) processor.. 1 gig of RAM and a GeForce 8400 graphics card.

I didn't even get a chance to tell it what to partition because it froze up..

> **Pumalite said:**
> If you are using Vista, you have to allocate space for Ubuntu with the Vista partitioner first; otherwise Vista will no let you run anything in that computer.

Okay,  I think we are onto something here.  I would take to heart what Pumalite said above.  Hopefully allocating the partition space with VIsta will do the trick.  If not, might have to look at the configuration of your two hard drives.  Lets us know if you are still stuck.

---

### Post by laxguy on 2007-12-29
in the vista partitioner it is labelled as "74.50GB NTFS Healthy (Active, Primary Partition)" should i partition it like i would with ubuntu? (my friend said a 2gb swap and 20 gigs as mountpoint/ and the rest as mountpoint/home or something lke that) or waht exactly are you saying i need to do, when you say i need to allocate the partition space?

---

### Post by Pumalite on 2007-12-30
When you 'allocate' space for Ubuntu, you create a new partition that you can format in any way. Ubuntu does nor install in 'unallocated' space.

---

### Post by laxguy on 2007-12-30
Then the drive has been allocated this whole time, as one large 74.5 gig piece.

---

### Post by Nebutron on 2007-12-30
> **laxguy said:**
> Then the drive has been allocated this whole time, as one large 74.5 gig piece.

Okay.  From one of your earlier posts, it sounded like you were trying to use one of your drives for ubuntu and the other drive for the other OS, Vista if I recall.  I don't have the answer as to why this happens, but found that I could not have two hard drives connected to my PC with two different operating systems.  I had Gutsy Gibbon on one and XP on the other.  IF I left both connected, It would crash every time.  I solved the problem by just doing a dual boot with both XP and Gutsy on the larger of the two hard drives.  It may be that you could run the two hard drives in a RAID 0 configuration and have the same result.  You may also be able to wipe the 2nd hard drive and still use it once you have completed a dual boot on the main drive.  

Others with more experience with multiple drives may have better ideas about how to do this, but that's what worked for me.  :)

---

### Post by jken146 on 2007-12-30
> **Nebutron said:**
> Okay.  From one of your earlier posts, it sounded like you were trying to use one of your drives for ubuntu and the other drive for the other OS, Vista if I recall.  I don't have the answer as to why this happens, but found that I could not have two hard drives connected to my PC with two different operating systems.  I had Gutsy Gibbon on one and XP on the other.  IF I left both connected, It would crash every time.  I solved the problem by just doing a dual boot with both XP and Gutsy on the larger of the two hard drives.  It may be that you could run the two hard drives in a RAID 0 configuration and have the same result.  You may also be able to wipe the 2nd hard drive and still use it once you have completed a dual boot on the main drive.  

Others with more experience with multiple drives may have better ideas about how to do this, but that's what worked for me.  :)

You should be able to install the 2 OSs on separate drives with no problem.  If Vista is on one drive and you have another (empty) drive that you want to put Ubuntu on, then go ahead and use that empty one -- it'll be easier than trying to resize the Vista partition.

As for the live CD, did you run the CD integrity check?  Did you try safe graphics mode?

---

### Post by laxguy on 2007-12-30
Yes you are correct Nebutron, i am trying to run both on seperate drives, and I don't have enough room on the larger drive to have both, unless I do some major moving around of stuff, and it just seems easier to use two (but i can always do that as a last option). Also I have had fiesty on two seperate drives and it seemed to work fine..so I'm not sure wahts up with this.

@ jken146, i have tried the integrity check, but it also brings me to the busybox shell thing, as does the safe graphics mode.

---

