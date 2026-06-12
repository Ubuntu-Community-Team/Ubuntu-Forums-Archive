---
title: "Extending/Enlarging Ubuntu Partition With GParted"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jeremyj on 2009-07-07
I'm hoping to add 10 gigs to my existing Ubuntu partition for some free space.  I've used Vista's Disk Management tool to create the 10 gigs of unallocated space, but I'm not sure if that's necessary before opening GParted.

Does anyone have any advice on how to add these 10 gigs?  Do I need to use GParted while booted into Ubuntu, or run it from a disc?  Thanks in advance!

---

### Post by danwood76 on 2009-07-07
You will need to boot a livecd as you wont be able to modfiy a partition whilst its active.

Once in the live cd open up gparted from System->Administration and resize the partition you are after.

---

### Post by spcwingo on 2009-07-07
As above, but _don't forget to backup_.  Any altering of the partition has the potential to do some serious damage (loss of data).  Although highly unlikely, it can still happen.

---

### Post by jeremyj on 2009-07-07
I've gotten to GParted from the 9.04 Live CD.  I do need the 10 gigs of unallocated space still free, correct?

Also, the only text box I need to enter data in under the Resize/Move dialog box is New Size (MiB), right?  Since my current partition is 20 gigs, I should add the 10 gigs in megabytes to that, and the resulting number is the one that goes into New Size (MiB)?  In other words, the number would go from 20473 to 30720?  The window also says Maximum Size:  20473, would that keep me from adding space?

I've included a screenshot of what I'm seeing, just in case.  I appreciate the help.

---

### Post by jeremyj on 2009-07-07
Don't know if this is discouraged here, but *bump* off 4th page.  It's not an emergency, but I didn't want to get buried under other threads.

---

### Post by akakingess on 2009-07-07
Possibly you need to format the "unallocated" 10 Gigs to ext3 first?  I am no expert, but you said it was an emergency, so just throwing some ideas around, I will try to dig up some more info on the correct process.

Sorry, I thought you said it "was" an emergency, my miscommunication.

---

### Post by michaelzap on 2009-07-07
I don't think that you can extend your Ubuntu partition to include the 10GB of free space with gparted because of their relative positions. There may be another way to do this, but it might require you to move your Ubuntu partition. I'm interested to see if anyone else has a suggestion, since I'm probably going to delete the Vista rescue partition on my Lenovo laptop and I'll end up with a very similar situation (except that I'll probably have to move my Vista partition as well).

---

### Post by jeremyj on 2009-07-07
> **akakingess said:**
> Possibly you need to format the "unallocated" 10 Gigs to ext3 first?  I am no expert, but you said it was an emergency, so just throwing some ideas around, I will try to dig up some more info on the correct process.

Sorry, I thought you said it "was" an emergency, my miscommunication.

No problem.  I appreciate any help.

---

### Post by akakingess on 2009-07-07
Obviously, the best way to do all of this would be back up everything, install Ubuntu and partition everything from the ground up and then also reinstall Windows, but if that isn't an option, let's see what we can work with.

---

### Post by michaelzap on 2009-07-07
You could of course just make that 10GB your home partition (or simply a separate storage volume).

---

### Post by jeremyj on 2009-07-07
> **michaelzap said:**
> I don't think that you can extend your Ubuntu partition to include the 10GB of free space with gparted because of their relative positions. There may be another way to do this, but it might require you to move your Ubuntu partition. I'm interested to see if anyone else has a suggestion, since I'm probably going to delete the Vista rescue partition on my Lenovo laptop and I'll end up with a very similar situation (except that I'll probably have to move my Vista partition as well).

This thought occurred to me as well, seeing as my SWAP partition is in between the Ubuntu and Vista partitions.  If moving is the solution, I may just delete Ubuntu and my SWAP, start over with a bigger partition, and restore my files.

---

### Post by raymondh on 2009-07-07
> **jeremyj said:**
> This thought occurred to me as well, seeing as my SWAP partition is in between the Ubuntu and Vista partitions.  If moving is the solution, I may just delete Ubuntu and my SWAP, start over with a bigger partition, and restore my files.

+1 ... if you do start over, consider separating your /home from root (/).

You can only add from the end of the partition and not the beginning.

---

### Post by jeremyj on 2009-07-08
> **raymondhenson said:**
> +1 ... if you do start over, consider separating your /home from root (/).

You can only add from the end of the partition and not the beginning.


So create two Extended partitions, one SWAP, and one ext3 for Ubuntu?



Also, for everyone/anyone else, is the only solution to adding extra room to Ubuntu, deleting my partitions and reinstalling with more gigs?

EDIT:  I missed raymondhenson's sentence about not being able to add from the beginning of a partition, so it looks like I'll just delete and reinstall.

---

### Post by akakingess on 2009-07-08
I believe what they mean, is create 1 NTFS for Windows, 3 ext3 partitions, (1) for Ubuntu boot, (1) for Swap, and (1) for your /home partition/directory.

---

### Post by Shazaam on 2009-07-08
No need to start over.
1. Defrag Windows twice.
2. Use Vista's partitioner to shrink sda3 (Windows) any size you want.
3. Reboot with the Ubuntu livecd; open gparted (Partition Manager).
Do the rest one at a time (slower but safer)...
4. Move the left side of sda4 (extended partition) to butt up against Windows.
5. Move sda5 (swap) left; 1gig or smaller is fine for swap.
6. Move the left side of sda6 (Ubuntu) to fill up the space.
When done boot into Windows first. It will problably want to do a chkdsk- let it run. Then reboot into Ubuntu.

---

### Post by jeremyj on 2009-07-08
> **Shazaam said:**
> No need to start over.
1. Defrag Windows twice.
2. Use Vista's partitioner to shrink sda3 (Windows) any size you want.
3. Reboot with the Ubuntu livecd; open gparted (Partition Manager).
Do the rest one at a time (slower but safer)...
4. Move the left side of sda4 (extended partition) to butt up against Windows.
5. Move sda5 (swap) left; 1gig or smaller is fine for swap.
6. Move the left side of sda6 (Ubuntu) to fill up the space.
When done boot into Windows first. It will problably want to do a chkdsk- let it run. Then reboot into Ubuntu.

Too late for that now.  :(

> **akakingess said:**
> I believe what they mean, is create 1 NTFS for Windows, 3 ext3 partitions, (1) for Ubuntu boot, (1) for Swap, and (1) for your /home partition/directory.

I have Windows, Recovery, and a Dell partition already set to go.  I just deleted my Ubuntu and SWAP partitions, so now I have 50.50 gigs of free, unallocated space.

I'm in the Live CD, and I keep running into a problem where I create a 48 gig Primary partition for Ubuntu, but there's 1.34 mb unallocated space before that partition between it and Windows, and 2.50 gb unallocated space after it.

I then go to add the SWAP partition, but I get an error dialog that says, "It is not possible to create more than 4 primary partitions.  If you want to create more partitions you should first create an extended partition.  Such a partition can contain other partitions.  Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

I can't do that last sentence without messing up my Windows, Recovery, and Dell partitions.  Should I just leave the SWAP and Ubuntu in the same extended partition?  How do I create a partition for /home by itself?

---

### Post by danwood76 on 2009-07-08
Yes you can simply create all your ubuntu partitions within an extended partition. I currently have 20 extended partitions on my main drive which has various versions of distros etc.

To create a /home you just create a seperate partition and set it to mount to /home in the installer.

---

### Post by raymondh on 2009-07-08
Hello JeremyJ,

This guide is to create the partitions using gparted from the liveCD and then using Manual during the installation.

Remember to review before applying.  Back up your files, there are no guarantees.

Creating the partitions:

1.  click on the unallocated/free space to highlight it.
2.  Go to PARTITION and select NEW and make EXTENDED using all free space.  Click OK to apply
3.  Click inside the newly created extended partition.  Goal is to make 3 LOGICAL  partitions

-   Make a swap partition, about 1.5GB (1500mb) and format LINUX SWAP FILE SYSTEM
-   Make a 15GB partition, format EXT3 (or EXT4).  This will be where root (/) will reside
-   The remaining space, format EXT3 (or EXT4).  This will be where /home will reside

4. Click OK, review and apply.  Once partitions are done, quit and close gparted.

Installation part: 

In the partitioning stage/step, select MANUAL

1.  Select the swap partition and click EDIT (button below).  Set 'USE' and file type 'SWAP'
2.  Select the 15GB and EDIT.  Set 'USE',  format 'EXTwhatever you chose'  and file type '/'
3.  Same for the last partition except file type is /home

Proceed with the installation.

Good luck.

---

### Post by jeremyj on 2009-07-08
Thanks, all.  I actually wound up going with my previous setup, but I added 20 gigs to Ubuntu and created my Swap at the end.  (See the Windows Disk Manager screenshot below.)  My Swap is 518 megs (did the wrong math :lolflag: ) because I don't put my computer to sleep.  This was something I found out in an older thread.

The biggest thing that confused me when I did this was the roughly 2 megs between Vista and Ubuntu when I was looking at it in GParted (no screenshot of that).  Since I was trying to bump Vista and Ubuntu side by side, it baffled me.  Doesn't look like it exists now.  I didn't create a /home partition though, because I didn't figure that out until I was letting Gparted run the tasks I'd set.  No big deal I guess since I just use one distribution of Ubuntu at a time.  It would probably make upgrading/reinstalling later on easier, but it's alright.

Anyhow, mission accomplished.  Ubuntu has a bigger partition, and it's side by side with Vista now.  Thanks for the help!

---

### Post by danwood76 on 2009-07-09
> **jeremyj said:**
> The biggest thing that confused me when I did this was the roughly 2 megs between Vista and Ubuntu when I was looking at it in GParted (no screenshot of that).  Since I was trying to bump Vista and Ubuntu side by side, it baffled me.

This will still be there, I have noticed this before and it happens when the windows partitioner (terrible piece of software) creates a partition but doesnt round up to the nearest cylinder which (g)parted does.
Its not a huge issue, the way to solve it is to do all the partitioning on your system with one piece of software and not multiple softwares.
But there is no need to worry about 1MB of space :)

---

