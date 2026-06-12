---
title: "installing question"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by jy0933 on 2010-04-10
about my laptop
Amd turionX2 64bit

i installed win 7 32 bit and think about installing ubuntu 9.10(64 bit) on it

i left around 100G free space with out any format...and was thinking about using that 100G for ubuntu installing

the problem is when it goes to the partition step ...

only 2 choices come up   
1. erase the whole hard disk
2. manual..<<but i dont know how to do it manually




can any 1 help me with it?

4/11 9:07

>>command=C:\Windows\System32\bcdedit.exe /set {e4fc7a66-451d-11df-b2f3-96eb40802714} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.

---

### Post by Skidbladnir on 2010-04-10
There SHOULD be an option.  But, you can do it manually.
What you need to do is: Set up a Swap Partition (Filetype: swap) around 1-2GB.  Then, the rest should be an EXT4 (default) or EXT3 (a little bit more stable, but slower) filesystem that files up the rest of it.

Screen shot the menu (Prt Screen or Print Screen) and I'll tell you.  I'm a little rusty with it, so, just upload it to twitpic, flickr, or something else.

---

### Post by lisati on 2010-04-10
Moved to "installation & upgrades"

---

### Post by jy0933 on 2010-04-10
> **Skidbladnir said:**
> There SHOULD be an option.  But, you can do it manually.
What you need to do is: Set up a Swap Partition (Filetype: swap) around 1-2GB.  Then, the rest should be an EXT4 (default) or EXT3 (a little bit more stable, but slower) filesystem that files up the rest of it.

Screen shot the menu (Prt Screen or Print Screen) and I'll tell you.  I'm a little rusty with it, so, just upload it to twitpic, flickr, or something else.


is it possible to do partition under win7 ?

im still somehow confused about the step in installation(pretty much different than before)

---

### Post by Skidbladnir on 2010-04-10
Wait, so, there is not a "use free space" option when partitioning, correct?

---

### Post by 3rdalbum on 2010-04-10
"Manual" is still pretty easy, really, but you need to know a couple of Linux/Unix terms.

When you select the Manual method, you'll be given a partitioning screen. The unpartitioned space on your hard drive (the 100 gigs) will be available for you to create partitions using the Add button.

Add a partition of at least a gigabyte, and make sure it's a little more than the amount of RAM you have. So if you have 512mb of RAM, make it a gigabyte. If you have 4 gigabytes of RAM, make a 5 gigabyte partition. This is your "swap". When you're creating the partition and you can choose the filesystem, choose "Linux swap area".

Now create another partition to take up the remaining space. Set the filesystem as "Ext3 journalling filesystem". You will also need to specify a "mount point" from the popup menu; choose "/". This is where everything else to do with Ubuntu will be installed.

That's it, for a basic installation. If you wanted to you could put your user data (/home) in a different partition or a different hard disk, but for a beginner it's not really necessary.*

*Some people will say "if you put /home on a different partition, then when you next reinstall Ubuntu you'll still keep all your personal files and settings". This is true, but for the last year or so Ubuntu's installer has automatically preserved the contents of your existing /home, whether it's on a different partition or not. I have my /home on a different hard drive, not so I can preserve my /home, but to get a small speed boost.

---

### Post by 3rdalbum on 2010-04-11
> **jy0933 said:**
> is it possible to do partition under win7 ?

Maybe (depending on you having a partitioning program capable of writing Ext3 and Linux Swap partitions), but you'd still need to use the Manual Partitioning screen in the Ubuntu installer to tell Ubuntu what partition to use as the "root" (/) and what one to use as Swap. You might as well create the partitions in the Ubuntu installer as well, and they are more likely to be correct too.

---

### Post by Tman5293 on 2010-04-11
If there isn't a use free space option you must do this manually. Although I don't know why the use free space option wouldn't be there.

To do this select the manual option. This will bring you to a page with a list of partitions on you hard drive. At the bottom of the list should be a space the says "Free Space". Click this once to highlight it. At the bottom of the screen click the button that says "New Partition". This will open the window for setting up the new partition. Under "Type For The New Partition" make sure "Primary" is selected. In the "Use As" box, select Ext4. Location for the new partition should be "Beginning". Since you have 100GB available you should make this partition 95GB so you have the other 5GB to use as swap space. Since the size is measured in MB you need to put 95000 in the box that says "New partition size in megabytes". The last box should say "Mount Point". Click the drop down. the first choice should be /. Choose that since this will be your root partition. After that press OK. You should now see your new partition on the list of partitions on your hard drive. There should still be about 5GB of free space left. Once again highlight "Free Space". Also, select "New Partition" again. This time the type of partition should be "Logical" and not "Primary". Skip down to "Use As". Click the drop down and select "swap area". Then click OK. 

Your partitions are now ready for Ubuntu and you can press "Next" at the bottom of the screen to continue with the installation.

---

### Post by jy0933 on 2010-04-11
here we go the pics 

[IMG]http://lh6.ggpht.com/_D0AlCUf7onw/S8F-y70p45I/AAAAAAAAACc/hDmM6N0IyZU/s640/2010-04-11%2002.47.30.jpg[/IMG]

i chose "advance"

[IMG]http://lh6.ggpht.com/_D0AlCUf7onw/S8F-9lsuDWI/AAAAAAAAACg/o1TnN0duQaQ/s640/2010-04-11%2002.47.12.jpg[/IMG]

the "free(un-used) space" is marked unusable...

---

### Post by jy0933 on 2010-04-11
some help plz?

---

### Post by cosine352 on 2010-04-11
a sata HD can only have 4 primary partitions (as I remember). And look like you already have 4. so you need to delet one of them to make a new primary partition.

---

### Post by jy0933 on 2010-04-11
what if i change 1 into logic partition

does that work?

---

### Post by jy0933 on 2010-04-12
when i was trying to partition...use the other software

it showed up that the who HD is dynamic

i'm not pretty sure

but as i can understand.... since i used win7 to do partition

seems that there wasnt any actual partition

the partitions showed on win7 are "fake"

which means  they are just like some "big folders" under the whole HD

is there anyone has a solution

btw

ima try new wubi ...cuz when i was trying to set up with old wubi and 9.10 64bit  (my win7 is 32bit) turned out problems ..when i tried 32bit 9.10..kind of work....

---

### Post by jy0933 on 2010-04-12
update


wubi trial fail

>>command=C:\Windows\System32\bcdedit.exe /set {e4fc7a66-451d-11df-b2f3-96eb40802714} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.

---

