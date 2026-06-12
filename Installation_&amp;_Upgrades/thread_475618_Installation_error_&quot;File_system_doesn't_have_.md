---
title: "Installation error: &quot;File system doesn't have expected sizes...&quot;"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by thatcrazycommie on 2007-06-16
I've finally got my partitions set up the way I want them: 30 GB for Windows, 9.5 GB for Feisty, and 400 MB swap space. However, when I try to continue, I get the following error message:

[img]http://img.photobucket.com/albums/v330/thatcrazycommie/Screenshot-1.png[/img]

What does this mean? Should I just press "ignore"? (Also, if anyone has any idea how I can figure out what the heck that 40 MB partition on the top is for, or where it came from, that would also be helpful.)

Thanks!

---

### Post by trak87 on 2007-06-16
I'm not sure what it means, but wouldn't it be better to use fat32 instead of fat16? That fat16 partition... did you create it or is it the aftereffect of installing Windows? I see that you are wondering where it came from as well and it seems others post something similar as a consequence of installing Windows. What version of Windows are u using? Also, the swap partition should be twice the size of your installed RAM. You've specified a 400 mb swap partition. Does this mean you only have 200 meg RAM? If you have 512 meg of ram, specify a 1 gig swap drive. This rule is generally true until you get up to very large amounts of installed RAM, like 4 or 8 gig of RAM.

---

### Post by thatcrazycommie on 2007-06-16
Yeah, like I said, I actually have no idea where that fat16 partition came from. It's the three below it that I plan on using (the ntfs for Windows, the swap for swap space, and the ext3 for Ubuntu.) I'm slightly hesitant to delete the fat16, though, because I don't know what the 33 MB of data inside it is, and I don't know how to access it to see.

Edit: Oh, I didn't know that rule about the swap space being twice the size of your RAM. I'll change that and see if it helps anything.
Edit again: No, I have increased the size of my swap space to 1000 MB, twice the size of my RAM, and I'm getting the same message.

---

### Post by trak87 on 2007-06-16
I don't have an answer for you about the fat16, but increasing the swap file size is still a good thing.

Was Windows pre-installed on your system? Perhaps that 41mb fat16 partition is part of a control mechanism for the vendor's install of Windows? Like information in case you need to do a re-installation or something like that. Just a guess.

---

### Post by thatcrazycommie on 2007-06-16
Yes, Windows was pre-installed, so you could be right -- Dell (the manufacturer) likely has something to do with that fat16 drive. Thus far, I can't find any way to explore or access it, though, so who knows. I am considering reinstalling Windows/reformatting my hard drive, but that's a considerable venture.

(Of course, I'm assuming that that "Warning" message I'm getting upon installation is referring exclusively to the fat16 drive, which may not even be the case. I wish I knew what the hell it was talking about.)

---

### Post by trak87 on 2007-06-16
There are nutty schemes with MS windows. People in the neighborhood ask me to fix their machines and I ask them if they have a Windows disk or a vendor reinstallation. To make a long story short, when it comes to pre-installed systems, they pay for Windows once when it was pre-installed and then they pay a second time when they realize they need the physical disk to reinstall.

Maybe there's a simple solution to this, but this is what I'm thinking: use a real Windows install disk and install that in the first partition. Then proceed to the Ubuntu installation and everything should be fine. My solution may be draconian though. Let's see what others have to say.

---

### Post by merlinus on 2007-06-16
I am with trak87.  Better to cut your losses now, than deal with massive agita in the future.

Beg, borrow or steal a Win2000 installation disk, and let it use your entire disk.  No activation crapola with this version, and I still think it's the best m$ ever made.

Then, if needed, download SP4 and the roll-up from microsoft.com.

Get rid of any temp files, and defrag several times.

Then partition and install ubuntu.

Of course, back up your data before doing anything!

Good luck....

-merlin

---

### Post by Pumalite on 2007-06-16
> **merlinus said:**
> I am with trak87.  Better to cut your losses now, than deal with massive agita in the future.

Beg, borrow or steal a Win2000 installation disk, and let it use your entire disk.  No activation crapola with this version, and I still think it's the best m$ ever made.

Then, if needed, download SP4 and the roll-up from microsoft.com.

Get rid of any temp files, and defrag several times.

Then partition and install ubuntu.

Of course, back up your data before doing anything!

Good luck....

-merlin

Use Gparted to prepare the disk and then, proceed.

---

### Post by merlinus on 2007-06-16
> 
Use Gparted to prepare the disk and then, proceed.


Definitely the best idea for partitioning before installing ubuntu!

Download the gparted live cd from:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Also, I would give 15G to windows and make an ext3 /home partition of 15G in addition to / and /swap.  You can use it for data and sharing between windows and ubuntu with the appropriate drivers.

-merlin

---

### Post by thatcrazycommie on 2007-06-16
I decided to bite the bullet and press "Ignore," and it installed fine. Also, it turned out that the fat16 partition was "Dell Utilities." It shows up on the Ubuntu desktop as a now-accessible drive. I'm still figuring some basic stuff out - this is my first time using any kind of Linux - but I'm up and running. Thanks for your help, guys.

---

### Post by boyofford on 2008-01-05
I had the same error come up on my dell while trying to install dual boot with pre-installed dell inspiron 530s
searched around a bit (for 2 hours) for solution/info,
in the end got impatient and chose ignore, no problems! 
don't really understand the error, but so far all good so just thought i'd post in case anyone else got stuck on this.
:popcorn:

---

### Post by Kiri on 2008-03-05
That fat16 partition is dell's 'recovery partition' that they use instead of including recovery cds. It's quite annoying, since it seems to confuse a lot of installers / partitioners.

---

