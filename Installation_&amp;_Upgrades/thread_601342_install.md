---
title: "install"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by goslings on 2007-11-03
When intalling Ubuntu 7.1 pop up finds disk and USB 2Gb 
If you select to use USB, it thinks and then returns back to the screen highlighting the disk it found?
Why ?
I want to install this live CD version to the USB ?

regards

---

### Post by PmDematagoda on 2007-11-03
You can install Ubuntu to the USB if you want it to. Otherwise, just install it to the HDD.

---

### Post by goslings on 2007-11-03
thanks, but it reports
prepare disk space
Guided
scsi1 - 160 - Gb
scsi3 - 2GB USB
I select the USB

it reports setting up partioner .... then thinks some more and when the hourglass comes back it has the dot against 
scsi1 - 160 - Gb 
highlighted 

and wants me to select fwd - so will it not then try to do this op on the scsi1 160Gb disk instead 
Cant see how this installs to USB - will I be able to save then data & update software etc to USB ?
Then when I feel comfortable use it to install to internal HB (dual boot)

be kind i'm new to linux (but not Sgi UNIX)

---

### Post by goslings on 2007-11-03
bit the bullet, and went to step 7 
it said it was to install to scsi3 - which was the USB
but as a newbie it was confusing that it returned back to a dot alongside Scsi1 (HD) after I had selected the USB. 
Its now installing to the USB
Progress ....
ah no - does the USB have to be empty - will this process wip the USB before hand ?

---

### Post by PmDematagoda on 2007-11-03
If you wish to install Ubuntu to a USB drive, you will definitely need something bigger than 2Gb, installing Ubuntu on a 2Gb USB drive is very risky.

---

### Post by goslings on 2007-11-03
why ? 
liveCD is only max 700Mb, maybe it is compressed and ran in memory  but max that will be 2Gb as PC tend not to have more, and assuming you want to do something with it much less ?
I read all over the place people installing to USB memory sticks + USB HD drives (granted much larger)
regards

---

### Post by PmDematagoda on 2007-11-03
Most likely you will only be able to run only Ubuntu and it's default applications, but another risk is the fact that you cannot let anything happen to the USB drive while using the OS.

---

### Post by goslings on 2007-11-03
so would I be best just to install to the HD in the machine?
Is this best done to continuous space having selected the scsi1 160Gb drive 
-All windows stuff remains in tact 
thanks for your  patience

---

### Post by PmDematagoda on 2007-11-03
No, you will need to partition the hard drive in order to keep Windows XP.

You can use Gparted, it should be found in System>Administration as Partition Editor.

But before you do the partitoning, you should defragment your Windows XP drive first.

---

### Post by goslings on 2007-11-03
I did the defrag last night, but I assumed that the install did the partitioning for you ?
Is this an operatiion that is documented anywhere ?
Is it best to choose "continuous" 
regards

---

### Post by PmDematagoda on 2007-11-03
If you choose continuous then most likely all of the free space would be used. Use the partitioner I told you to resize the Windows partition and then use the newly available partition for Ubuntu.

---

### Post by goslings on 2007-11-03
I am a bit scared of this as reading things makes me think it is not a easy as it sounds
here is an png of th Gparted after it scans my system
What should I do now
thanks for your help

---

### Post by PmDematagoda on 2007-11-03
It seems that Gparted cannot resize NTFS volumes. I'm very sorry, but I'm not sure when it comes to resizing NTFS volumes, most likely someone will come along and help you out with your problem.

---

### Post by goslings on 2007-11-03
thanks anyway 
hope someone can help & chip in 
brilliant forum post, cup of T, and there is a response!
maybe I should use it from USB for now?
fantastico

---

### Post by goslings on 2007-11-03
I'm just reading around and I've found this
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
this suggests that I choose the 1st option and the install takes care of it all to present me with a dual boot system 
I assume this works for NTFS systems?
regards

---

### Post by PmDematagoda on 2007-11-03
Yes, I did not think of that, how silly of me. That will work even on NTFS volumes. Use that option and pick a fair percentage, not too high and not too low otherwise you might damage XP or Ubuntu will not have enough space.

---

### Post by goslings on 2007-11-03
when you say a fair % - thats a fair % of what ? free space ?
thanks

---

### Post by goslings on 2007-11-03
uhm -step 5 of install is JUMPED ???

step 4 of install
how do you want to partition disk
selected SCSI1 (0,0,) sda - 160 GB ATA WDC WD1600BB-22B
step 5  
????? is jumped 
step 6
who are you data
step 7 reports
see image 
NO mention of partition %
+ will this damage my win xp install 
regards

---

### Post by goslings on 2007-11-03
why step 5 of install missed?
why no mention of this aspect of the install in any 7.10 documentation
[http://www.psychocats.net/ubuntu/installing#partitioning]("http://www.psychocats.net/ubuntu/installing#partitioning")
regards

---

### Post by PmDematagoda on 2007-11-04
Step 5 is the partitioning part and is given to those who chose "Manual", since you didn't you don't face that part, and the percentage I meant was the percentage of the hard disk, so you may have to define a percentage of about (I'm suggesting) 50-70%.

---

### Post by goslings on 2007-11-04
> **PmDematagoda said:**
>  ... and the percentage I meant was the percentage of the hard disk, so you may have to define a percentage of about (I'm suggesting) 50-70%.

Hi again
It does not ask for a % at any point up to step 7 ?
which is the point of install (see previous image) ? 
after which I assume it installs and asks no more questions
regards

---

### Post by PmDematagoda on 2007-11-04
I believe you should set the correct percentage in step 4. And once you reach step 7 you are ready to install, and no more questions will be asked.

---

### Post by goslings on 2007-11-05
> **PmDematagoda said:**
> I believe you should set the correct percentage in step 4. And once you reach step 7 you are ready to install, and no more questions will be asked.
Thats just the point it does NOT ask in step 4 for the % (ubuntu 7.1)
???

---

### Post by PmDematagoda on 2007-11-05
Could you please post a screenshot of Step 4.

---

### Post by goslings on 2007-11-05
best bet to look at 
[http://ubuntuforums.org/showpost.php?p=3705655&postcount=1]("http://ubuntuforums.org/showpost.php?p=3705655&postcount=1")
cheers

---

### Post by PmDematagoda on 2007-11-05
Well, I can't make much headway into this install from here, I am really sorry about that. The best advice I can offer right now is to get a secondary HDD and install Ubuntu on it.

---

