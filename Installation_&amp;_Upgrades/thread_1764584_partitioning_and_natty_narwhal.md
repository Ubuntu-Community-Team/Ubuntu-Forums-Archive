---
title: "partitioning and natty narwhal"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by Wyxr on 2011-05-21
Hi forums! I just built a new computer and installed Windows 7 and Ubuntu to dual boot (successfully). Two hiccups, though, that hopefully won't be my undoing.

First, partitions. I did it with gparted during the ubuntu install (which I did second, if that matters). Windows 7 creates 2 primary partitions and I had read somewhere that I should have /boot/ be a primary and then have the 4th extend to have logical partitions for Ubuntu OS and swap. All done. The thing is, I left about 1TB unallocated, thinking for some reason I could use that as space the two could share (forgetting it still needs a partition). SO, in Windows Disk Management AND in Gparted (both launched normally and via Live CD), everything is locked down. Obviously I've used all 4 primary partitions, but nothing can be extended (the logical partitions have options to resize but can only decrease in size); the extended partition has almost no options--flags, information...I think that was it. No resize, no unmount. Sooo......whoops. What now?

Second, installed 10.10, took the upgrade to Natty Narwhal. Really really really not into the UI. What's the best way to regress/downgrade to 10.10? 

Thanks!

---

### Post by ronparent on 2011-05-21
First, I am not sure where you are at. Win 7 primary partitions are best created by win 7. In my system I used win 7 to create and install windows to. Outside of the two primary partitions win 7 created to install to, I used gparted to create an extended partition occupying the entire unallocated space not used by windows. 

Within that extemded space I used gparted to create whatever partitions I needed for ubuntu (including any partitions needed for ubuntu such as / for several different releases, swap and /home, and any additional ntfs win 7 partitions I needed). Win 7 recognized all the ntfs partitions so created and they were accessible by both all systems. In one instance when I used win7 to create an ntfs partition at the end of the disk - presumably within the extended partition - I found that win 7 designated the space as a primary partition and my primary partition count now exceeded four. 

I believe I was able to reclaim the space by using windows to delete the partition and gparted to extend the extended partition to include the space. I read somewhere that this is not permitted but I didn't know any better at the time and it worked for me. 

Make sure you are trying to enlarge the extended space, not any individual partition. Beyond that you might have to clear the drive and start all over! 

Second, at the login screen select the classic interface in the menu bar at the bottom of the screen. I don't like the new interface and run natty in the classic mode myself.

Good luck.

---

### Post by Dutch70 on 2011-05-21
Hi and welcome to UF

We can get a better idea of what you're talking about if you open Gparted & take a screenshot of it. Then attach it to your next post by using the paper clip in the toolbar.

ps. using the "select area to grab" function to take the screenshot will give us a better pic.

---

### Post by Wyxr on 2011-05-22
Ok, well, I experimented a little bit... :)

@ronparent I deleted the last logical partition in Windows (which saw no logical partitions, only primaries, incidentally). No change. Deleted the others Ubuntu had created (I knew I would probably be causing problems and would most likely need to install Ubuntu again). Still couldn't do anything. All I could do was shrink the primaries. 

OK, so indeed, I needed to reinstall. This time around I started in the same place I did the first time, with 2 Windows partitions, but now with a bunch of unallocated space). I made a primary partition, 1 gig, for /boot/. Then I made a logical partition for ~70gig for swap, then a logical partition ~300gig for Ubuntu (ext4), then with the rest I wanted to just make a generic logical partition that could be used by either system, but in order to format for ext4 it needed me to mount it to / or some other Ubuntu directory? which seemed like a bad idea. So I set it to FAT32 and mounted it to /windows. As soon as I started installing, it popped up a red X with an error of 000:000:000 (or something like that...all zeroes). It then brought Gparted back up and all of the partitions were set to /windows. Yikes. Abort.

Starting over. Same as last time except I didn't create that last FAT32 partition, so the last one is the one Ubuntu is installed on (no Natty upgrade this time). I hoped if I just left the last partition accounting for the whole rest of the disk, I could then shrink it or partition it later. No dice. Again, can't do anything with it. 

Attaching screenshots from gparted and disk management if it helps.

So all I want now is to take a chunk of that last partition and give it a drive letter, accessible to both. :/

---

### Post by Hedgehog1 on 2011-05-22
You partition sizes are kinda off.

Swap should be the size of your RAM + 10%.

Also, having a separate '/' (root) and '/home' partition are you better choices, a separate '/boot' partitions is only going to cause you grief later. 

Lastly, Windows cannot understand Linux partitions, but Linux can read/write to NTFS partitions just fine.

My I suggest that you make the 'sharing' partition NTFS. That way Linux sees it, and it can be assigned a drive letter from Windows, too.

***The Hedge***

:KS

p.s. Suggested partition layout (Windows is untouched):

[B]/dev/sda3 NTFS Large shared partition
/dev/sda4 extended partition
__/dev/sda5 EXT4 '/' (root) 20-30 gigs
__/dev/sda6 EXT4 '/home' 100 gigs? 200?
__/dev/sda7 Swap RAM size + 10%[/B]

---

### Post by ronparent on 2011-05-22
The Hedge has the right idea. NTFS partitions are all sharable including the one Win 7 is installed on (bad idea to access it with Ubuntu in anything other than read only for various reasons). Any NTFS partition in extended space should be created in linux. Win 7 will automatically assign drive letters when recognized.

One thing confuses me. On my system all my extended partitions do show as extended partitions with the win 7 disk management utility. For some reason yours don't. Is it possible you used Win 7 to create or manage some of these partitions? It will lead to problems if you try to use win 7 to manage those partition in any way.

---

### Post by Wyxr on 2011-05-22
> You partition sizes are kinda off.
> Swap should be the size of your RAM + 10%.

Ok. I had read "at least the size of how much RAM you have" for swap, so I just went over, not really understanding if it would help me or not (I have 12gb RAM so put in a little more than 4x that). Unnecessary I take it.

> Also, having a separate '/' (root) and '/home' partition are you better  choices, a separate 
> '/boot' partitions is only going to cause you grief  later. 

I see. Ok, I thought it was necessary to use grub as my boot loader. Why have root and home as separate partitions, though? Something about separating superuser and user activity or something

> Lastly, Windows cannot understand Linux partitions, but Linux can read/write to NTFS 
> partitions just fine.
> My I suggest that you make the 'sharing' partition NTFS. That way Linux  sees it, and it 
> can be assigned a drive letter from Windows, too.
> p.s. Suggested partition layout (Windows is untouched):
>[B]/dev/sda3 NTFS Large shared partition
> /dev/sda4 extended partition
> __/dev/sda5 EXT4 '/' (root) 20-30 gigs
> __/dev/sda6 EXT4 '/home' 100 gigs? 200?
> __/dev/sda7 Swap RAM size + 10%[/B]

Ok so to do this... I have the two Windows partitions which take up about 500gb, then format the whole rest of it for NTFS, then install Ubuntu and use Gparted to take a couple hundred GB off of that?

---

### Post by Hedgehog1 on 2011-05-22
It would be better if you did not make a large NTFS partition and trim it, instead make the /dev/sda3 partition the size you want it to end up at.

Because you are not installing any OS on the /dev/sda3 partition, you can do the whole thing from gparted off the LiveCD/USB:

Run gparted and remove all the partitions execpt /dev/sda1 & sda2. You may need to right click on the SWAP partition and select 'swapoff' if the swap partition is mounted.

Figure out how much space you want for Ubuntu (lets say 240 gigs total) and then create an NTFS partition that uses all but 240 gigs.  This is partition /dev/sda3. You can even format using gparted (but you will assign a drive letter from windows only)

Next, create an extended partition that uses the rest of the drive: /dev/sda4

Now create the thee partitions for Ubuntu:
__/dev/sda5 EXT4 '/' (root) 30 gigs
__/dev/sda6 EXT4 '/home'  200 gigs
__/dev/sda7 Swap RAM size + 10%

Then go ahead and install Ubuntu right into these partitions:

When you get to the 'allocate disk space' screen, select the '**Something Else**' option for Natty/11.04.
If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

The next partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

Lastly, the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

***The Hedge***

:KS

---

### Post by Wyxr on 2011-05-22
Success! 

sda1 Hidden Windows system partition (100MB)
sda2 C: (Windows/NTFS) - 500GB
sda3 F: (NTFS) - 1.15TB
ext4/sda5 - /root - 50GB
ext4/sda6 - /home - 210GB
ext4/sda7 - swap - 24 GB (a little more, yes...maybe it's unnecessary but oh well)

I can get to F: from both operating systems. Actually I can get to C: from both, as well, but as you say I won't mess with it in Ubuntu. 

Wonderbar. 

I really appreciate the help!

Now, finally, to play with my new toy.. :)

---

### Post by Hedgehog1 on 2011-05-23
In my best 'Mr. Burns' voice:

*[SIZE="4"]'Excellent...'[/SIZE]*


***The Hedge***

:KS

---

