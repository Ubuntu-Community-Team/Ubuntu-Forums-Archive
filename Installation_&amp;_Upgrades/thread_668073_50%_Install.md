---
title: "50% Install"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by JR Tyner on 2008-01-15
I have a Dell Inspiron 1521 Laptop with Windows Visa.
I created a 10 GB partition to install Ubuntu 7.10 I386 as a dual boot.
Processor: AMD Turion 64 X2 Mobile Technology TL-56 1.80 GHz (Dual)
Disk Drive: WDC WD1200BEVS-75RST0 ATA
Network Adaptor: Dell Wireless 1505 Draft 802.11n WLAN Mini-Card

I start the install from the Live CD, but it freezes at 50% each time.

I restarted and tried to make a basic text file on the partition while running the Live CD, and it says I don't have permission.

Any ideas?

---

### Post by jeffus_il on 2008-01-15
What file system is on the partition?

---

### Post by JR Tyner on 2008-01-15
Ntfs

---

### Post by jeffus_il on 2008-01-15
> **JR Tyner said:**
> Ntfs
You problem may be that ntfs is not writeable by the live CD,
During installation reformat it to ext3.

---

### Post by JR Tyner on 2008-01-15
Didn't work.

I reformatted it to ext3.

The Mount point was: /media/sda2

I get: "No root file system is defined. Please correct this from the partitioning menu."

For it to start, I have to set it to Mount point: / 

I got this message this time:
File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 32043 (63962 expected); size of FATs is 126 sectors (250 expected).

You have not selected any partitions for use as swap space. Enabling swap space is recommended so that the system can make better use of the available physical memory, and so that it behaves better when physical memory is scarce. You may experience installation problems if you do not have enough physical memory.

If you do not go back to the partitioning menu and assign a swap partition, the installation will continue without swap space.

---

### Post by Partyboi2 on 2008-01-15
when you manually set the partitions  make a / (root) partition a /swap and a /home partition.
depending on how much ram you have is what you would set for /swap

---

### Post by zipperback on 2008-01-15
If you are just wanting to install Ubuntu on your system as the only operating system, then simply boot the live cd, then when it gets to the desktop, double click the install icon, then when it gets to the partitioning portion of the installation process, select the second option that says to use the whole hard drive.

Let it use the defaults, and then just install it.

Also, when you first boot the livecd you should select the verify media option, and verify the installation media as being without problems.

This is the easiest method to install it.

If you want to setup your system for dual boot then follow this link.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by Circus-Killer on 2008-01-15
> **Partyboi2 said:**
> when you manually set the partitions  make a / (root) partition a /swap and a /home partition.
depending on how much ram you have is what you would set for /swap

just to extend the previous post, most people tend to make their swap partition double the size of their ram. for example if you have 512MB of ram, then your swap would be 1GB.

the /home partition isn't an essential, but is very common and recommended.

---

### Post by JR Tyner on 2008-01-15
How big should these partitions be?

/ 
/swap
/home 

I have to keep in mind that soon I want to have it a triple boot system (Visa, Ubuntu, and another Linux)

---

### Post by JR Tyner on 2008-01-15
> **Circus-Killer said:**
> just to extend the previous post, most people tend to make their swap partition double the size of their ram. for example if you have 512MB of ram, then your swap would be 1GB.

I have 1918MB ram.

> **Circus-Killer said:**
> the /home partition isn't an essential, but is very common and recommended.

What would I use it for.

I'm probably asking some dumb questions right now, but I haven't been able to sleep for awhile due to pneumonia and migraines, and my only experience with Linux so far is running Knoppix off a CD.

---

### Post by jeffus_il on 2008-01-15
Don't need double the ram for certain, when you run your system, put a system monitor on the panel to watch your swap usage, I have 1 Gb or ram and hardly ever use swap space, you will use less because you have more memory, seems like dropping the NTFS was a problem since your errors changed, maybe not the only one.

---

### Post by JR Tyner on 2008-01-15
> **jeffus_il said:**
> Don't need double the ram for certain, when you run your system, put a system monitor on the panel to watch your swap usage, I have 1 Gb or ram and hardly ever use swap space, you will use less because you have more memory, seems like dropping the NTFS was a problem since your errors changed, maybe not the only one.

How would adding a second Linux boot down the road effect the swap space I make for this boot? 

Would they both use the same swap space? 

I'm not really sure what swap space is, it sounds like window's virtual memory.

---

### Post by jeffus_il on 2008-01-15
Yes they can all use the same swap partition, since it is a temporary store only while the OS is running, there may be an exception if you hibernate to the swap partition, I don't know, but if you boot a livecd Linux distro, it will  pick up the swap partition and use it, even though they are not running from the hard drive.

In short the computer memory is divided into pages, this is the unit which the computer allocates, manages, and writes to the swap file, also called a page file. When a process runs short of memory, it writes little used pages it has in memory to the swap area, freeing up memory for other uses. This is what your swap partition is used for, (much too short a description) If you want to read about it, I'm sure google will be happy to help!

---

### Post by JR Tyner on 2008-01-15
How big should I make the home partition?

---

### Post by jeffus_il on 2008-01-15
It's your home, you put the stuff in and you determine the size, For mail and regular stuff, 5Gb should be more than enough, If you download lots of stuff to your home directory, it might not be enough, though you could always open another partition and mount it under your home directory for downloads, the Linux file system is very flexible ...

---

### Post by JR Tyner on 2008-01-15
If I put in a second version of Linux, will they share the same home partition too?

So far I have a 85 GB Visa patition, a 10 GB partition for the "/", 3 GB free space, and I decided to go ahead a make a 2 GB partition for the "/swap" partition since I had the space.

---

### Post by JR Tyner on 2008-01-15
What partition do I put the files I want Ubuntu to share with Visa in, like my Thunderbird and Firefox profiles?

---

### Post by Partyboi2 on 2008-01-15
I have not tried these guides, but have thought about doing this. Let me know how you get on.
[http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)
[http://www.downloadsquad.com/2007/05/23/sharing-your-thunderbird-and-firefox-data-between-ubuntu-and-win/](http://www.downloadsquad.com/2007/05/23/sharing-your-thunderbird-and-firefox-data-between-ubuntu-and-win/)

---

### Post by Sef on 2008-01-15
Read [Psychocat's site]("http://www.psychocats.net/ubuntu/index.php") for how to dual boot and more.

---

### Post by jeffus_il on 2008-01-16
> **JR Tyner said:**
> If I put in a second version of Linux, will they share the same home partition too?

So far I have a 85 GB Visa patition, a 10 GB partition for the "/", 3 GB free space, and I decided to go ahead a make a 2 GB partition for the "/swap" partition since I had the space.
You decide, if you want to, the install prompts you to give the mounts. You can also change it at any time in your fstab file.

---

### Post by jeffus_il on 2008-01-16
> **JR Tyner said:**
> What partition do I put the files I want Ubuntu to share with Visa in, like my Thunderbird and Firefox profiles?

You don't have to choose ahead of time, you can share whatever directories ypu like, normally if you share your home directory, you will have access to the thunderbird and firefox directories.

---

### Post by JR Tyner on 2008-01-16
Is 10 GB big enough for the "/" partition?

Maybe that's why it still stops at 50%.

---

### Post by jeffus_il on 2008-01-16
Yes.

---

### Post by JR Tyner on 2008-01-16
Then what does it mean when it says:

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 32043 (63962 expected); size of FATs is 126 sectors (250 expected)."

---

### Post by jeffus_il on 2008-01-16
> **JR Tyner said:**
> Then what does it mean when it says:

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 32043 (63962 expected); size of FATs is 126 sectors (250 expected)."

What file system are you installing on the partition?

---

### Post by JR Tyner on 2008-01-16
I'll retry and get screenshots.

---

### Post by JR Tyner on 2008-01-16
I partitioned in Vista.

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/1.jpg[/img]

---

### Post by JR Tyner on 2008-01-16
these are the partitions in Ubuntu

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/2.png[/img]

---

### Post by JR Tyner on 2008-01-16
setting up

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/3.png[/img]

---

### Post by JR Tyner on 2008-01-16
setting up

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/4.png[/img]

---

### Post by JR Tyner on 2008-01-16
setting up

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/5.png[/img]

---

### Post by JR Tyner on 2008-01-16
Manual Partitioning

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/6.png[/img]

---

### Post by JR Tyner on 2008-01-16
My partitions

[img]http://ncrcag.com/Linux/Ubuntu/screenshots/7.png[/img]

---

### Post by Sef on 2008-01-16
If you are installing Ubuntu on F, use Ubuntu's default file system, which is ext3.   NTFS is a Microsoft's proprietary file system, and Ubuntu if installed on NTFS will not work very well.

---

### Post by JR Tyner on 2008-01-16
By this shot, I set my 10 gb partition as "/" and I'm setting up my swap partition:



[img]http://ncrcag.com/Linux/Ubuntu/screenshots/8.png[/img]

---

### Post by JR Tyner on 2008-01-16
> **Sef said:**
> If you are installing Ubuntu on F, use Ubuntu's default file system, which is ext3.   NTFS is a Microsoft's proprietary file system, and Ubuntu if installed on NTFS will not work very well.



Yeah, but I'm repartitioning them to Ext3 as you'll see.

---

### Post by JR Tyner on 2008-01-16
Here I am repartitiong "/home" to Ext3:



[img]http://ncrcag.com/Linux/Ubuntu/screenshots/9.png[/img]

---

### Post by JR Tyner on 2008-01-16
Here it is, 2 partitions repartioned as Ext3 and one as SWAP





[img]http://ncrcag.com/Linux/Ubuntu/screenshots/10.png[/img]

---

### Post by JR Tyner on 2008-01-16
This is the warning message I'm getting, I posted it on page one, but here's the image:



[img]http://ncrcag.com/Linux/Ubuntu/screenshots/11.png[/img]

---

### Post by JR Tyner on 2008-01-16
This no reporting operating system message always seemed weird to me:





[img]http://ncrcag.com/Linux/Ubuntu/screenshots/12.png[/img]

---

### Post by JR Tyner on 2008-01-16
Who are you?






[img]http://ncrcag.com/Linux/Ubuntu/screenshots/13.png[/img]

---

### Post by JR Tyner on 2008-01-16
Ready to install






[img]http://ncrcag.com/Linux/Ubuntu/screenshots/14.png[/img]

---

### Post by JR Tyner on 2008-01-16
Final step





[img]http://ncrcag.com/Linux/Ubuntu/screenshots/15.png[/img]

---

### Post by JR Tyner on 2008-01-16
And it stops at 15% this time, wtf?












[img]http://ncrcag.com/Linux/Ubuntu/screenshots/16.png[/img]

---

### Post by JR Tyner on 2008-01-16
So there you go, it stopped at 15% this time. 



As you can tell from the clock, I gave it over half an hour. Before, it's always been stuck at 50% by this time.

---

### Post by jeffus_il on 2008-01-16
Not clear why it hangs on "detecting file systems".
I would try to set up each partition individually ( /, home, and swap) before running install,
using the partition editor gparted.
If there is a problem there, you will pick it up.

---

### Post by JR Tyner on 2008-01-16
I just so happen to have a gparted iso burned on a DVD. I had read about it in the Linux journal, that's where I learned about Ubuntu. I'll try that and let you know.

---

### Post by JR Tyner on 2008-01-16
I put the dvd in, clicker the first load option, fell asleep, and when I wole up the screen was black. Is it because I burned it to a DVD instead of a CD?

---

### Post by jeffus_il on 2008-01-16
Shouldn't be a problem, reboot and see what happens.

---

### Post by JR Tyner on 2008-01-16
I inserted the cd and rebooted.

I waited for the menu and pressed enter. Should I have tried a different option?

This was what it said on screen when it stopped, when it stopped here last night, I went to bed and found a blank screen when I awoke.

I need a minute to get the screen shots off  my phone.

---

### Post by JR Tyner on 2008-01-16
That didn't work, so I retried it and this time I took pictures d uploaded them to my server.

---

### Post by JR Tyner on 2008-01-16
[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20001.JPG[/img]

---

### Post by JR Tyner on 2008-01-16
searching

[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20005.JPG[/img]

---

### Post by JR Tyner on 2008-01-16
Scanning

[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20007.JPG[/img]

---

### Post by JR Tyner on 2008-01-16
Error








[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20009.JPG[/img]

---

### Post by JR Tyner on 2008-01-16
Output error







[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20010.JPG[/img]

---

### Post by JR Tyner on 2008-01-17
[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20011.JPG[/img]

---

### Post by JR Tyner on 2008-01-17
[img]http://ncrcag.com/Linux/GParted/SOMETHING%20FOR%20BRIAN%20012.JPG[/img]

---

### Post by JR Tyner on 2008-01-17
Those are the error messages I get when I try to use GParted to fix my partitions so I install Ubuntu.



Can anyone tell me what that means?

---

### Post by jeffus_il on 2008-01-17
Hi, I see something like "No raid disks"
When you boot you computer go into the bios setup, usually by hitting <delete>
In the setup look for the section with hard disk settings.
It may be setup for raid disks, change this to regular "IDE"
I am assuming that you have one harddisk and intend to use it as a regular hard drive and not a multidisk raid array.

This is my guess from what I have managed to gather from your posts.

---

### Post by JR Tyner on 2008-01-17
:confused: I looked over every bios option (it's the F2 key on Dell Inspirions) and there is no mention of Raid or IDE.

This is probably my whole problem and afterwards Ubuntu will install without a hitch, as soon as I can ](*,)

---

### Post by Partyboi2 on 2008-01-17
If you are setting up raid, you will need the alternate cd as the ubuntu live cd does not have the tools to set it up. But are you using raid? Another option is to delete the partitions you have already made and defrag vista a few times. Then try making all the partitions again with the live cd, or try the alternate cd.

---

### Post by JR Tyner on 2008-01-17
> **Partyboi2 said:**
> But are you using raid?

No, I'm trying to figure out how to disable it. Why would I use it on a laptop? :confused:

> **Partyboi2 said:**
> Another option is to delete the partitions you have already made and defrag vista a few times. Then try making all the partitions again with the live cd, or try the alternate cd.

I'll go ahead and try this.

---

### Post by JR Tyner on 2008-01-17
[img]http://ncrcag.com/Linux/GParted/no%20partitions.jpg[/img]

---

### Post by JR Tyner on 2008-01-17
Any idea why the two unallocated spaces did not combine? I had free space, and I deleted three partitions, Shouldn't I have one partition and one mass of unallocated space? :confused:

---

### Post by Partyboi2 on 2008-01-17
Resize vista to take the unallocated space, so that you will end up with 2 partitions Vista and the EISA. then defrag vista a couple of times. Then resize vista down and leave the unallocated space from it. Then boot the ubuntu live cd and choose 
use the largest continuious free space. This will take care of the /swap and / partition as well as hopefully install the system. You can create a seperate /home partition at a later time if you need one.

---

### Post by JR Tyner on 2008-01-17
> **Partyboi2 said:**
> Resize vista to take the unallocated space, so that you will end up with 2 partitions Vista and the EISA. then defrag vista a couple of times. Then resize vista down and leave the unallocated space from it. Then boot the ubuntu live cd and choose 
use the largest continuious free space. This will take care of the /swap and / partition as well as hopefully install the system. You can create a seperate /home partition at a later time if you need one.

Brilliant. 

On a side note while I defrag, doesn't the EISA partition have something to do with me having a dual core system?

---

### Post by Boguz on 2008-01-17
I had the same problem as you. To me it you stop the installation always on 56%.
First i thought it was from the CD, so i downloaded it again, but the same was happening...

I looked for a solution but i did not find it.
Then i friend told me to try to download and use the Alternate Desktop Version of the CD
(you can find it here: [[SIZE="4"]HERE[/SIZE]]("http://www.ubuntu.com/getubuntu/download") and then check the box in the end where it says :*"Check here if you need the alternate desktop CD..."*).

I don't know what difference it makes, but, for me, it worked perfectly...

Maybe it is worth a try for you also...

;)

---

### Post by JR Tyner on 2008-01-17
> **Boguz said:**
> I had the same problem as you. To me it you stop the installation always on 56%.
First i thought it was from the CD, so i downloaded it again, but the same was happening...

I looked for a solution but i did not find it.
Then i friend told me to try to download and use the Alternate Desktop Version of the CD
(you can find it here: [[SIZE="4"]HERE[/SIZE]]("http://www.ubuntu.com/getubuntu/download") and then check the box in the end where it says :*"Check here if you need the alternate desktop CD..."*).

I don't know what difference it makes, but, for me, it worked perfectly...

Maybe it is worth a try for you also...

;)



What is the difference in the install? Do I just run it from my desktop, or do I need to burn it too?

---

### Post by Partyboi2 on 2008-01-17
you need to burn the iso to disk just like you did for the live cd, the alternate cd is a text base install and is pretty straight forward to use. :)
How did you go with defraging and installing from the live cd?

---

### Post by JR Tyner on 2008-01-17
> **Partyboi2 said:**
> you need to burn the iso to disk just like you did for the live cd, the alternate cd is a text base install and is pretty straight forward to use. :)
How did you go with defraging and installing from the live cd?

The defraging just ended #-o

---

### Post by JR Tyner on 2008-01-17
Now I'm starting the second defrag.

---

### Post by JR Tyner on 2008-01-17
This is odd. Windows won't let me add the 10 GB partition.
 
When I first got my laptop it had a 100 GB Visa Partion, and a 10 GB partition that it backed Vista up to.

---

### Post by jeffus_il on 2008-01-18
A disk may be partitioned into a maximum of four primary partitions, if you already have four,  It will not let you add more. Did you get an error?  If this is the problem, you have to delete one (after saving the data), and create  an extended partition, which  will enable you to add many more partitions which reside inside the extended partition, called logical partitions.

---

### Post by JR Tyner on 2008-01-18
That's it, Microsoft has gone to far. I can't work Vista for another day. I have to get rid of it now.

---

