---
title: "Did Ubuntu format my hard drive without me wanting it to? (****!)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by kongle on 2007-10-22
I am quite... scared... and I believe I have good reason to be. Here's the story:

I get back home from a long journey, eager to try the new Ubuntu release. I'd only tried Ubuntu 6.06 before, on another machine. This time I wanted to try it on a laptop, actually on the one I am currently using, a Dell Inspiron 6000 running Windows XP. I got an error message after 15 minutes of the Ubuntu install trying to do some partitioning. But that doesn't matter. The computer seems to be working fine still.

However, I proceeded by attempting to install Ubuntu on another laptop also running Windows XP, a Dell Inspiron 9300. I think the partitioning step where the last computer failed passed very quickly on this one. It was in the middle of what seemed to me the step where the computer does all the installation work that it hung up on the 9300. At around 50 %, after doing some "partitioning", I think, it failed to copy some files, and the install was aborted.

Still running Ubuntu from the CD, I tried to check the content of the hard drive. It seemed like there were two partitions, both showing mostly the same folders, like that of an Ubuntu install. No Windows-folder. I got scared. I restarted the computer, wanting to get back into Windows. No Windows. I got VERY scared. Then I remembered that during the partitioning step of the install wizard, I had two choices (on the other computer I had four). I had chosen the first option, avoiding the "manual" way which I remember not understanding much of when I installed Ubuntu 6.06 a year ago. I had heard that installing Ubuntu was now easier than ever, and that it would do the partitioning automatically for those who lacked skill and insight. I counted myself among them.

Now, later, I remember some words from the details of the partitioning alternative I chose. I believe it said something like "use all the disk". I admit doing this a little bit too quickly, but at the time I felt certain that this meant the Ubuntu installer would use all of the space on the disk that *was not occupied by the Windows-installation and all my family's personal files and folders*. After all this was the only reasonable option for newbies like me who lack the skill for installing Linux manually.

Now I have booted the Ubuntu CD again, on the problem computer (it required 30 minutes and A LOT of error messages this time). In the file browser, the only partition visible is "File System" containing two files. The Partition Editor shows two or three partitions: sda1 (big partition, "boot", file system "ext3", 2.5 GB used) and sda2 (2.89 GB, file system "extended", no space used), the latter, sda2, having sda5 (2.89 GB, "linux-swap) arranged under itself.

I guess... this means... that the content of sda1... is... the incomplete Ubuntu install, and that... Windows (which I don't care **** about)... and all my family's personal files and folders... are... gone?:cry:

Yikes.

In that case it's quite serious. Can you confirm that this is the situation?

And: Is there any way of retrieving those files? Or did Ubuntu format the drive?

If those files are eternally lost, it's very easy for me to get very angry at Ubuntu. I'm not, because I guess I was ignorant myself, but I'll have a hard time when I have to tell this to my family. My sister has been working a lot on a thesis which she should have ready for school soon. If this is gone, it is NOT fun.

So basically I wonder, why didn't Ubuntu detect the Windows install and warn me sufficiently of what it was about to do? I think it said something about the partitioning changes about to be done being irreversible, but if it was actually about to format a drive containing approximately 20 GB of files, it should've said so very CLEARLY. Also, it is dangerous to target Ubuntu at "human beings", or people who don't know much about computers, and during the partitioning step of the installation wizard only offering the options of "using all the disk" and doing it "manually" (which sounds scary to most).

Oops, I might've been jumping to false conclusions. I'm hoping for good news; that it didn't format my hard drive against my will.

But I'm pessimistic. Help please!

Best regards,
Seb-

---

### Post by dagrump on 2007-10-22
I could be wrong, but if you selected "use entire disk" , yes , YOU wiped the drive. This is not an issue with the operating system, this is operator error. Now some one might be able to help you recover your data, but I wouldn't bet on it.
Please from here on read & understand the directions, if you don't understand ASK some one.
Oh, your sister is going rip your ears off!

---

### Post by kongle on 2007-10-22
I am sorry, dagrump, and thank you for a nice welcome to the forums. As I already wrote, (1) I read the directions and thought I understood, but I was too quick, which means (2) I was stupid. I cannot help it now. I am feeling deeply like **** because I made a mistake, and I am asking for some help if there is anything that *can* help.

I believe I made a point regarding the formatting, though. I am pretty sure it didn't warn me about it. It warned me about partitioning the drive, which sounds to me like it will go about splitting it up, leaving the used space on one partition and unused on others, which I wanted it to, but if it was actually FORMATTING, I think it should warn the user very clearly. Some people are like me. Stupid.

If it DID warn me about formatting, I do of course pull this critique back, but I am pretty sure it didn't.

---

### Post by dagrump on 2007-10-22
As I said there could be some one that knows how to recover your data,but I don't have any idea how to do it.  I'm sorry that the partitioning tool doesn't ask "you are about to format your entire disk, allow or deny.
If I remember correctly though,you did say you got in a hurry, & that is what bit you.
I'd use the search or trying google for recovery methods or software. I realize it not much help but it is the best I can offer.
Not stupid just hasty!

---

### Post by kongle on 2007-10-22
Thank you for your help. I will check.

Or, if someone knows about the possibility of data recovery:

1. Is it possible?
2. If yes, how can it be done, and what would be the best way, taken that I now seem to have a hard drive with only a defect Ubuntu installation? Should I install Windows or try to install Ubuntu again? Is there any software for either operating system that can recover data that was erased in the way the Ubuntu installer did?

I am VERY grateful for any help.

---

### Post by rsambuca on 2007-10-22
As long as you haven't done a low level format (which you haven't), then you may be able to recover most of the data.  There are many file recovery options, but I can't remember the best ones off hand.  If you google for 'file recovery software', you will get a bunch.  I will also try and hunt down the one I had used for a friend and let you know.

---

### Post by jaybombalous on 2007-10-22
U have to understand one huge thing in the computer industry, things are meant as literal as possible.


"use all the disk" means just that, period!!!!

---

### Post by kongle on 2007-10-22
Thank you!

I am very tired and now that I've had good news I should be able to go to sleep, so I will leave the job of recovering data tomorrow. I just read in the Wikipedia article on data recovery that Knoppix contained some tools for recovering data. If these tools are sufficient, it would be ideal as I should be able to fix everything from a live CD. Does anyone know if this would be possible?

Thank you and good night.

---

### Post by kongle on 2007-10-22
> **jaybombalous said:**
> U have to understand one huge thing in the computer industry, things are meant as literal as possible.


"use all the disk" means just that, period!!!!

I know very well now, thank you.

---

### Post by kostkon on 2007-10-22
Please, next time *make a backup of your data* before trying to install a new OS *on the hard disk that they exist*.

During such *serious system altering actions* (i.e. installing an OS), *a simple mistake can have serious consequences*, like the ones you experienced yourself.

---

### Post by keforex on 2007-10-22
See, I am a n00b with Linux and Ubuntu also, and when I did get to that screen "use all the disk" thing I stopped because I didn't undestand.

What I did was phisically disconnect the power and data cables inside my machine from the HD that has my Windows Ultimate x64.

When I started the Ubuntu install again, it recognized the one and only HD that was connected, exactly the one I wanted to use. The other one was safely protected by un-connected cables.

As a n00b, the tricky part IMHO was that partitioning menu that says "use all the disk" etc... because it did show (recognized) all HDs on the machine. Since that screen did not have any warnings about what OS could be already installed in what HD, I coudn't "assume" it wouldn't wipe out all the disks found.

A suggestion I have for the developers is to put some more messages on the scrreen like "The disk you selected already has another Operational System installed, are you sure you want to wipe it out?" or something like that.

If Linux is to take over Windows, it has to be "operator-proof" becuase the vast majority of computer users are just that, users.

---

### Post by dagrump on 2007-10-22
Microsoft has no such safeguard, it will automatically wipe your drive and take it all. It is not going to see another operating system & allow you to boot to it.
The installation of most FOSS OS's see windows & allow you to resize & use your free space for their install. Well linspire try to take it all, but they did start out calling themselves lindows, go figure.
Use entire disk most of the time means exactly that, use the entire disk. The OP did say he got in a hurry & just plunged ahead. This is a case of didn't back up info that should not be exposed to corruption or loss, & admitted hast to install (before Mom or Dad or Sis caught them).
I have thrashed systems right & left, it happens, that why backing up your data to external sources is just S.O.P.

---

### Post by az on 2007-10-23
> **dagrump said:**
> I could be wrong, but if you selected "use entire disk" , yes , YOU wiped the drive. This is not an issue with the operating system, this is operator error. Now some one might be able to help you recover your data, but I wouldn't bet on it.
Please from here on read & understand the directions, if you don't understand ASK some one.
Oh, your sister is going rip your ears off!

That's somewhat rude and mostly wrong.

Whatever data was not overwritten is recoverable.  Formatting (even a "low-level" format) does not erase data.

The Ubuntu base install is just under 1.5 gigs.  Depending on how big and how full your drive was, Kongle, you should be able to salvage those files. 

See [http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

There is a data recovery forum there.  As well as all of the data recovery software you will need.  Post a new topic ([http://ubuntu-rescue-remix.org/forum](http://ubuntu-rescue-remix.org/forum)) and get the help you need.

You will need another hard disk on which to copy (image) the disk, and then some more space to put files you will carve out of that.  If you are really short on space, you can always work on the original drive instead of imaging it.

Good luck.

---

