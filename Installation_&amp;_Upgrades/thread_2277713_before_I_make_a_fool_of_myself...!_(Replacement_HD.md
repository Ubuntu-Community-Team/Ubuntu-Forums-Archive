---
title: "before I make a fool of myself...! (Replacement HDD &amp; install 14.04 LTS?)"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by RogerStenning on 2015-05-11
Hi,

First post, and liable to be a doozy.

I've searched, but not found anything that I could see that specifically related to this, so here goes...

I have a Toshiba Satellite C855-29M notebook. Originally installed with Win8, I replaced the OS with Ubuntu 14.04 a couple of months ago after Windows kept falling over (got tired of recovering it all the time, hacked off with WinDoze, so decided to take the leap to the Penguin. I did the change with a Live USB thumb drive carrying Ubuntu 14.04 LTS. It was ridiculously easy, wish I'd done it ages ago, but that's hindsight for you).

However, the (SEVERAL expletives deleted) PC has continued to fail twice more since then, requiring reformatting and repeated re-installation of 14.04 LTS using the afore-mentioned live thumb drive, and with the last reinitialisation, I reformatted the drive to EXT3 standard. Then, I had the stereotypical 2-watt bulb go on above my head, and ran *Disks* on the thing. Lo and behold, 1142 bad sectors, and yep, not surprisingly it failed the *SMART* test.

So, I bit the bullet, and ordered a replacement drive of the same type - a Toshiba MQ01ABD100, which is a 1Tb SATA-compatible HDD (43 quid off Amazon.co.uk; cheaper than I was expecting, which was nice). And this is where I'm at, right now; the replacement drive is due for delivery sometime today, and doing last minute homework on formatting it and performing a fresh installation of 14.04 LTS has left me somewhat dazed and confused, as I've previously formatted the existing drive which already had either FAT32 or EXT3 on it. Formatting a fresh HDD right out of it's static-resistant bag is a bit of a new thing for me, as a result.

Here come the questions as they occurred...


[LIST=1]
[*]Once I've swapped out the old drive for the new one, will the 14.04 LTS on the live USB thumb drive let me format the brand new drive? 
[*]Of not, is there any special software, application, or package that I need to add to the live USB thumb drive installation of 14.04 LTS, (such as, for wild example, gparted?)? 
[*]If I need to specify partition size, how many, and what size, should I create? 
[*]Are there any pitfalls awaiting me that you can warn me about before I fall headlong over them? 
[/LIST]

In case it helps with the advice you give, I should mention, fwiw, that I know my way around a screwdriver & soldering iron (and, when needed, a bleepingly big mallet), I'm a Licenced Radio ham (G1LIW), and spend a few years in 1st line IT support about two and a bit decades or so back (this latter point probably as much use as a chocolate fire grating, of course!)...

Many thanks for any advice you can give :)

Cheers,

Roger

---

### Post by Elfy on 2015-05-11
Swap the drive.

Boot with the USB.

Tell it to use the whole drive - while that's doing that wander off and beat the chocolate fire grate into submission with the mallet. 

That will give you a swap partition and a massive / drive.

You *might* want to look into partition schemes - this early in the game you can do more or less whatever you like. 

Depends how you use the machine.

Personally I'd create 
1 extended partition
swap partition = to RAM (logical)
ext4 partition = to 20GB (logical)
then remainder as ext4 (logical)

Gparted is on the live session - use that.

Then install using Something Else.

Set the 20Gb partition to be /
Set the big partition to be /home

---

### Post by Bucky Ball on 2015-05-11
1. Yes. Boot the drive, Try Ubuntu, launch Gparted, add partitions (although there is no need to do this as you can choose 'Something Else' during install and create the partitions there ... either way, use EXT4, not 3);
2. No;
3. Basic set-up:

/ = root, where your OS will go, 20Gb is plenty;
/home = where your personal data and settings will go, as large as you like;
/swap = 2Gb unless you hibernate with lots of apps open, then safest to make it as large as your installed RAM. 

4. None that I can think of and hopefully you won't find too many when you get there ... if you do, just give a yell.

There are a lot of sites that guide you through a fresh install. [This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") site will give you some clues on using 'Something Else' during the install.

* Ninja-ed by Elfy. There's more than one way to skin a cat. ;)

I generally make a solid plan of what I want the drive to look like prior to switching the machine on so when I get there I have a clear idea and clear goal. Go for a plan that suits your purposes and run it by us if you want confirmation it is going to work. Good luck.

PS: Some people (me included) use symlinks in /home to link to data in already existing partitions. That is another alternative if you have data already existing on other drives. It has its advantages.

---

### Post by dino99 on 2015-05-11
> Here come the questions as they occurred...

Once I've swapped out the old drive for the new one, will the 14.04 LTS on the live USB thumb drive let me format the brand new drive?
Of not, is there any special software, application, or package that I need to add to the live USB thumb drive installation of 14.04 LTS, (such as, for wild example, gparted?)?
If I need to specify partition size, how many, and what size, should I create?
Are there any pitfalls awaiting me that you can warn me about before I fall headlong over them?
1) should work without surprise
2) Gparted Live is my fav app as i does not like the all-in-one magic script that should blindly works but fails too often (well, that was my horribly experience long ago).
3) So i now use gparted to format the device first, with the required partitions (for a home user):
     - / (root) ext4 format, boot flag set, about 12/15 gb
     - swap, about 4 gb (rarely used if ram =>4 gb, except if using heavy apps)
     - /home, ext4, as large as you want to store your data & settings
    Indeed you can set more partition(s), for a backup for example, but an external device is more appropriate. And remember that setting an extended partition, where you can set multiple partitions inside, let you change later the number of partitions you will need/want (we cant have more than 4 primary partitions by design). For example that new device can be formated with one primary partition for /, then an extended one where you set swap & /home.
4) when the partitions are set, from above, then start the ubuntu installation, and when the installer will ask you where to install it, select 'something else' option to choose the previous partitions made. Then you will be asked where to set grub bootloader, choose /dev/sda

That it you might be ready to play :p

---

### Post by RogerStenning on 2015-05-11
Wow. Can't fault the speed of replies, folks - thanks :D

> **Elfy said:**
> Swap the drive.

Boot with the USB.

Tell it to use the whole drive - while that's doing that wander off and beat the chocolate fire grate into submission with the mallet.

"Beat the chocolate fire grate into submission with the mallet" [IMG]http://www.coldwarprovost.org.uk/forums/rofl.gif[/IMG]

> **Elfy said:**
> That will give you a swap partition and a massive / drive.

You *might* want to look into partition schemes - this early in the game you can do more or less whatever you like. 

Depends how you use the machine.

Personally I'd create 
1 extended partition
swap partition = to RAM (logical)
ext4 partition = to 20GB (logical)
then remainder as ext4 (logical)

Gparted is on the live session - use that.

Then install using Something Else.

Set the 20Gb partition to be /
Set the big partition to be /home

OK, thanks :) Count one in favour of gparted; also interesting on the two major partitions - unless I missed something, would that be:
20gb /root
8gb /swap
xx gb /home
and
xx gb /somethingelse?

where xx is unknown (and I'd appreciate suggestions on sizing there?)

If so, what was the something else (colour me a bit confused!)?

> **Bucky Ball said:**
> 1. Yes. Boot the drive, Try Ubuntu, launch  Gparted, add partitions (although there is no need to do this as you can  choose 'Something Else' during install and create the partitions there  ... either way, use EXT4, not 3);
2. No;
3. Basic set-up:

/ = root, where your OS will go, 20Gb is plenty;
/home = where your personal data and settings will go, as large as you like;
/swap = 2Gb unless you hibernate with lots of apps open, then safest to make it as large as your installed RAM. 

4. None that I can think of and hopefully you won't find too many when you get there ... if you do, just give a yell.

There are a lot of sites that guide you through a fresh install. [This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") site will give you some clues on using 'Something Else' during the install.

* Ninja-ed by Elfy. There's more than one way to skin a cat. :wink:

I generally make a solid plan of what I want the drive to look like  prior to switching the machine on so when I get there I have a clear  idea and clear goal. Go for a plan that suits your purposes and run it  by us if you want confirmation it is going to work. Good luck.

PS: Some people (me included) use symlinks in /home to link to data in  already existing partitions. That is another alternative if you have  data already existing on other drives. It has its advantages.

OK, thanks; I don't know symlinks, and of the two drives attached via USB, one is the data backup drive (thanks the stars only a week out of date!), and the other is the media store (music, etc). Been struck by failing drives before on windoze, so made a habit of keeping my machines as backed up as reasonably possible since then, so while I'll look into it, if it's what I think it may be (a global system redirect for Home files), I'll probably give it a miss as being a little bit redundant - we'll see, anyhow :)

OK on the formatting; I'm leaning towards keeping it simple, and using the installer to create the EXT4 partitions - why invite confusion? This said, there are now two recommendations for gparted. Need to think that over.

LOL on being "Ninja-ed" Love the phrase :)

Not with standing any further comments from Elfy on partitions and sizing, I currently think that three partitions as described (20gb /root, 8gb /swap, and the rest as /home) is a plan should suffice for the time being; using EXT4 means that I can always repartition or add partitions later, without consequential loss of data, right?

> **dino99 said:**
> 1) should work without surprise
2) Gparted Live is my fav app as i does not like the all-in-one magic  script that should blindly works but fails too often (well, that was my  horribly experience long ago).
3) So i now use gparted to format the device first, with the required partitions (for a home user):
     - / (root) ext4 format, boot flag set, about 12/15 gb
     - swap, about 4 gb (rarely used if ram =>4 gb, except if using heavy apps)
     - /home, ext4, as large as you want to store your data & settings
    Indeed you can set more partition(s), for a backup for example, but  an external device is more appropriate. And remember that setting an  extended partition, where you can set multiple partitions inside, let  you change later the number of partitions you will need/want. For  example that new device can be formated with one primary partition for  /, then an extended one where you set swap & /home.
4) when the partitions are set, from above, then start the ubuntu  installation, and when the installer will ask you where to install it,  select 'something else' option to choose the previous partitions made.  Then you will be asked where to set grub bootloader, choose /dev/sda

That it you might be ready to play :razz:

Thanks :) I've used the live USB thumb drive three times to format and install 14.04 on the existing drive, where there was already an existing FS to look at (and overwrite); in those cases the installer worked fine; my concern was for its use on a drive that would be completely blank and fresh out of the wrapping. Thus far, I've not really seen any concrete advice *not* to use the installer; this said, there are two recommendations (including yours) to use gparted before letting the installer loose. Hmm.

Boot flag? I've obviously missed something along the way. Come again?

Thanks,

Roger

---

### Post by Elfy on 2015-05-11
>  Boot flag? I've obviously missed something along the way. Come again?Never done it. Never needed it.

---

### Post by RogerStenning on 2015-05-11
Fair enough; I would have thought the installer took care of that when formatting the drive, hence the confusion :)

Thanks again for the swift and very constructive replies :)

Makes a pleasant change from some of the places I've visited on other topics over the years :)

Cheers,

Roger

---

### Post by Elfy on 2015-05-11
As far as extra partitions go - if you've got an extended partition - you can create as many as you want within reason.

the OTHER option is to 

/
swap
/home

but not use all the drive - then you can come back tomorrow, next week/month/year and have space still on the drive. 

That *really* is up to you.

---

### Post by Bucky Ball on 2015-05-11
Unless you're going to hibernate, as mentioned, you don't need a /swap anywhere near 8Gb. 2Gb is fine. I always put it at the end.

Just to throw something else in here, /, /home and /swap are one option, and a good one, as your personal data is separated from your OS (meaning easier backups and if you need to reinstall the OS your data remains on the /home partition). But there is more basic. You can create just:

/ = large as you like, your OS goes here and your personal data and settings go in a /home DIRECTORY, not partition, inside /;
/swap = 2Gb.

The basic-est. ;)

As mentioned, up to you where you want to go with this at this stage. Grab your favourite beverage, a piece of paper and writing implement and have a think about what might suit you best.

PS: the mount points /, /home and /swap are selectable defaults in 'Something Else', along with a few others, so it is reasonably 'follow your nose' if you spend some time acquainting yourself with what is coming up before you dive in.

---

### Post by mattharris4 on 2015-05-11
I did a search on your computer model and it isn't that old (it came with Win8 from the factory which makes it less than three years old).  Your hard drive should not have failed that soon (I type this on an HP with an eight year old HD, we have two computers with HDs that are four years old and I haven't had to replace any of them -- I even have an 18 year old Toshiba Tecra which is no good for modern use but still fires up and runs fine, I load up Microsoft Works on it and let little kids type their fingers off with it, as far as I know it has the original battery and HD on it).  Since you can put any HD that is 2.5" (or an SSD that is between 7mm to 9mm thick) 2TB or less and SATA compatible in your computer if you have another failure within 2-3 years I would recommend trying a different brand of HDD.  It doesn't even have to be 1TB in capacity; a 250GB, 320GB, 500GB, 640GB, 750GB, 1.5TB or 2TB drive (or any other with SATA compatibility smaller than 2TB) will work just fine.  Of course a SSD would work as well, boot up much faster and any capacity would work although I would recommend at least 240GB capacity for you, those cost about $100 US and are sold on Amazon as well as probably a billion other computer hardware retailers both online and brick and mortar.  I have read about several other Toshiba computers from this era that had early HDD failures, I think they had a year where their HDD quality took a dive (I hope it improved by 2014, I have a year-old Toshiba laptop myself), if you ended up purchasing a Toshiba drive from that era still "new in the box" it may fail early as well and this information might help you in the future.

---

### Post by RogerStenning on 2015-05-11
Hmm.

Elfy & Bucky -

OK, time to grab brain juice (Coffee), and thunk hard...

I  like the idea of keeping the OS separate from the data; makes recovery  efforts easier (and definitely less fraught) in the long run. It also  makes creating a recovery image of the OS smaller, without user data to  get in the way (which is backed up on a weekly basis anyhow).

I think, on balance, that simplicity is the key here, at least to start with; three partitions, as follows;
20gb /home
4 gb /swap (split the diff, I do use graphics packages from time to time)
and the rest, /home (which can always be further split later on as requirements might change).

Thoughts?

Matt -

Yeah, it surprised the hell out of me too. It's the fastest I've *EVER* had a hard drive begin to go to pieces on me, and I used to shout rather rudely at WD units back in the day if they failed in under four years! The replacement HDD is an interim measure anyhow; I actually looked at SSDs, but they're still a bit expensive; maybe in a year (when capacity has gone up, and price come down) I'll think about getting one, but not just now. Thanks for the comment, though; confirmed something I was wondering about.

Cheers,

Roger

---

### Post by Bucky Ball on 2015-05-11
> **RogerStenning said:**
> I  like the idea of keeping the OS separate from the data; makes recovery  efforts easier (and definitely less fraught) in the long run. It also  makes creating a recovery image of the OS smaller, without user data to  get in the way (which is backed up on a weekly basis anyhow).

Agreed. ;)

> **RogerStenning said:**
> I think, on balance, that simplicity is the key here, at least to start with; three partitions, as follows;
20gb /home
4 gb /swap (split the diff, I do use graphics packages from time to time)
and the rest, /home (which can always be further split later on as requirements might change).

Looks good to me (although I always put the /swap at the end of the drive, old school rule of thumb not really needed now, and old habits die hard!). I'd say you're ready, you've aimed, now all that's left is to fire!

* But just one thing ... remember, UEFI is fine with more than four partitions, but if you install in legacy, you are limited to four partitions per drive. This could be a problem if you need to add more partitions. To overcome that, if you come to it, shrink the /home partition and leave free space and create the fourth partition as an extended partition. This acts as a 'container' for virtual partitions. You can put as many of those (theoretically) as you like inside an extended partition and the system sees it as one partition, the extended container partition. Cool. The logical partitions inside it behave, for all intents and purposes, as any regular partition.

---

### Post by RogerStenning on 2015-05-11
Hmm. Actually makes sense as well, now I've got some of the java down me neck, to put the swap file at the end, rather than in the middle. There's No School like Old School, after all ;)

Cheers,

Roger

*edit*

intersting point re legacy; hadn't thought of that. Hmm.

OK,
/root = 20 gb
/home = 400 gb (should be more than enough, can be resized smaller later if necessary)
/media = balance of the gb (had to call it something, so 'media' it is! Again, more than enough, can be resized bigger or smaller, or even subdivided later with nested partitions, as required)
/swap = 8gb

Sound like a plan?

---

### Post by RogerStenning on 2015-05-11
Marked as 'solved', all that's needed now is for the Amazon delivery person to hand me the replacement drive at some point today, and the rest will be down to me, a grounding wrist strap (always good practice in the workshop when dealing with electronic bits), a decent crosshead screwdriver, and the 14.04 installer :)

---

### Post by Bucky Ball on 2015-05-11
Sounds like a plan. ;)

With your four partition set up in your last post, though, you would need to delete one of them to add the extended partition if you're installing in Legacy. I'd be tempted to make 'media' an extended partition to start with then create logical partitions inside that as required, but again, up to you and what you think will work best. Good luck.

PS: From memory this relates to Elfy's suggestions previously: You could create / on a primary partition then create an extended partition using the rest of the disk and put /home and /swap inside that. No partition limit then. You can add whatever logical partitions inside the extended without issue (within the hardware capabilities of your machine, that is!). Save you diddling around later if the need arises. So:

/ = primary partition;
Rest of drive = extended partition with /home and /swap inside that as logical partitions.

The system will see this as two partitions.

---

### Post by RogerStenning on 2015-05-11
OK, now I'm a tad confuzzed; an 'extended' partition? How does that differ from a normal partition? I thought partitions had to be of a fixed size, is an extended one a dynamically variable size?

[I]edit
[/I]
Cancel the above, found out what it is. OK, if I make the main partition an extended partition (is that even possible?), can I stick /home in there as a nested partition?

i.e.

/ root
/ extended partition
  |- / home
/ swap

Does that work?

---

### Post by Bucky Ball on 2015-05-11
No, not dynamic. An extended partition is like a container for other partitions. It is not a regular partition and you can't store data 'on' the partition, but you can store data on the logical partitions 'inside' the extended partition 'container'. 

Say if I have 200Gb free space. I right click in Gparted and 'New'. Select 'extended partition' and use the whole 200Gb. That's it. Now, right click the extended partition. You'll notice that you can click 'new' and create a logical partition INSIDE the extended partition. I'll make that a 50Gb logical partition. Now I have 150Gb free space inside the extended partition and a 50Gb logical partition. 

Hope that makes a little more sense. [This]("https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition") might make more sense.

---

### Post by Bucky Ball on 2015-05-11
That link I posted has an example of an extended partition with logical partitions inside it. Here is a real-life example from my own machine. Look closely at the extended partition and how many logicals I have in there. This is a legacy install with the four partition limit (extended is seen as one partition regardless of how many logical partitions are inside it). As far as the system is concerned I have sda1 through sda4 so all is good as far as the four partition limit goes. Logical partitions inside the extended don't count.

---

### Post by RogerStenning on 2015-05-11
ok, now my head is hurting ](*,)

Days off are supposed to be spent relaxing, not learning new concepts in cross-eyed confusion!

right... deep breath...

My understanding thus far, and please correct me if I'm wrong...

The hard drive comprises:
A boot sector, from which the PC gains all the instructions needed to run up the system in preparation for reading the full operating instructions contained in the primary partition, /root.

/Root is the primary partition where the OS is held, along with the software packages that one might conceivably use. In addition, the OS primes and prepared the /swap partition.
/swap is the smaller partition, used by active programs that are not currently in focus at any given time.

And now we come to the fun bit...

The extended partition will take up the rest of the disk; nested inside will be logical partitions.

And here's the question: Can /home be a logical partition, or do I have to maintain /home as an ext3 partition of fixed size, with the extended partition taking up the rest of the space, to be eventually filled with one or more logical partitions?

Sorry to sound dense, but I work permanent late turn, and this is well late for me ;)

Hold up. You "Ninja-ed" me. Gimme a mo to read your second post...

OK, think I'm getting this now, cheers for the diagram.

also, it begs another question, which I'll come to in a moment or three...

So, /home CAN be placed as a logical partition within the extended partition?

And the follow-up Q, HDDRecovery partition? an image of the OS, perhaps?

Cheers,

Roger


EDIT

hang on a mo. Your SWAP FILE is a logical partition within the extended partition?!

---

### Post by dino99 on 2015-05-11
>  Can /home be a logical partition

as explained previously, an 'extended partition' is a 'container' where some 'virtual' partitions are inserted; it is not a 'usual' partition where folders/files can be created like in a 'primary' or 'virtual' partition. That said, its a two steps partition creation: first the 'extanded' one, then creation of a 'virtual' (also named 'logical') one (like /home) inside it (and some others if you need).

note: avoid naming a partition with a reserved word: /dev/media, 'media' is already used by the system, and is a risk of confusion, so choose an other name to be safe.

---

### Post by RogerStenning on 2015-05-11
Dino -

Hindmost foremost, or something...

OK on reserved words, yeah, I'd forgotten that, thanks for the reminder :)

Right, I'm back to square one on this, as what I thought about files systems was apparently wrong. Good lord, I need an idiots guide.

Time to K.I.S.S.; original plan mk 2, I think.

/root (20gb)
/home (everything else after the swap)
/swap (4gb)

That'll do me for a year or so, until I get an SSD for this thing. It also gives me a lead-in period to learn EVERYTHING I need to know about file systems under Linux. No sense in running before I can walk, after all ;)

It really isn't playing the game, you know... I've got an analogue mind in a digital age ;)

...Especially when I'm on a low-carb diet and need a beer or ten ;) [IMG]http://www.coldwarprovost.org.uk/forums/beer.gif[/IMG]

Cheers,

Roger

---

### Post by dino99 on 2015-05-11
go for a beer, its my fav medecine too  ):P

---

### Post by RogerStenning on 2015-05-11
Gonna be a nice warm day too, perfect for a day off ;) Bugger the diet. Pale Ale it is ;)

Cheers for the advice, folks, even if my brain is slow and clunky ;)

Have a good one if you can :)

---

### Post by RogerStenning on 2015-05-11
Follow-up post from earlier this morning...

> **mattharris4 said:**
> I have read about several other Toshiba computers from this era that had early HDD failures, I think they had a year where their HDD quality took a dive (I hope it improved by 2014, I have a year-old Toshiba laptop myself), if you ended up purchasing a Toshiba drive from that era still "new in the box" it may fail early as well and this information might help you in the future.

Matt -

Well, the replacement just arrived (nice and fast, that's good :)), and inside the large box was a small drive (Good God, these things have got a LOT smaller in thirty years!), sealed in a factory-issue Toshiba-stamped Anti-Static bag ;)

It's dated 10 January 2015, so hopefully it won't have any issues :) Even so, it's going to be up for replacement by SSD in a year or so, as mentioned earlier in the thread.

I'll let you all know how the swap-out, formatting, and installation goes later today. Gonna go grab a few winks before beginning this job.

---

### Post by Bucky Ball on 2015-05-11
Yes, /home can be a logical partition inside an extended partition. In fact, just to spin the head a little more, Ubuntu can be installed on a logical partition inside the extended! This is not possible with Windows. That needs a primary partition and prefers the first partition on the drive. 

Yes, the /swap can be on a logical partition within the extended. Theoretically, you could just plop one large extended partition using all the space on the drive and install Ubuntu and related partition to logical partitions inside the extended without issue. No four partition limit then as the system will see this as one large partition on the drive. 

Don't worry about the NTFS partitions in my screenshot (Win recovery, etc.). I have Win7 installed on this machine also (though it is only used once or twice a year).

And I advise you use EXT4 rather than EXT3. ;) /swap you will not need to set as anything but 'swapspace' (that is a default option that will pop up automagically when you mark the partition as /swap so nothing to worry about there).

---

### Post by RogerStenning on 2015-05-11
Bucky -

Wow, I must've been well tired (or the body clock must have been stuffed by the morning or something), but the intended hours' kip turned into three hours!

Anyhoo...

Yeah, I know windows partitions like being at the beginning. That started with Win95 - I cut my teeth on MS-Dos 5.1, Win 3.0, 3.1, and 3.11 Workgroups (back before software and even OSs were distributed on CDs! MS Office 95, for example, came on TWELVE 3.5 inch floppy disks, and took something like two hours to install!), and then promptly forgot how to keep 'em sharp after I left one of the most thankless jobs in existence!

Right; I'm about to pull the plug on the current HDD. I'll check to see if the USB drive has gparted, just in case, but I'm going to give the installer a try, at least at first. If it carks it up, there's always gparted to recover the resulting mess ;)

Beer will come later upon a successful conclusion to the proceedings.

More later :)

---

### Post by RogerStenning on 2015-05-11
Righty-ho, then... 

The new HDD was successfully fitted (it was pitifully easy, one screw, prize of a plastic panel, carefully ground against the metalwork, and swap them out. Many orders of magnitude easier than when I worked in the IT game - at least someone's learned how to make things simple!)

The old one was dated 22 Dec 2012, btw, so sounds as if it was smack-dab in the middle of the suspect QC period, so hopefully this one should be a darn sight more reliable. 

The installer, running off the LiveUSB thumb drive, did the job with no problems; the new installation then took itself off to update everything in sight to current release levels, as expected.  Interestingly, gparted was NOT apparently installed in this new installation, I just had to install it manually. Firefox has already synced successfully with the server at Mozilla, so no loss of data there, again, as expected.

The one fly in the ointment thus far is that WINE failed to install from the repository, so I'm trying that again; it's possible there was a comms failure (I use a tethered 4G connection), so no insurmountable problems thus far.

All in all, it's looking quite unremarkably easy, all things considered.  Still, plan for the worst, and everything else will be easy ;)

Many thanks for all your advice and suggestions, and I'll pop up a shot of the drive table from gparted shortly.

---

### Post by oldfred on 2015-05-11
Not to confuse things as what everyone has suggested is fine. But it assumes BIOS boot with MBR partitioning with its 4 primary partition limit and extended & logical partitions.

But Windows 8 was UEFI with gpt partitioning. And then you probably had your older install of Ubuntu on the gpt drive. And how you then booted installer either UEFI or BIOS will be how it installs. But with gpt your need either an efi partition for UEFI boot or a bios_grub partition for UEFI boot.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

I converted my BIOS only system so all new drives or totally reconfigured drives were gpt partitioned, 10.10 was my first install on a small gpt partitioned drive. So gpt works well in my opinion. And you do not have primary, extended and logical partitions, just partitions and only a soft limit (resetable) of 128 partitions.

But if ever planning Windows again, Windows only boots from gpt drives with UEFI, where Ubuntu can boot in BIOS or UEFI boot modes.

---

### Post by RogerStenning on 2015-05-11
Hi, Fred;

OK, I don't yet know enough to comment on that; all I can say is that when I first installed 14.04 LTS on the original drive, I had the installer wipe it clean and repartition it automatically prior to installation; I did the same this time round with the fresh HDD, and thus far, (very early days here) it seems to be behaving. gparted installed first time, WINE installed second try, Gimp first time, and oh yeah, here's the screen shot from gparted, taken before I installed WINE...

[ATTACH=CONFIG]261933[/ATTACH]

Looks fairly basic to my eyes, but then I'm new to Ubuntu, gparted, and current partitioning practices ;)

I'll hopefully know more when I eventually fit an SSD to this machine :)

Also - while I think about it, any recommendations on routine disk maintenance, or does the system take care of all that in the background? (Windoze you had to go in and defrag things, root out al manner of redundant rubbish, and so on!)

---

### Post by dino99 on 2015-05-11
so you have not set a separate /home partition nor an extended one (installer job i suppose; that's why i does not like it)

---

### Post by RogerStenning on 2015-05-11
Dino -

No, I figured I'd let the installer do it all automatically, and that's what it came up with. I'll stick with it for the time being, and when it comes time to swap it out for an SSD in the next year, I'll do a proper job of things, as by then, I'll have boned up on things to the point where I understand them enough to be safe playing with the digital nuts and bolts ;)

Now all I have to do is figure out how to successfully install pipelight so that I can watch Amazon instant vids ;) Got it running right before the first failure under Ubuntu, but for some reason couldn't get it to run again on the restored systems afterwards. Think it may have had something to do with the fact that WINE wasn't installed before I tried to install pipelight the last couple of times, so I've installed WINE *first* this time, and later on I'll try installing pipelight again. We'll see, anyhow, but that's a whole different topic ;)

---

### Post by Bucky Ball on 2015-05-11
No, you don't need to defrag the drive (EXT works differently to Win disk filesystems) and do 'Windows things' as such. Just make sure you keep up your updates/upgrades and all will be be well. 

You also don't need to reinstall every six months which is what I used to do with Windows as it would get so 'clagged'. If you stick with the LTS releases you'll only need to install sometime within five years of its release (five years support).

---

### Post by RogerStenning on 2015-05-11
Excellent, thanks :)

And I know about reinstallations of windoze, trust me, damn things *mutter mutter mutter* ](*,)

I've got the automatic updater running, well, automatically, and don't plan to mess with it any time soon; nice to know EXT works (presumably) better than FAT/NTFS, so all sorted there as well ;)

Again, many thanks to one and all :D

---

