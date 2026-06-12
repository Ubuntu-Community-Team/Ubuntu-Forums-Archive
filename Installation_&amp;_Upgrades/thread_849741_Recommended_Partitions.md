---
title: "Recommended Partitions"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Dave_P on 2008-07-04
Hi Guys,
I'm fairly new to linux but not a total newbie. I've been MS free now for a month :).

Anyway I've decided to do a fresh install after reading various articles on partitioning and the benefits of keeping thing's separate. Problem is that the articles I have read often gave conflicting advice so I find myself somewhat confused.

I will be using my entire HDD for this install (500 Gig) and would ask advice from you as to a recommended partitioning scheme.

Does below seem ok..?

/ 100 Meg
/usr 30 Gig
/var 1 Gig
/boot 20 Meg
/tmp 100 Meg
/swap 3 Gig
/home The rest of the Disk.


Computer has 3 Gig of Ram, is a Dual core HP Pavillion. I do loads of differing stuff, but would also like to be able to emulate a web server for testing websites. I have just received the 8.04 Ubuntu server disk and plan on doing a clean install soon. I'd like to get the partitioning right 1st though and so would appreciate your advise.

Thanks.

---

### Post by scragar on 2008-07-04
the only one you will find universal agreement on is the seperate home, a lot of people will agree with the boot as well.

all depends on what you want as well, the seperate /var is to prevent logs taking up most of some smaller HDs, which won't happen on a 500GB drive. a seperate /tmp I can't see the benifits of, since tmp is cleaned out all the time, and doesn't ever appear to get any larger. /usr is the most part of your OS, so adding this on a seperate partition doesn't make as much sense as you would think, since it doesn't offer any of the benifits you normaly gain from seperate partitions, unless you reinstall a lot, in which case the odds are the folder will be overwrote with the new installed contents anyway.

---

### Post by Dave_P on 2008-07-04
Ok Thanks for that.
So is below a better partition list..?

/      100M
/boot  20M
/home  Rest of HDD
/swap  3Gig

Also I'm assuming that the partition order has a relevance, is the above correct.?

---

### Post by scragar on 2008-07-04
partition order is irrelevant, although since your limited to 3 main partitions per disk you'll have to use an extended partition to house at least 2 of your partitions(I'd say / and /boot, however this is only because then the OS is in 1 main partition instead of 2)

you may want to make / a bit bigger as well, the OS is normally around 2 GB in size, although some people have(by installing a LOT of programs) managed to get it to 4GB, I'd recommend making it between 3 and 3.5GB though, because very few people have got it to 4GB(mines @ 2.6GB with a fair number of programs installed)

---

### Post by sFX KeZeF on 2008-07-05
Hello All.....

I will say I am very new to Linux and Ubuntu, and need some info on how many logical partitions I need and why.

scragar, I know or at least pretty sure you know your allowed more than 3 partitions, it might confuse some people in regards to partitioning the drive for installation, and partition placing does matter, at least from what I understand.

Your allowed 4 primary partitions, many of the popular installs (Win, OS X, etc) like to be installed in Primary partitions, with Linux usually being an exception. So what most people will do is create 3 Primary Partitions for OS's such as Windows XP, Vista, Mac etc, then take what would be the last or fourth partition and make what they call an extended partition, in this so called extended partition you can create numerous logical partitions, which will accommodate numerous other operating systems.

As far as the order and why it matters is due to the way hard drives are currently made. Again if I understand this properly many years ago hard drives were made to read at the same speed across the whole platter / disk, this was done by creating bigger gaps in between the sectors on the outer edges / tracks where as the sectors on the inner tracks were not spaced so to speak. Currently the manufacturers are trying to get the best performance and density from the drives so the sectors are not gaped, thus allowing the data at the edges of the tracks (which spins faster than the inner tracks closer to the spindle) to pass under the heads at a faster speed, in turn giving you better read speeds. 

Sooooo, by placing partitions with critical data (Swap, Page, Hibernation files etc.. - normally not OS type files) at the outer edges does give some slight advantage as that data can be read quicker. I think for instance the SA area on 3.5 drives are at the outer edge, while the manufacturers of 2.5 drives put the SA or negative tracks near the spindle because they do not want to sacrifice drive performance by wasting the outer tracks with SA info / data. 

Now if I am not getting this right, please by all means correct me so I don't continue to look like an idiot in other posts, lol!

Ok, now for my question, why so many partitions for Linux, what is stored in each of those partitions? Because during the install it looked like I could have create about 10 partitions, lol. I don't mind reading up for myself if someone could dump a link here to a good article that explains the whys and why not's on Linux partitions.

Thanks to all who are helping us Linux newbies out! It truly is appreciated!!!!

Tom

---

### Post by sFX KeZeF on 2008-07-05
PS. I am looking to boot 3 to 4 OS's XP, Vista, Linux and maybe Mac.

---

### Post by Herman on 2008-07-05
> PS. I am looking to boot 3 to 4 OS's XP, Vista, Linux and maybe Mac.> Ok, now for my question, why so many partitions for Linux, what is stored in each of those partitions? Because during the install it looked like I could have create about 10 partitions, lol. I don't mind reading up for myself if someone could dump a link here to a good article that explains the whys and why not's on Linux partitions.I always recommend making one single integral / (root) partition plus a small swap area for Linux.
I don't believe in dividing up an installation into many small partitions because in fact, what you are doing is setting unnecessary restrictions on yourself. 
Partitions are relatively rigid and slow to resize, whereas directories are flexible and efficient, they are always the perfect size no matter what happens, you don't need to use special software to resize a directory when its contents change.
If you have more than one operating system per hard disk, having many partitions per operating system can quickly become confusing when you need to remember which partition belongs to which operating system.
You still need to make backups just the same, so splitting an installation into many partitions is only making extra complications and extra work for yourself. There will be more file systems needing to be checked on boot-up too.
Not everyone thinks creating extra partitions is a good idea at all, I don't.
Maybe for a server or a system with many users where you need to be able to restrict people it might be useful, but for a single user desktop I don't think it makes much sense.

Regards, Herman :)

---

### Post by misterbk on 2008-07-05
Agreed, for single user stations the partitioning would probably get in your way more than help you.

My web travels have taught me that server guys tend to like multiple partitions because you can then set security restrictions on them.  Like for example /var/log and /tmp can be set as separate partitions, and by doing that you gain the ability to set the "noexec" flag so that if some attacker managed to cause one of your log files or temp files to contain malicious code, they would not be able to execute that code.  (At least, that's what server guys have said.  Server guys are more paranoid about their systems.)

I'm installing Kubuntu on a hybrid server and home station.  It will serve up mp3s to my stereo and start playing like an alarm clock, record TV if I get that working, and do some web browsing if I don't feel like turning on my main machine.  It also serves samba, FTP and Web though, depending on my needs, so I will be doing some partitioning.

Here's the table I had before:
Filesystem	Size  	Used 	Avail 	Use%	Mount
/dev/hda1    	37M   	11M   	24M  	32% 	/boot
/dev/hda4    	170G  	112G	50G  	70% 	/music
/dev/hda5    	749M   	35M  	677M   	5% 	/var/log
/dev/hda6    	610M   	18M  	562M   	3% 	/tmp
/dev/hda7	16G   	14G  	436M  	98% 	/

[edit] wups, df doesn't report the swap.  There is an 800MB swap partition there. [/edit]

/tmp and /var/log have the "nosuid" and "noexec" flags set as recommended to me before.  My home folders are piled in with "/" because I didn't know how I would be using those when I initially partitioned.  They probably account for much of the space on "/".  The section of drive I was most concerned about not having to reformat was my large music collection, so that went on /music.

I have NO IDEA if the "noexec" and "nosuid" flags are even relevant today, if there are actual attacks that use them to compromise systems, or if the whole deal was purely theory some time in the 80's and just crept its way into practice for good measure.  The servers used by the last I.T. dept. I worked for used far more partitions even than that.

One thing I'm pretty sure of is that you want to avoid being able to accidentally fill up your "/" partition.  (Notice I did a poor job of avoiding that up above...)  I guess it can make the system hard to boot or something?  I know XP Pro can become completely hosed (unbootable) if its C: drive completely fills up.  

I'm working on a new partition table right now.  Thanks above for reminding me to put my swap partition on the outside of the disk!  That trick will significantly boost any disk activity that has a reasonable sequential read / write component, and won't have any negative impact on activity that doesn't.

---

### Post by Herman on 2008-07-05
> One thing I'm pretty sure of is that you want to avoid being able to accidentally fill up your "/" partition. (Notice I did a poor job of avoiding that up above...) I guess it can make the system hard to boot or something? I know XP Pro can become completely hosed (unbootable) if its C: drive completely fills up. 
 Yeah, Linux file systems never need defragging as long as they are less than around 80% full, so as long as people allow enough extra in their partition sizes so there's at least 20% free space in each partition they should be fine.

---

### Post by esteckis on 2008-07-05
I thought that if you had a separate home partition, then if you had a fatal corruption or crash, you could just reinstall Ubuntu and not overwrite your home partition so all of your info and settings are saved?

---

### Post by Slihp on 2008-07-05
Hey guys,

Im a linux newbie as well. Im having some trouble setting up my partitions when installing hardy. I entered all the relevant information regarding my swap space partition but when i press the create button the system hangs. Any ideas?

80gig IDE
AMD Athalon 64
1 gig DDR
Nvidia  TV 256 meg.

Thanks

---

### Post by misterbk on 2008-07-05
Here's what I landed on for my half-server jukebox setup.

Goals:  

* Secure /var/log and /tmp from code execution since they are easy to write to.
* Keep myself from filling up "/" but still have room for doing some minor stuff in /home and storing a large music collection in /music
* enough temp space to keep a CD image if some program likes to use /tmp
* keep things that should load fast at the outside edge of the disk


/var/log	400mb	ext3
/home		8gb	ext3
/music		170gb	ext3
/		23gb	ext3
/tmp		1.1gb	ext2
swap		750mb	swap
/boot		50mb	ext2


This because I noticed in my previous run, which has been up for a year and a half, /var/log stayed really small, and /home took over "/" because I didn't separate them.  I don't really intend to do much in the home directories though I do set the box to download .iso files now and then.  I could probably tune this a bit but I kind of expect to land back on KDE 3 for this box after briefly trying 4.

If someone has an idea what a good maximum size for "/" is, excluding /home and /tmp, I'd be curious.

---

### Post by Herman on 2008-07-05
> Im a linux newbie as well. Im having some trouble setting up my partitions when installing hardy. I entered all the relevant information regarding my swap space partition but when i press the create button the system hangs. Any ideas?If you're using the Hardy Heron 'Desktop' Live/Install CD, try running it as a Live CD and use Gnome Partition Editor in the Live CD to create your partitions first, then after your partititons are created, run the installer. 
We can have a maximum of four primary partitions, or up to three primary partitions plus one that is called an 'extended' partition. 
An extended partition may be subdivided into many logical partitions, providing they are 'contiguous'. (They can be separated by a gap of free space, but we can't place a primary partition in between our logical partitions).
Linux can be installed in a logical or a primary partition, and the swap area can be primary or logical.

---

### Post by Herman on 2008-07-05
> I thought that if you had a separate home partition, then if you had a fatal corruption or crash, you could just reinstall Ubuntu and not overwrite your home partition so all of your info and settings are saved?:) Hello esteckis, That is partially true, but always remember that you still need to back up your data to some separate media just the same.
It's heart breaking to be trying to help someone who has lost all their data because they thought having a separate /home would 'keep their data safe', in the event of 'something happening' to the rest of their operating system, so they thought they were excused from the need for making regular backups.
With the types of files most people want to keep these days, (music files and video files), most people have such a large amount of data that they probably need another hard disk, (internal or USB external), for keeping backup copies of their data.

As long as people still bother to invest in another hard disk and take the time to make regular backups of the data they want to store, there's nothing wrong with having a separate /home partition, other than the fact that you're restricting your own potential for growth of either your / (root) partition or your /home.
If I was sharing my PC with other people, such as other family members or if it was a server or a school or work computer it would make sense to have a separate /home to restrict the amount of hard disk space /home can take up. That way if people try to store too many files, it won't affect the / (root) operating system. The system will still boot and you can police who is being a hard disk hog and ask them to remove some files or else you'll take some kind of action.

If it's just your own PC and you are the only user, why restrict your self?

---

### Post by Tanker Bob on 2008-07-05
I'm a believer that fewer partitions is better. I have a 320GB Raid 1 setup partitioned as:

/ 14GB ext3 (only 41% full with a fully loaded OS and lots of add-ons)
/home 282GB (rest of the disk minus the swap, 47% in use)
swap 1.8GB (I have 2GB SDRAM, so this rarely gets used)

I believe that these are the only partitions worth making.

I strongly believe that the /home directory should be a separate partition. I have upgraded or reinstalled the OS a number of times, including creating the RAID 1 array, and having a separate /home partition kept my data and settings intact through all those changes. I just finished upgrading to 8.04.1 yesterday, and it was pretty much operational as soon as it finished because my data and personal settings were preserved on the /home partition. As has been said, that in no way provides an excuse not to back up your data regularly. I have a separate 320GB drive for that purpose, plus CDs for pictures and stuff.

---

### Post by tipiglen on 2008-07-07
A stupid question perhaps, but here goes anyway.

How do you set it up so that home goes on its own separate partition?  Is it with a link from /home?

I'm going back to Gutsy, since hardy is giving me screen resolution restrictions and won't recognise my wireless card - says it's 'disabled', but Xubuntu Hardy recognises it and connects at boot.

I intend (unless otherwise advised to keep Xubuntu on the present sda1 with swap on sda2, and split the remainder between sda3 and sda4, one for home and the other for gutsy.  It's an older computer (emachines633 or suchlike - on the laptop elsewhere at the moment) with a 15GB HDD (13.99GiB), leaving about 8GiB for sda3 & 4.  

I also have an external 300GiB usb drive for backup, and may try to use it for /home, but the machine has a bad habit of freezing up if asked to transfer any file above 100MB or so, even transfers within its own internal HDD.  Any suggestions what might be causing this behaviour?  It's been a feature of the damned thing ever since I bought it for my daughter at uni eight or nine years ago.  I blamed it then on Windoze Millennium Edition, but it still happens, and there ain't been any microtrash anywhere near it for a year.

Details of my present frustration with Hardy here:
[http://ubuntuforums.org/showthread.php?t=851442&highlight=wireless+hardy+xubuntu](http://ubuntuforums.org/showthread.php?t=851442&highlight=wireless+hardy+xubuntu)

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by Tanker Bob on 2008-07-07
> **tipiglen said:**
> A stupid question perhaps, but here goes anyway.

How do you set it up so that home goes on its own separate partition?  Is it with a link from /home?

When you install Xubuntu, it should ask about partitioning the drives. When you reach the partitioning screen, the partitioning program allows you to set the various system directories to individual partitions. That's where you can set one partitions (~10-15GB) to / (root), your large data partition to /home, and a small partition (size equal to the amount of RAM that you have) to "swap".

---

### Post by tipiglen on 2008-07-07
Thanks Bob,

Just wondering if there's any reason why two different OS versions shouldn't share a common home directory?

I've got xubuntu set up and working fine and I've gone back to feisty on another partition on the same box - it's far quicker on the slow processor (633MHz) than Hardy was, AND the wireless works AND the screen resolution is variable....

It seems I might keep both versions on the box sharing the swap (they already do), and why not the /home as well.  After your answer, I did the feisty install, and noted that all that happens for the separate /home partition is that it gets mounted on /home in fstab  - duhhh!  So I thought why not mount the same partition on /home for either OS???

I already mount the root of the non-leading OS anyway to enable tweaking and such.  The idea of a shared home seems in line with your philosophy of keeping the number of separate things down.  

Just thinking

Salaam/Shalom/Shanthi/Dorood/Peace
   Namaste  -ed

---

### Post by Tanker Bob on 2008-07-08
tipiglen,

I've never tried it, but I don't think that it's a good idea. The /home directory holds all the preference settings for your programs. There are bound to be differences or conflicts across the versions, including some system settings.

Perhaps someone with more experience can offer their thoughts before you take the plunge.

---

### Post by misterbk on 2008-07-20
Hi guys,

I had some problems with the partition scheme I posted above, remembered this thread and thought I'd share.

I did separate /var/log and /tmp partitions, mounted noexec. The box does some light public serving and I don't want to worry about script kiddies.  Here's what happened:

#1:  Apparently when installing some packages through apt (ClamAV did this specifically), the installer will drop stuff into /tmp and try to execute it.  Kind of annoying, but I guess /tmp can't be mounted noexec.  (So, no reason to make it a separate partition.)

#2:  I installed MythTV on this machine, and apparently it has the nasty habit of building up ridiculously big log files.  Over the course of two weeks it filled up my ENTIRE /var/log partition, all by itself, with a gigantic text file full of the same ten lines over and over again.  That caused me filesystem errors.  Somehow the 5% superuser safety didn't kick in and the partition was legitimately 100% full.  (not even 99.9%.)  Deleting the MythTV log didn't free the space.  (The sum of all files was 2% of the partition, yet there was only 2% free space.)  

So, I guess if you have a separate /var/log you have to watch its free space a bit.  I'm fine with that, I'm just going to get a disk space widget.  I can't think of any reason I'd ever want to have more than 100MB of logs total on my system.


So, at this point I'm wondering.  Did I ***cause myself problems*** by having a small separate /var/log partition, or did I ***rescue myself*** from accidentally filling up my root partition and having to fsck my ENTIRE disk?  (Along with the possibility of corrupting my / partition because of it?)

I admit that if this had been my main system or a laptop, it would have been slightly different.  A single partition would have filled up very slowly, and I probably would have noticed something wrong, even if I didn't immediately figure out the space was all going to /var/log/mythtv.

Anyway, the full /var/log folder only caused me a few reboots and 5 minutes worth of running fsck and holding down the 'y' button. I think I benefited from the fact that the damaged partition was fairly small and had only non-critical files, as opposed to being my big '/' partition full of everything that matters.  So I'm keeping the separate /var/log.  

If I partitioned this box again I would use this setup:
```

Size  Use%    Mounted on

** remember this is a media box.  I don't "use" the system daily. This effects my partitioning.**

(Main Disk)
 19G   17%    /
 45M   28%    /boot
7.5G    3%    /home       # really I am just wasting space here.
                          # I store anything big in /music or /basement.
161G   44%    /music      # noexec - is a media archive
619M    2%    /var/log    # noexec - prevents code in log files
                          # (system has some servers.)

(Extra Storage Disk)
932G   64%    /basement   # noexec - is a media archive  

```

When I get my laptop, however, I will be formatting it differently, to maximize my use of the space.  I've decided if I feel like reformatting I can back up my /home folder.  I usually end up wiping it anyway so I can adjust the partition space.
```

33G - /
45M - /boot
300M - /var/log    - - (I've decided I like this.)

```

Note:  The MythTV log might be getting big because I haven't had time to read up and configure it.  It was spitting out large numbers of errors about not being configured.

---

### Post by capatt on 2008-07-21
What happens if you already have a SATA drive with 4 primary partitions?  I want to install an additional distro to an HD that looks like this:

C:\
--Primary Partition 1:  XP
--Primary Partition 2:  Ubuntu root
--Primary Partition 3:  Ubuntu swap
--Primary Partition 4:  Ubuntu home

I have plenty of unallocated space just sitting there, but I'm up against the 4 partition limit and I want to preserve my Ubuntu installation intact......

Thanks

---

### Post by anobomski on 2008-07-21
you could remove your swap to make space for an extended partition. you can then create a logical partition for swap and any othe OS you might want to install

---

### Post by capatt on 2008-07-22
My Ubuntu partitions are designated sda1 (XP), sda2 (Ubuntu root), sda3 (swap), sda4 (home), I think.  Anyway, swap is in the middle.  If I deleted swap, would home become sda3?  Would fstab need to be edited to reflect that change?

---

