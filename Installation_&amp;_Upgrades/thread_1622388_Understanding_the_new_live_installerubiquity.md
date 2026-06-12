---
title: "Understanding the new live installer/ubiquity"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2010-11-15
**[COLOR="Red"]NOTE[/COLOR]**: *[COLOR="Red"]This is NOT intended to be a complete or comprehensive installation guide![/COLOR]*

A new live installer (aka: ubiquity) was introduced in the Maverick release and there were quite a few changes so, whether you're an experienced user or a new user that might be looking at some older guide(s), I think it's worth having a look at just what to expect. 

Both Aysiu and &#65279;HowtoForge have assembled some very good screenshots describing an &#8220;Entire Disc&#8221; installation so I&#8217;m not going to reproduce everything they&#8217;ve done:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)

Softpedia also has a good guide here that shows a bit about creating partitions "on-the-fly":

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

But I'd like to point out some of the most prominent changes between this version of ubiquity and earlier versions.

#1: There is no longer an option to &#8220;Install in largest continuous free space&#8221;. There's a bug report filed regarding that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

#2: The option to choose where to install grub is now only available if you choose &#8220;Manual partitioning&#8221;, and there is no option to not install grub. AFAIK if you don&#8217;t want to install grub to the mbr of a drive you must now install grub to the pbr of the new "/" (aka: root) partition or the &#8220;/boot&#8221; partition if one is being created. More about using a separate &#8220;/boot&#8221; later.

#3: I personally find the &#8220;Install alongside other operating systems&#8221; option to offer some rather confusing options (more about that later), up to a total of eight decisions to be made:

Select drive
Allocate drive space by dragging divider
Offer to use advanced partitioning tool
Use entire partition
Use entire disc
Quit
Back
Install now

I have filed a bug report regarding that:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

And this bug may exacerbate the problem:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

#4: There is no longer a final screen where you can review changes before proceeding with the installation! (That&#8217;s where you used to change the bootloader install location). After you complete the user/computer name and password categories the installation begins!

NOTE: The user name must not include CAPS!


**************************************************


**Time out!**

Always follow basic pre-installation safeguards! Just a few that come to mind:

#1: Since it&#8217;s always a good idea to test the Live CD/USB anyway, by all means select &#8220;Try Ubuntu&#8221; instead of simply choosing to &#8220;Install&#8221;! Then while you&#8217;re trying out the Live Desktop lets find out how Ubuntu recognizes your existing drives, partitions, operating systems, etc. The most useful tool for doing this is Gparted which is installed in the Live Desktop by default, it&#8217;s found in System > Administration. You&#8217;ll notice in the upper right hand corner you can toggle between, and display, each recognized drive.

Since you&#8217;ll be installing with this Live CD/USB you need to understand Ubuntu&#8217;s device designations. For quite some time Ubuntu has used the &#8220;sd&#8221; designation regardless of hard drive architecture while others continued to use &#8220;hd&#8221;, but since you&#8217;re installing Ubuntu you&#8217;re only concerned with how Ubuntu recognizes your drives/discs & partitions! 

Basically device designations begin with &#8220;/dev/sd&#8221;, the first character following &#8220;sd&#8221; indicates the drive/disc number, and the second character following &#8220;sd&#8221; indicates the partition number. So /dev/sda = drive #1, /dev/sdb = drive #2, /dev/sdc = drive #3, etc. And /dev/sda1 = drive #1/partition #1, /dev/sda2 = drive #1/partition #2, /dev/sdb1 = drive #2/partition #1, /dev/sdc2 = drive #3/partition #2, etc.

NOTE: If any of that is unclear please post a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

And don&#8217;t just take the first advice offered. If we&#8217;re serious users we understand people are concerned about doing things right the first time. One saving grace of the new ubiquity is the option to QUIT until you&#8217;ve completed the username info!

#2: Once you feel comfortable about installing you should still back up anything important! Bad things can happen no matter how careful you are, like an unexpected power outage during repartitioning or resizing operations.

#3: Only resize Windows Vista or Windows 7 using their own partitioning tools, and only after defragging and cleaning up!

**************************************************

Now onto what the new ubiquity options look like, as previously mentioned there is no longer an option to install to largest free space. Depending on the existing configuration you&#8217;ll see up to three options:

Install alongside other operating systems
Erase and use the entire disc
Specify partitions manually (advanced)

As previously mentioned I've been discussing (and cussing) the "Install alongside other operating systems" option and you will find a brief summary here along with a screenshot:

[http://ubuntuforums.org/showpost.php?p=9986685&postcount=46](http://ubuntuforums.org/showpost.php?p=9986685&postcount=46)

I've literally installed Ubuntu hundreds of times as an iso-tester and I find that very confusing.

[B]In spite of my personal dislike for the new "Alongside" option in Maverick I decided to go somewhat more comprehensive in post #15:
[/B]
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

I hope that may save someone from data/OS loss.

And I assume that everyone knows if they choose the &#8220;Erase and use the entire disc&#8221; option it will do just that! It will erase everything on the chosen drive - period! And even if you have more than one drive are you sure you selected the proper drive? Also remember that you can no longer choose where to install grub unless you choose the manual partitioning option.

So I think everyone needs to understand the &#8220;Specify partitions manually (advanced)&#8221; option. And there is no real reason to be scared, I&#8217;ve long believed the safest and smartest process is to create the new partitions in advance somewhat as described here:

[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

But things look different so I created some screenshots. The first shows what you'll see after selecting &#8220;Specify partitions manually (advanced)&#8221;:

[ATTACH]175697[/ATTACH]

Basically you see (from top to bottom) a graphic displaying the current partition arrangement, the section listing all devices, and the section allowing you to change where grub will be installed. The graphic is just eye candy, do NOT rely on it for accuracy! Let&#8217;s concentrate on the section listing all devices for now.

Just below that you can see five options:

#1: New partition table - will only be available if you select a disc/drive, selecting this will erase everything on that drive!
#2: Add - should only be available if you select a device with free space available.
#3: Change - well, just what it says. This is usually the only option you'll use if you pre-created partitions as previously recommended.
#4: Delete - does what it says!
#5: Revert - should revert any change before it&#8217;s been applied if possible. Don&#8217;t count on it!

Since the Change option is what you'd likely be using you&#8217;ll see four options:

(1) New partition size
(2) Use as 
(3) Format the partition
(4) Mount point

[ATTACH]175698[/ATTACH]

I think (1) is fairly self explanatory. If you&#8217;ve created your partitions in advance as suggested you&#8217;ll be using the existing size. The &#8220;Use as&#8221; option allows you to choose the file system type. The current default is Ext4. At this time I&#8217;d say using either Ext3 or Ext4 is fine for your &#8220;/&#8221; (aka: root), and &#8220;/home&#8221; partitions. Of course SWAP will be used as swap area, but if you already assigned the SWAP using Gparted you&#8217;ll find that the installer will use any and all existing SWAP partitions. I multi-boot a lot and quite often have a SWAP on each of two or more drives, so if I don&#8217;t want the SWAP on a certain drive to be used with a new installation I simply choose the &#8220;do not use this partition&#8221; option.

[ATTACH]175699[/ATTACH]

I assume everyone knows that &#8220;Format&#8221; will erase everything on that specific partition! Commonly if you&#8217;re creating a new &#8220;/&#8221; and &#8220;/home&#8221; you will want to format the new partitions. However, if you&#8217;re using an existing &#8220;/home&#8221;, you would not want to format that &#8220;/home&#8221;! Doing so will erase all data in &#8220;/home"! There is no need to format a SWAP partition.

In the next screen you'll see the &#8220;Moint point&#8221; options displayed. Normally you&#8217;d only be concerned with &#8220;/&#8221; (aka:root) and &#8220;/home&#8221;. IMHO it&#8217;s seldom necessary to create a separate &#8220;/boot&#8221;, I&#8217;ve found doing so can create more problems than it solves. By default the automated installation creates only a &#8220;/&#8221; and a SWAP.

[ATTACH]175700[/ATTACH]

The next shot shows &#8220;Device for bootloader installation&#8221; options:

[ATTACH]175701[/ATTACH]

I'm aware that a lot of this may seem overwhelming and I will try to provide some partitioning examples in the near future.

---

### Post by kansasnoob on 2010-11-15
Well, this turned out fairly well after all :)

Should I remove that warning in red?

Should we ask the mods to sticky this?

I love criticism so let me have it.

---

### Post by cchhrriiss121212 on 2010-11-15
> I love criticism so let me have it. My suggestions:

Who is the target for this guide? I ask as the focus seems to be split between experienced users and brand new ones. Any new users will not need to know that the installer has changed and I imagine most old users will be happy to explore this themselves.

Some headings would be useful, the only one I see is called "Time out!" which is not particularly descriptive. Here is how I would lay it out with relevant headings for each section:

What has changed? - Your section describing the changes from the old installer
Preparation - Your tips on what to do before running the install
Installation
Further guides - You mention other guides right at the start, which is something best put at the end IMO.

You could also clean up a few things. As a general rule this would be removing any personal preferences (e.g. "I personally find the &#8220;Install alongside other operating systems&#8221; option to offer some rather confusing options"). Personal preferences are not bad, it is just that they do not offer anything helpful. It also does not fill the reader with confidence to know that the author is confused which you do mention on two occasions.

Layout consistency is also helpful for the reader. You use "#1" as a part of your headings *and* as a part of your text in the Time Out! section which should be avoided. And later on you switch to heading style to "(1)" but refer to it as "#1" still.

Other than that, a good guide!

---

### Post by kansasnoob on 2010-11-16
> Who is the target for this guide?

Both old and new users. Even the noobies will likely find outdated guides like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

But there is no longer an option to "install to largest continuous space".

> Some headings would be useful

I don't really intend that this be a full guide. I simply lack the skills and availability of web site to create an entire guide. That's also why I listed the other guides first. They show all screenshots up to what I've included here.

I also could not get the screenshots to "thumnail" as expected so I included a link to a post in my thread addressing the "side-by-side confusion":

[http://ubuntuforums.org/showpost.php?p=9986685&postcount=46](http://ubuntuforums.org/showpost.php?p=9986685&postcount=46)

Here's a typical screenshot of that:

[ATTACH]175751[/ATTACH]

I do find that very confusing :(

Why ask if a person wants to use entire partition or disc after they have already selected "install alongside".

That's exactly why I don't want to "fill the reader with confidence". From what I've seen, and I've had very little time to spend at the desk, the number of new users reporting that they've wiped out Windows has increased greatly :(

In order to publish a truly complete guide I'd need to include at least 14 screenshots and I couldn't get past 5 this time. I have in the past managed to post one actual screenshot and up to 5 thumbnails but this time I couldn't figure it out.

I'd love to collaborate with someone to create a more complete guide. I have a 3.9MB file of screenshots that I'd send anyone interested :)

---

### Post by dino99 on 2010-11-16
Some good improvments have been done, but its not enough, not for me as ive definively dropped that tool because i play with several hdds and a bunch of partitions, meaning that i never remember their typology. 
Thats why i use an external tool to prepare installation partition (partedmagic) and be able to "see" the whole hdds image.

 I still cant understand why ubiquity dev(s) dont use the image partitioner, which is less confuse than those too often meaningless dialog boxes. Well, seems the problem is that devs are devs not designers :(

---

### Post by Mark Phelps on 2010-11-16
I thought what you've done is quite good ...

That being said, I really think you need two guides:
1) For the new person coming over from MS Windows who wants to install dual-boot with Windows (probably Win7)
2) The experienced person who is interested in the details

I am ALARMED by the changes in the new installer that puts new folks in the position of accidentally wiping out their Win7 installs. Talk about creating a BAD first impression!  How much WORSE could it be than destroying someone's work simply because they wanted to try out something new?

The new user is going to need a very simple, step by step list of actions to perform, perhaps with screenshots as well.  You already have ALL of that, but you just need to trim it back for the new user.

Put basically, they don't care about WHY something needs to be done, they only care about HOW. And, they really do want a cookbook approach.

Also, as a FIRST step, since the practice of preinstalling Win7-loaded PCs (especially laptops) with 4 primary partitions is becoming more commonplace, I would suggest starting out with a detail example of how to use "sudo fdisk -lu" in the LiveCD mode to check the number of partitions in place.  If they have 4 already, it's going to be a LOT more work for them to preserve what they have while also installing Ubuntu.  So much work, that it probably merits a different guide -- one containing details about partitioning.

Not being negative -- think you've done a great job -- just providing some suggestions.

---

### Post by kansasnoob on 2010-11-16
> **dino99 said:**
> Some good improvments have been done, but its not enough, not for me as ive definively dropped that tool because i play with several hdds and a bunch of partitions, meaning that i never remember their typology. 
Thats why i use an external tool to prepare installation partition (partedmagic) and be able to "see" the whole hdds image.

 I still cant understand why ubiquity dev(s) dont use the image partitioner, which is less confuse than those too often meaningless dialog boxes. Well, seems the problem is that devs are devs not designers :(

I frequently end up using Gparted 0.4.6-1.iso which I know is getting a bit prehistoric but it always works :)

But when I perform iso-testing I always try to put my noob-shoes on and ask myself, if I'd never installed an OS before, would I understand this.

Well, I've installed Ubuntu literally hundreds of times. Partly because I've converted a lot of seniors from Win 98 and ME to some flavor of *buntu, but even more so performing iso-testing.

This spring and summer has just been bad for me. I've had almost no time to spend between the keyboard and the chair.

---

### Post by kansasnoob on 2010-11-16
> **Mark Phelps said:**
> I thought what you've done is quite good ...

That being said, I really think you need two guides:
1) For the new person coming over from MS Windows who wants to install dual-boot with Windows (probably Win7)
2) The experienced person who is interested in the details

I am ALARMED by the changes in the new installer that puts new folks in the position of accidentally wiping out their Win7 installs. Talk about creating a BAD first impression!  How much WORSE could it be than destroying someone's work simply because they wanted to try out something new?

The new user is going to need a very simple, step by step list of actions to perform, perhaps with screenshots as well.  You already have ALL of that, but you just need to trim it back for the new user.

Put basically, they don't care about WHY something needs to be done, they only care about HOW. And, they really do want a cookbook approach.

Also, as a FIRST step, since the practice of preinstalling Win7-loaded PCs (especially laptops) with 4 primary partitions is becoming more commonplace, I would suggest starting out with a detail example of how to use "sudo fdisk -lu" in the LiveCD mode to check the number of partitions in place.  If they have 4 already, it's going to be a LOT more work for them to preserve what they have while also installing Ubuntu.  So much work, that it probably merits a different guide -- one containing details about partitioning.

Not being negative -- think you've done a great job -- just providing some suggestions.

I couldn't agree more, especially with this:

> I am ALARMED by the changes in the new installer that puts new folks in the position of accidentally wiping out their Win7 installs.

If I were able to write a guide, errrrm maybe should say "guides", I guess I'd begin with the new "Install alongside other operating systems" option.

And I guess I'd say, "ignore the use entire disc/partition options, they may (or quite likely will) hose your existing OS and/or data partition!"

But enough about that for the moment, on to this:

> Also, as a FIRST step, since the practice of preinstalling Win7-loaded PCs (especially laptops) with 4 primary partitions is becoming more commonplace

That's why I put in the Time out! You'll notice after my brief explanation I include this:

> NOTE: If any of that is unclear please post a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

As I've said previously, I've had very little sit-down time in recent months and as time slips by I keep looking for someone else to jump in and create some kind of a guide.

So I tried to show a few of the pit-falls/differences. To my knowledge there is no actual 10.10 dual boot guide yet.

The guides I listed have very good screenshots, I provided a link to one of my previous posts about the "confusing side-by-side option" with a screenshot, and screenshots of each step if using the manual partitioning option.

Also a link to Herman's:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I really would love to collaborate with someone on creating a proper guide for 10.10. Right now I'm going to focus on trying to fix things in 11.04. I joined the proper group, now I need to put together a sensible argument :)

---

### Post by kansasnoob on 2010-11-18
I made a few minor tweaks.

I'm also going to take a few new screenshots and possibly try a slightly different approach.

I think I did a fairly good job of displaying what a person will see as they click thru the different manual partitioning steps so they'll at least know what to expect. That way they can hopefully plan in advance :)

I really do think Aysiu's guide is great:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

It shows choosing "try" rather than "install" so that's great. It doesn't show the "side-by-side" option but the Softpedia guide does.

I guess the biggest problem is explaining what to do with the "Use entire partition" and "Use entire disc" options if using the "side-by-side" option.

I say ignore them! If you've already chosen to "install alongside" an existing OS they don't belong there!

If you choose "Use entire disc" you'll wipe things out for sure, unless you've chosen to install to a different disc. Will a Windows user know how to select the proper disc/drive :confused:

The "Use entire partition" option is equally confusing. Which partition? Do you mean a new partition? I guess I want a new partition, or do I? Or do you mean wipe out the existing partition? **The latter is correct!** You'll lose your stuff :(

If you're a Windows user what is a disc and/or partition? If you have a floppy it's Drive A. Generally the main partition is Drive C, but what if you have Win 7? Are the extra "boot" partition and/or "utils" partition even recognized?

And even for those of us that do understand Ubuntu device designations there's this actual bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

That's why it's so hard to even think about writing an "alongside" guide. You're offered confusing options & there's also a bug!

---

### Post by dino99 on 2010-11-18
Thanks Erick for all the efforts and time you spend to make Ubuntu better, you rock :)

By the way im considering that its easier for a new comer to find a quick and simple howto with the main warnings about installing, than deeply explain everything and techy words and so on.

So the installer might load the image partitioner to let the user select where he want to install.

---

### Post by kansasnoob on 2010-11-18
> By the way im considering that its easier for a new comer to find a quick and simple howto with the main warnings about installing, than deeply explain everything and techy words and so on.


In a way that's what I'm trying to do here. I lack the skills and resources to create an actual web site or even a web page on someone else's site. So I rely on what others have done.

I've long thought that this is the ultimate dual/multi-boot guide:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

But it's not yet updated for the new ubiquity, and no other guide fully describes the changes in the new ubiquity.

I only hope to fill in the gaps within the limits of my capabilities. I'd very much like someone else to take up the mantle of fighting with the devs to correct this in Natty, but so far that's not happened.

---

### Post by kansasnoob on 2010-11-20
Thought I'd bump this just seeking more comments on improving it :)

Or exploring the possibility that someone else might take on the project :D

I've been trying to figure out how to change the title to something like "New live installer in Maverick".

I suffer from both a lack of skills and a lack of time :(

---

### Post by Herman on 2010-11-20
:) You did a great job with your installation how-to in post#1 there, kansasnoob!

I could really use some help if you and or some of the other fellows are interested.
I have a number of out of date Ubuntu installation guides that need updating and improving. I have always welcomed input from other Ubuntu Web Forums members.
I'm pretty sure we can work out ways to co-operate with each other for the benefit of Ubuntu and new users, and have some fun at the same time. :)

---

### Post by kansasnoob on 2010-11-21
> **Herman said:**
> :) You did a great job with your installation how-to in post#1 there, kansasnoob!

I could really use some help if you and or some of the other fellows are interested.
I have a number of out of date Ubuntu installation guides that need updating and improving. I have always welcomed input from other Ubuntu Web Forums members.
I'm pretty sure we can work out ways to co-operate with each other for the benefit of Ubuntu and new users, and have some fun at the same time. :)

That sounds awesome. I've always regarded your guides as the ultimate multi-booters bible (so to speak) :D

I ran through a couple more tests using the "Alongside" option and I still think that the "use entire disc and/or partition" options just don't belong there, but we'll have to see if I can get that changed in Natty.

As it is users need to know that selecting "entire disc" will wipe/erase the disc/drive indicated where it says "Select drive".

Likewise if the user selects "entire partition" it will wipe the selected partition, usually the largest existing partition! And sometimes the device designations are wrong :(

I just don't think potential data/OS-destroying options should even be available in the "alongside" option. It seems to me to be a recipe for disaster!

But I'd certainly help you in any way you wish.

---

### Post by kansasnoob on 2010-11-21
Despite my personal dislike for the &#8220;Install alongside other operating systems&#8221; option I decided that I should provide the best possible info so here we go.

I began with this partition scheme:

```
ubuntu@ubuntu:~$ sudo parted /dev/sdb print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1119MB  1119MB  primary  ntfs
 2      1119MB  74.5GB  73.4GB  primary  ntfs
 3      74.5GB  80.0GB  5519MB  primary  ntfs
```You'll see in this first screenshot the typical eight options described in my original post:

[ATTACH]176187[/ATTACH]

Note: I tried to hover the mouse pointer over the "drag" point to display the "slider" but didn't seem to be able to pull that off, regardless just trust me the pointer turns into a two-sided arrow that will allow you to "drag" the divider to change partition size.

Of course the eight options are:

Select drive
Allocate drive space by dragging divider
Offer to use advanced partitioning tool
Use entire partition
Use entire disc
Quit
Back
Install now

I believe the only two confusing options are "Use entire partition" and "Use entire disc".

But if you're really paying attention you'll notice that it shows it's going to resize /dev/sdb2 (ntfs) and create a new /dev/sdb3 (ext4). This is of course WRONG! Remember I already have an sdb3. That's this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

Read to the end and you'll see what the installer actually did.

But for now lets look at what happens if you choose "Use entire partition":

[ATTACH]176188[/ATTACH]

You can see that it shows it's going to use all of /dev/sdb as ext4, but it still shows two smaller partitions hidden, huh?????????

**[COLOR="Red"]Note:[/COLOR]** I've now filed a separate bug report regarding the "Use entire partition" option because it will in certain scenarios wipe the whole disc:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

Then it displays "Split Largest Partition". Now think about that. I've already selected "Install alongside other operating systems", then (among eight options) I selected "Use entire partition", and now it's asking me if I want to "Split Largest Partition". Not confusing at all, huh??????????

I get nearly the same thing if I select "Use entire disc":

[ATTACH]176189[/ATTACH]

You'll notice that the one major difference is that it shows "3 partitions will be deleted ........". That is accurate! It will wipe the drive! And once again it now offers "Split Largest Partition". No confusion there, huh??????????

As previously stated the one truly saving grace is that both "Back" and "Quit" work properly.

**[COLOR=Red]Trust me here![/COLOR]** If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! [COLOR=Red]**You will most likely lose the OS and any data contained therein!**[/COLOR]

And remember, you no longer get to review your selected changes once you've completed the username/password/computername info! You do however get this after you've completed your choices in the "Install alongside other operating systems" option:

[ATTACH]176190[/ATTACH]

So, be darn certain!!!!!!!!!!!!!!!!!!!!

What I did was use the "slider" and changed from the default 35.3GB /dev/sdb2 (ntfs) & 38.0GB /dev/sdb3 (ext4) to where the partition being created was 50GB and this is what I ended up with:

```
ubuntu@ubuntu:~$ sudo parted /dev/sdb print
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  1119MB  1119MB  primary   ntfs
 2      1119MB  24.5GB  23.4GB  primary   ntfs
 4      24.5GB  74.5GB  50.0GB  extended
 5      24.5GB  72.4GB  47.9GB  logical   ext4
 6      72.4GB  74.5GB  2092MB  logical   linux-swap(v1)
 3      74.5GB  80.0GB  5519MB  primary   ntfs
```Not bad, but I certainly did NOT use the "entire disc/partition" options.

Now I'm going to get some fresh air.

---

### Post by Herman on 2010-11-23
:) Well done and thanks for all your time and effort. It's nice to be able to communicate with someone who actually tries things out.

I'm starting to edit [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html") and I hope to be able to bring it up to date in the next few days.
For a start all I've done is delete a lot of words that aren't needed.

I'm trying to decide whether to bring it up to date with Ubuntu Lucid Lynx LTS or Maverick.
What do you guys think? 

Maintaining a website is fun but it does take up a lot of spare time.
One job is research and testing, finding out what the installer can do and what has changed since the previous installer. It looks like you have already done a pretty good job of that for Maverick, kansasnoob.

Another job is thinking of ideas about what kind of installation to show people. There are now a gazillion websites around on the internet about how to install Ubuntu. A standard installation is fine, but it's also nice if we can show people something the other websites don't cater for.

Thirdly there's work with image files, I use an emulator to get some of them, others and just screencaps and a few are made from scratch with GIMP. A lot of them need editing in GIMP.

The writing is another part of the fun of creating a good website, trying to think up the right words to explain clearly and concisely what the various available options will do and what results to expect from choosing each one.

Finally, there's proof reading and spell checking and there are hyperlinks to fiddle around with and keep up to date.

I use kompozer in Ubuntu to make my html pages, and it's just as easy to use as a word program. All we need to do is type what we want and insert images, it's simple to use and doesn't take much practice to get used to. 
There are always new tricks to learn with it though, so it's always quite interesting and enjoyable.

Keep an eye on [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html") and you guys can start helping me whenever you have time.

There are lots of way you can help.
First, we need to decide between Lucid or Maverick, Lucid is LTS, so it's more stable and better for new users, and we won't need to re-do our work for a long time.
If we chose Maverick we'll be more up to date, obviously, but it'll need updating a lot sooner, like when Natty Narwhal is released. :)

---

### Post by kansasnoob on 2010-11-24
Well, you have good ones using 10.04 here:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

and here:

[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

So IMHO I'd try to focus on 10.10.

I've been hammering the ubuntu-installer list in hopes of changing a few things in 11.04:

#1: I'd particularly like to see the "use entire partition/disc" options removed from the UI after choosing "Install alongside" option. IMO they only cause confusion.

#2: This actual bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I only recently discovered that choosing "Use entire partition" also appears to want to actually use the whole darn disc so when I iso-test Natty Alpha1 I need to update that bug report.

#3: Bring back the "Use largest continuous free space" option.

#4: Make the installer windows resizable/maximizable again. It makes complex partitioning schemes easier to read.

#5: Bring back the option to not install grub.

Of course #2 is a real bug so if I'm persistent I should be able to get it fixed. Or if they do #1 it wouldn't need to be fixed :D

No response yet from the ubuntu-installer team members so we shouldn't hold our breath.

Anyway, IMHO, I'd focus on 10.10. One of the things I love about your guides is being able to copy a link location to explain something to other users, like if I wanted to show someone what to expect when they click on "change" partition:

[http://members.iinet.net/~herman546/p28/025_ssd-done.png](http://members.iinet.net/~herman546/p28/025_ssd-done.png)

To me a picture truly is worth a thousand words.

---

### Post by Herman on 2010-11-24
:D Things were worse than this years ago with the first few Ubuntu released when they didn't yet have any 'Desktop Live/Install' CD. People had no choice but to install with the 'Alternate Installation' CD, but of course we didn't know any better in those days anyway.
The 'Alternate Installation' CD is really not all that hard to use, but you do need an installation guide if you're using it for the first time. Most people were overjoyed when the first 'Desktop' Live/Installation CD came out.

Dapper Drake was the first version of Ubuntu to have a Live CD, and it was nice and easy to use. It just had the same GParted in it as we find on the desktop if I remember correctly, so it was quite simple to use. 
Since then they've been making it fancier, slicker and faster, but it seems to be getting gradually more difficult for new users until it almost seems now like the 'Alternate Installation' CD might be the better alternative. 
The part that could possibly use some improvement is as you pointed out, the way the hard disk and partition information is displayed. 

There's a cool improvement I really like in the Maverick Meerkat Live CD. The newest GParted in Ubuntu now features an 'Align to:' spinbox instead of an 'Round to Cylinders' checkbox, which should be a nice improvement for SSD and other flash memory users.
I have started testing it but I haven't had time yet to play with it enough to say what it can and cannot do. More testing is required with that. If anyone wants to help they're welcome. 
So far I have tried it out for resizing an NTFS partition aligned to the old conventional 63 sector mark, and GParted did not move the start point of the partition when resizing while the 'Align to' spinbox was set to 'MiB', as I expected it to. It must be smarter than that I guess. 
I'm curious to find out under what circumstances it will move or not move a partition aligned to the 2048 mark, (Windows7, Vista), and partititons aligned to the 63 sector mark, (all other operating systems). It would be quicker and easier to just use an empty partition in a USB drive for example, for testing with. There's no need to use an entire operating system full of files just to find that out, and in fact it would be too slow to do it that way. Testing with a real operating system will come later. 
I'll have time this weekend to get some work done on this myself, and hope to be able to get some updates made to the website too. :)

---

### Post by Rubi1200 on 2010-11-24
Hi,
I would like to say, first of all, thanks to both kansasnoob and Herman for the fantastic work you both do on the forums and with the website.

I haven't really played around with the installer on Maverick as I only installed it to test other aspects of the latest version. Also, at least in my test environment, I was not faced with the kinds of issues kansasnoob has outlined (I do not use Windows, installed Maverick first, knew I was going to overwrite the bootloader later anyway etc.).

The problem, in my opinion, is one of perspective. If I look at the way Ubuntu has developed since version 6.06 (my first experience with Ubuntu specifically), I would have to say that the goal of the developers seems to be, in certain respects, to take as much thinking out of the equation as possible.

In other words, in an effort to make Ubuntu as easy as possible to install and use, with the least amount of hassle, and with the minimum potential for something going wrong, the developers have, in fact, made it, apparently, even more difficult for users.

How else to explain, what for me personally is inexplicable, the decision to remove the option to not install a bootloader?!?

On this point, I believe that the decision to not install a bootloader MUST rest in the user's hands, not those of the developers.

Why remove the option to install side-by-side if not for the fact that it appeared to cause Windows users to do something they really did not want to do (as evidenced by the number of posts on these forums at one point)? Yet, we are now seeing a slew of posts from users confused about the new options.

I fully support kansasnoob's efforts to affect some changes for the upcoming 11.04 and hope that users read this thread and bear these things in mind before installing (I have linked to this thread on at least a couple of occasions recently when a user was unsure how to proceed with the installation).

---

### Post by Herman on 2010-11-26
I tried a number of experiments with Maverick Meerakt's new GParted and I think the changes they made to GParted are a wonderful improvement.
Whenever we want to resize a partition now, there's no longer any need to remove the checkmark from the 'align to cylinders' checkbox, which was something that caused a lot of Windows users problems, especially Vista users.

This means the chances of a Windows user unintentionally 'moving' their entire partition and thus causing themselves problems with the Windows boot loader are now almost  negligible. The Windows boot loader is nowhere near as sophisticated as GRUB, and cannot understand its own file system, but relies on block addressing in the boot sector to find the next part of itself. When the partition is 'moved', Windows users needed the Windows Installation CD to repair (update) the boot sector to point to the next stage of the boot loader.

For speed, I experimented first with an empty 5GB NTFS partition, and moved it around and resized it quite a number of times. More testing would be nice if anyone wants to contribute.
In each case, the start sector for the NTFS partition remained at 2048 or whatever sector it was set in before resizing, except of course when I changed the 'Align to:' spinbox to 'cylinders'. Then I was able to successfully 'move' the start point of the partition to sector 63. 
I had no problems getting it to align to sector 2048 again when I selected 1 MiB again.
Just for fun I tried a few times to get it to move the partition to start at 4096, but instead it seemed to prefer to jump to 6144 for some strange reason. That's still on a MiB alignment, so I guess it's okay, it's not exactly what I wanted though.

I'm really pleased with this improvement in GParted. Whoever thought of that and implemented it deserves a good pat on the back! :)

---

### Post by kansasnoob on 2010-11-26
@ Herman,

I can't help much on the Windows front because the only Windows I have available is an old XP box.

When I do set up a dual boot with either Vista or Win7 I always just use their own partitioning tools.

My thought there is that Windows should never eat itself ;)

Even my old XP box is weird. I think only about 8GB is "used", but the way Win splatters data all over a disc, about 40GB is the smallest I can go with the Win partition.

I also tend to think that Vista and Win7 dual-booters should be warned or stopped by it's own partitioning tool if they're trying to do something wrong.

Anyway you know much more about using Gparted to resize Windows than I do.

---

### Post by Herman on 2010-11-26
> Even my old XP box is weird. I think only about 8GB is "used", but the  way Win splatters data all over a disc, about 40GB is the smallest I can  go with the Win partition.Windows XP is still a good operating system and does everything most  people want on way less hardware than Windows 7 and particularly Vista. :smile:

Possibly it's stopping at the 'immovable files'. That's represented by the big green bar you can see in the disk defragmenter. Try turning off your paging file and I'll bet those 'immovable files' will disappear! Then you should be able to defrag better and you'll be able to resize Windows as small as you want.  :smile:

To turn off the paging file, (equivalent to a swap area), you just go into 'Control Panel' -->'System' --> 'System Properties'-->'Advanced' tab -->'Performance, Settings button' --> 'Advanced' tab, 'Virtual Memory',-->'Change'.
[COLOR=#ff0000]Before you do anything, take note of your settings[/COLOR] (on a piece of paper) for later reference when you want to put things back the way they were again.
Then  click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.

Then restart your computer and now you can run defrag as many times as you need to, without the big green block in the way, and/or resize Windows a lot smaller than you were able to before.

For best performance please remember to go back into control panel and restore the original settings.

That information would only be relevant to people using Windows' own 'Disk Manager' to resize Windows. I have no objection to people using Windows own tools to resize Windows.  You need Windows own tools to run CHKDSK anyway, and besides, if  anything goes wrong at that stage of the proceedings it won't be seen as  Ubuntu's or GParted's fault.

GParted can resize Windows much faster regardless of the position of the 'immovable' paging file or the state of fragmentation.
I do recommend running CHKDSK /R before using GParted to resize any partition containing and NT File System though, possibly  several times until no more errors appear. CHKDSK /R is more thorough than CHKDSK /F and also, sometimes it takes several consecutive runs of it to fix all errors.

I prefer to use GParted for resizing Windows, and since we're going to be installing Ubuntu, Ubuntu's partitioner will eventually need to write to the partition table anyway. 

In order to be able to collaborate, we can 'agree to disagree', and say what I believe and what you and others think on this subject and let the users decide for themselves. :smile:

---

### Post by Herman on 2010-11-26
I have now had enough of testing GParted on a small empty NTFS partition, I was only doing that to find out what I wanted to know and save time.
Now I have Windows 7 installed and I'm practising installing Ubuntu and rebooting both OSes, then uninstalling and returning the computer to its 'original state' again.

In the past I have used virtual installations in VMware Player and screencaps from 'Applications'-->'Accessories'-->'Take Screenshot', but this time I'm experimenting with gtk [recordMyDesktop]("http://recordmydesktop.sourceforge.net/about.php") for keeping track of what I'm doing and a digital camera in video mode for other things like rebooting. I'm not sure how long it will take before I'll be able to update the website, but I want to let you know that I am busy working on it. :)

---

### Post by kansasnoob on 2010-11-27
> In order to be able to collaborate, we can 'agree to disagree'

That's absolutely correct!

For that matter my personal dislike of being presented the options to use entire disc/partition after having already chosen to install alongside is just that, "my personal dislike".

If the devs decide it's going to stay that way I'll accept that.

I hope you didn't think I was being critical of your procedure(s). I've long thought your guides were the best on the planet.

If someone asks 10 experienced Linux users how to create a dual/multi-boot setup they'll likely get 20 to 30 answers from just those 10 :D

---

### Post by kansasnoob on 2010-11-27
> **Herman said:**
> I have now had enough of testing GParted on a small empty NTFS partition, I was only doing that to find out what I wanted to know and save time.
Now I have Windows 7 installed and I'm practising installing Ubuntu and rebooting both OSes, then uninstalling and returning the computer to its 'original state' again.

In the past I have used virtual installations in VMware Player and screencaps from 'Applications'-->'Accessories'-->'Take Screenshot', but this time I'm experimenting with gtk [recordMyDesktop]("http://recordmydesktop.sourceforge.net/about.php") for keeping track of what I'm doing and a digital camera in video mode for other things like rebooting. I'm not sure how long it will take before I'll be able to update the website, but I want to let you know that I am busy working on it. :)

Don't rush. I posted a new comment here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

I need to repeat a test or two in Maverick. I'm sure one will require filing a new bug report.

I'm in hopes that I can get a solid answer regarding what they'll do with the "confusing options" soon.

---

### Post by tommcd on 2010-11-27
Ubiquity???
This is only one of many reasons why I always do clean installs from the alternate CD. 
I find those live CD "point & click" installers to be so very confusing. 
 I first started using Ubuntu back when 4.10 first came out. The only way to install Ubuntu back then was from a text based install CD, which was, and still is, very similar to Debian's install CD. This is what later became the alternate install CD when the live CD acquired the ability to also install Ubuntu. So I just choose to avoid the live CD altogether.
Problem solved!!!

---

### Post by kansasnoob on 2010-11-28
Should anyone think I'm slacking that's far from the truth:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

I'm working my silly butt off trying to figure out a new iso-testing scheme :)

Now, onto testing!

---

### Post by kansasnoob on 2010-11-28
> **tommcd said:**
> Ubiquity???
This is only one of many reasons why I always do clean installs from the alternate CD. 
I find those live CD "point & click" installers to be so very confusing. 
 I first started using Ubuntu back when 4.10 first came out. The only way to install Ubuntu back then was from a text based install CD, which was, and still is, very similar to Debian's install CD. This is what later became the alternate install CD when the live CD acquired the ability to also install Ubuntu. So I just choose to avoid the live CD altogether.
Problem solved!!!

I noticed Debian is updating the debian-installer, not for Squeeze but beyond, so it will be interesting to see what Ubuntu does :D

Nothing stands still!

BTW the debian-installer is the alternate install CD with a few minor tweaks.

---

### Post by Herman on 2010-12-01
This is just a progress report.
I have four web pages altogether on installing Ubuntu with the 'Desktop' installer.
Many of the images I need to use can be shared by all four pages.
That saves me some work and it also saves disk space in my account's portion in the iinet server, (my ISP hosts the website and I have a space allowance).

I'm working on all the images and I'm hoping to have all four pages ready to update simultaneously in a few more days, (possibly by Saturday Dec 4th I hope).

Each image has always had a number under it to identify it.
I'll need help with the captions under each image, if you care to take a look when the website gets updated. :)

[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")

[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

[http://members.iinet.net/~herman546/p28.html]("http://members.iinet.net/%7Eherman546/p28.html")

Some images won't have any caption in which case if you have time to write one I'll take a look at it and probably use it.
Researching and maybe testing to verify the validity of statements I make to make sure they're correct, thinking of clearer and more concise way to explain things and  spellchecking and spotting errors are all ways to help.

Some subjects we may need to talk about may be relevant to other Ubuntu Web Forum users.
For boring stuff that nobody else will be interested in just PM me instead.  :)

---

### Post by kansasnoob on 2010-12-02
I've been totally wrapped up in Natty iso-testing. We're on the third, and hopefully final, round now.

---

### Post by kansasnoob on 2010-12-02
I finally narrowed this down:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

> I did a bit more testing this AM since I'd finally gotten my mind around this a bit. I know some of my previous comments got a bit rambling so here's a recap:

This bug can be reproduced by creating either 2 or 3 primary partitions on a testing drive. No extended or logical partitions may be present on the drive.

I've tried this with empty NTFS partitions and a "manually installed" Ubuntu that uses only primary partitions.

Having chosen "Install alongside .........." the installer selects the largest partition as it should, but if you then select "Use entire partition" it actually uses the entire drive.

I must say though, I can't imagine any circumstance under which a person would want to select "Use entire partition" after selecting "Install alongside ..........". I suspect this is responsible for an uptick in reports of OS/data loss at the forums.

IMO the "Use entire partition" and "Use entire disc" options just don't belong there. In fact I believe they only present an opportunity for an inexperienced user to wipe out an existing OS and/or data.

The "Erase and use entire disc" option on the previous screen is more appropriately descriptive.

If I had my druthers I'd like to just see those options removed and have the "Use largest continuous free space" option restored to the prior screen.


I'm about bushed :P

---

### Post by Herman on 2010-12-03
So we have a language selection slider on the left-hand side of the very first screen that loads before the LiveCD even boots, beside the 'Try Ubuntu' or 'Install Ubuntu' decision.

Then we have a second language selection slider in the first screen we see when we start the installer.

It would almost be safe to assume that the first language selection is for the language the Live CD will be run in, and the one for the installer will be the language for the installation and the installed operating system. 

Can anyone confirm that for me? :D

Or does the installer remain in the language selected for the Live CD, but the *resulting installed operating system only* ends up in the language chosen at the start of installation?
(So someone who speaks only English can install an operating system for somebody who only speaks some other language).

---

### Post by kansasnoob on 2010-12-03
> **Herman said:**
> So we have a language selection slider on the left-hand side of the very first screen that loads before the LiveCD even boots, beside the 'Try Ubuntu' or 'Install Ubuntu' decision.

Then we have a second language selection slider in the first screen we see when we start the installer.

It would almost be safe to assume that the first language selection is for the language the Live CD will be run in, and the one for the installer will be the language for the installation and the installed operating system. 

Can anyone confirm that for me? :D

Or does the installer remain in the language selected for the Live CD, but the *resulting installed operating system only* ends up in the language chosen at the start of installation?
(So someone who speaks only English can install an operating system for somebody who only speaks some other language).

I hadn't thought of that but you're absolutely right. I only know English but I'll try an installation where I run the Live CD in English and when I get to the try or install part I'll select Spanish just for fun and see what happens.

---

### Post by kansasnoob on 2010-12-03
OK, I guess this is weird :)

Once you see the noninteractive boot screen you can press any key to display the normal options. BTW I tried to get that changed, if you're curious scroll down to "Rethink the noninteractive Live CD default boot" here:

[https://lists.launchpad.net/ayatana/thrd8.html](https://lists.launchpad.net/ayatana/thrd8.html)

Anyway that's your first option to select language. The next option to select language appears when you see this:

[ATTACH]177312[/ATTACH]

If you select "Install" that's the last time you'll see it, but if you select "Try ubuntu" you'll see it again if, or when, you click on the desktop icon.

Seems repetitious doesn't it?

Since Ayatana is difficult to search this was my original post regarding the noninteractive boot:

> I originally posted this as a question at Ayatana:

[https://answers.launchpad.net/ayatana-ubuntu/+question/110648](https://answers.launchpad.net/ayatana-ubuntu/+question/110648)

But thought I'd try this approach, please be kind.

As I found out iso-testing prior to Lucid Beta 1 the Live CD now requires user interaction to display menu options:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

At first this seemed fine but having used this more and more I find it to be only annoying. Consider the following:

1) It creates confusion for those who are new to Ubuntu. I've seen this a lot at the forums.

2) We've only moved the interactive part to a later point in the boot cycle because you still must choose whether to just "run" Ubuntu or install Ubuntu, so this really did not result in a faster boot.

3) With that "move" all we've done is "remove" the options to check CD for defects, adjust boot parameters, etc. without an otherwise unnecessary reboot which only results in frustration.

4) Even after learning of the new "boot behavior" the option to press any key passes so quickly that even an unplanned phone call or some other interruption can cause me to miss the opportunity, and increasing that "time out" would only increase the boot time.

I'm curious what others think about this. We could possibly plan changes for the first "point release" of Lucid and I'd think certainly for Maverick, and no time like the present ;^)


You'd think the installer or casper would remember the language instead of asking repeatably, eh?

---

### Post by Herman on 2010-12-03
:D Okay, thank you, kansasnoob, I guess it doesn't do any harm, but yes, it does seem a little bit repetitious.

---

### Post by Herman on 2010-12-03
I have uploaded the updated version of '[Ubuntu / Windows Dual Boot Installation 'A']("http://members.iinet.net.au/%7Eherman546/p24.html")', which is about how to install Ubuntu in a different hard disk than Windows or whatever other operating system is already there. 
It applies to installing Ubuntu in removable drives like USB and eSata as well as internal drives like SATA and IDE connected drives because it demonstrates how to install GRUB to the MBR in the same disk as Ubuntu is installed in.

Also newly uploaded to the iinet server is the updated version of '[Ubuntu / Windows Dual Boot Installation 'B']("http://members.iinet.net.au/%7Eherman546/p23.html")'. That one's about how to install Ubuntu in the same hard disk as Windows, using the Ubuntu installer's built-in partition editor.

I also uploaded the new version of '[Ubuntu / Windows Dual Boot Installation 'C']("http://members.iinet.net.au/%7Eherman546/p22.html")', and that one is the one that shows how to prepare the hard disk partitions ahead of time with GParted, (or some other partition editor if you prefer), and then install Ubuntu. 

All three of those are still under construction and will still need a lot of changes and corrections over the next few days or even weeks. 
All the images are in place, but there are a lot of images that don't have any captions to explain what they're about. 
I'm working on it and I'm open to suggestions if anyone want to discuss ideas with me or write some captions. :)

kansasnoob, I'll add your opinion about the 'Install Alongside' and 'Erase and Use Entire Disk' options and link to page1 of this post. I'll get around to that shortly as well as a few other changes. Thanks for your opinions so far, I agree with you that those options aren't very user friendly. :)
EDIT: Added.

---

### Post by kansasnoob on 2010-12-04
I guess I was kind of hoping you'd leave one based on 10.04. But honestly, since your focus is on manually creating partitions, it probably shouldn't matter.

I'm super cooked right now, after 3 days of iso-testing, and I get frustrated with arguments like I'm getting here:

[http://ubuntuforums.org/showthread.php?t=1595807&page=10](http://ubuntuforums.org/showthread.php?t=1595807&page=10)

Don't get me wrong, seeker5528 has helped me in the past, for instance understanding how dpkg remembers prior grub2 settings - thus causing a multi-booted Ubuntu to take over booting even if you didn't want it to :)

In this case offering the options to "use entire" are just wrong! If the devs end up saying it'll stay that way then I'll have to accept it, but I don't have to like it ;)

---

### Post by Herman on 2010-12-04
> I guess I was kind of hoping you'd leave one based on 10.04. But  honestly, since your focus is on manually creating partitions, it  probably shouldn't matter.I didn't get around to updating the netbook install to 10.10 yet like I said I was going to. Perhaps I should leave it for now and start taking a look at some of the 'Alternate Installation' CD pages?

I experimented with Windows Disk Manager for shrinking Windows 7 this morning and I wanted to find out if it's really true that it can only shrink Windows to half way due to the presence of the MFT in the middle or if it's because of the page file. I turned the page file off and it didn't make any difference, I could still only shrink it to half the size of the partition. That's interesting because I have already resized the same partition many times using GParted, and to a very small size too, so the MFT must have been moved during those times. Apparently GParted puts it back in the middle again when it gets resized larger. 

An inadequacy in all the web sites I've visited so far on using the Windows Disk Manager is they all neglect to explain how to turn off the page file if it's in the way, and if that happens the Windows Disk Manager wouldn't be much use at all unless the user knows how to turn it off or move it.
Windows help for the Disk Manager does explain a way to move the page file to a different partition temporarily. I added info about how to turn it off temporarily in Windows 7 right under the directions I already have for XP in my pre-install page under [Preparing For The Install]("http://members.iinet.net.au/%7Eherman546/p17.html#Preparation_For_The_Install_"), originally that was only there for advice on defragging. 
> Turn it off in 'Control Panel' -->'System and Security' --> 'System'-->'Advanced System Settings'-->'Advanced' tab, 'Performance'-->'Settings'-->'Advanced' tab, 'Change', [COLOR=#ff0000]take note of your settings[/COLOR] (on a piece of paper), remove the checkmark for 'automatically manage and click the radio button for 'no paging file' -->'Set', 'Apply', 'Okay'.It didn't seem to slow my Windows7 down at all when I turned off the page file, but I have 2 GB of RAM and I didn't have other programs open except paint now and again for saving the screencaps.  As expected I was easily able to use Disk Manager to resize Windows to half size while having the page file turned off.

EDIT: This link answers one ot two of my questions:[Working Around Windows Vista&#8217;s "Shrink Volume" Inadequacy Problems]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") - the how-to geek

EDIT: [Trouble Shooting Disk Management]("http://technet.microsoft.com/en-us/library/cc771775.aspx") - Microsoft
:shock: It appears that contrary to popular belief, a few things can go wrong when resizing your Windows 7 partition using Disk Manager after all. Especially if people try to use it in a computer with a few bad caps, a flaky power supply or a hard disk drive with a few bad sectors it's no safer than any other partition editor. This is the list of 'common issues', according to the heading. Luckily so far most Windows 7 and Vista computers are still fairly new eh?

---

### Post by kansasnoob on 2010-12-05
> I didn't get around to updating the netbook install to 10.10 yet like I said I was going to. Perhaps I should leave it for now

I think that would be a good idea. 10.04 will be supported for a very long time and I still hope to get some changes made before 11.04 is released. (I don't give up easy).

As far as the rest, if you feel it's safer and better to use Gparted I'm perfectly fine with that :)

---

### Post by Herman on 2010-12-06
> As far as the rest, if you feel it's safer and better to use Gparted I'm perfectly fine with that  No, it's not that it's necessarily safer or better to use GParted either.

I think it depends mainly how small the user wants to resize Windows and a little how much they prefer open source compared with proprietary software.
If someone likes Open Source and wants to shrink Windows to a size any smaller than half of its original size, (probably that kind of person will want to shrink Windows pretty small), then they should use GParted.
Someone who doesn't know anything about Open Source or what it's about and who is just trying Ubuntu for the first time, feels a little scared maybe and want to be conservative and only wants to shrink Windows a little is far better off sticking with Windows Disk Manager.
 
A point in favor of using Windows Disk Manager is it's 'the only one supported by Microsoft'. Nobody understand their proprietary file system as well as they do. They don't have to tell anyone else their secrets. and they can make changes too if they want to and they don't need to let anyone else know or give any warnings.

---

### Post by kansasnoob on 2010-12-06
Just looking through this one:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

It's my personal favorite :D

Consider this just thinking out loud, as I may be faced with many interruptions ;)

Since it deals with using Gparted I wonder if this should be adjusted slightly:

> 002
In this screen we're offered the chance to try Ubuntu out first by booting the rest of the way to the Ubuntu Live CD's 'Desktop' , or finish booting now and go right to the Ubuntu installer.
If you choose 'Install Ubuntu' and skip loading the Ubuntu Desktop, you'll save the extra minute or two it takes for the Desktop to load, and you'll have more RAM to spare during the installation too, which could be worth thinking about if you're computer is a little low on RAM. If is very low on RAM, consider using the Ubuntu 'Alternate Installation' CD instead. This website contains pages with examples about how to use the 'Alternate Installation' CD too.
I recommend choosing the second option, 'Try Ubuntu', unless you're really in a hurry. The advantage of loading the Desktop and trying Ubuntu out is you can make sure everything works okay with this version of Ubuntu and your hardware. 

Something about, "If you're going to use Gparted, as described here, you'll need to load the Live Desktop".

Then below "026" is a caption even needed? To me it seems self explanatory.

Below "027" I'm not sure what to say, if anything at all? The official Ubuntu install "guide" just says:

> We advise you to stay connected to the Internet so you can get the latest updates while you install Ubuntu. If you're having problems connecting to the Internet, use the menu in the top-right hand corner to select a network.

With some of my test installs I left both of those unchecked and I believe that I noticed the Partner repo was non-existent without selecting "Third party software". But I'm not certain!

What do you think?

Now, at "029" I had to back up a bit to where we create new partitions. Should we mention writing down or remembering device designations? In that case both /dev/sda1 and /dev/sda2 are Windows partitions. And /dev/sda5 will be "/", and sda6 will be SWAP.

I'm not sure where and when to mention that exactly, and I'm still pondering what other captions should be added during the making of the SWAP partition, if any.

Maybe at:

> 024
I had GParted create this Linux swap area for me, shown as a red rectangle in the above screencap.

And now I'm finished with the partitioning work, I can close GParted now.

Should a short bit be added about device desigantions? Then at "029" we could refer to something like, "remember you created sda5 for "/" and sda6 for SWAP". Certainly not those exact words, but I'm sure you get what I'm trying to say :)

Maybe at "029":

"Remember before closing Gparted you recorded the device designations for your new Ubuntu install and /dev/sda5 will be used for the root file system so highlight /dev/sda5 by clicking on it, then select change". Of course we need to be clear that their specific designations may vary from the example shown.

*I'm never sure exactly at what point to describe Ubuntu device designations, I seem to recall seeing a link in one of your other tutorials.*

At "029" we should probably also say something like, "after clicking on change you'll see a window open with the options:

(1) New partition size
(2) Use as
(3) Format the partition
(4) Mount point

since we just created the proper size partition no "size" change is needed."

Although I'm wondering if we should warn against clicking on any option other than "Change". Maybe refer back to post #1 in this thread?

Interruptions are eating my lunch now so I'll have to get back to this later, but so far my only real concerns are being certain the user understands device designations and describe the options available at "029". Then add/edit captions throughout "034", maybe mentioning that no further change is needed regarding SWAP.

What do you think?

Sorry to be so scatter brained.

---

### Post by kansasnoob on 2010-12-06
This is what I was thinking of:

> p24/029.png

We need to scroll up and down our list of disks and the partitions within them to find out where we want to install Ubuntu.

There's no such thing as a 'C: drive' in Linux, or any other drive letter, so just forget about it.
 If you're new from Windows, you'll soon see why the Linux way of numbering disks and partitions makes a lot more sense.

My first disk is called /dev/sda in Linux speak.
My second disk is called /dev/sdb.
My third disk will be called '/dev/sdc', and so on ...
The first part, '/dev/' stands for 'device', and the second part, 'sdb', means hard drive b.

It used to be 'hdb' in the old days, for 'hard drive b', but they changed the 'h' to an 's' for reasons that are outside the scope of this how-to.

The partition in my sdb disk is /dev/sdb1.
If I had more partitions they'd be numbered /dev/sdb2, /dev/sdb3, and so on ...
Only primary partitions can be numbered 1,2,3 or 4, and logical partitions are numbered from 5 upwards.
If you're not sure what I'm talking about here, don't worry about it too much, it won't be important for this particular how-to. If you're curious you may use this link, Help on Partitioning.

Be very careful here because the viewing area devoted to displaying the very important disk and partition has been reduced in size to make room for fancy graphics. You need to use the scroll bar carefully to scroll up and down the list of disks and partitions.

From:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Later :)

---

### Post by Herman on 2010-12-06
:) Thanks kansasnoob, I have  made some of those changes already but I ran out of time and will take another look at it later and will finish adding all those improvements.
You are now named as co-author near the top of the page to. Thanks again for your help. :)

---

### Post by kansasnoob on 2010-12-06
> **Herman said:**
> :) Thanks kansasnoob, I have  made some of those changes already but I ran out of time and will take another look at it later and will finish adding all those improvements.
You are now named as co-author near the top of the page to. Thanks again for your help. :)

Time is the major challenge :D

You do great work, I'm too pooped to make much sense of anything right now but I'll take a look again in the AM.

I appreciate the heck out of your efforts, you deserve an award from Ubuntu! Mark should take you along on his next space flight ;)

Honestly the three sites I most often link to are yours, Aysiu's psychocat, and SourceForge's perfect desktop series.

---

### Post by Herman on 2010-12-07
:D Well I owe Mr Shuttleworth and the developers and all of the other people who contribute to GNU/Linux and Ubuntu for providing me with such a great operating system. 
It started off as a wonderful hobby and now the things I have learned along the way have helped me to get promoted to a better job and earn a living in a more comfortable way.
There's no way I'd ever be able to pay back all the good I have been given, but maybe I can pass it on if my website helps people to get started with Ubuntu. :)

---

### Post by kansasnoob on 2010-12-10
Just wanted you to know I haven't jumped ship, just got super busy :)

I need to pick up some glass at the lumberyard today, and once it's installed I should be able to start looking things over again.

---

### Post by Herman on 2010-12-10
Okay. I still have some catching up to do anyway. :)

---

### Post by kansasnoob on 2010-12-12
Finally following up on:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Remember these are only suggestions :)

Please read this all before applying any changes, because I'm a pain where the sun never shines!

Below 026 do you even need a caption? Simply "select language"? I think it should be self explanatory.

**********************************

At 029 do you think it's worth mentioning the five options:

#1: New partition table - will only be available if you select a disc/drive, selecting this will erase everything on that drive!
#2: Add - should only be available if you select a device with free space available.
#3: Change - well, just what it says. This is usually the only option you'll use if you pre-created partitions as previously recommended.
#4: Delete - does what it says!
#5: Revert - should revert any change before it’s been applied if possible. Don’t count on it!

**I guess my biggest concern is someone highlighting a disc (eg: /dev/sda) and clicking on "New partition table".**

Then maybe just say something like, "Since, in this example, you've already created your partitions using Gparted the Change option is all you'll be using."

Then maybe, "After selecting the proper device (/dev/sda5 in this example) you’ll see the following four options:

(1) New partition size
(2) Use as
(3) Format the partition
(4) Mount point

Since we already set the new partition size using Gparted no change is needed there, the other three options are detailed below."

Note: I'm never sure how much info is adequate, too much can be a drag, but I prefer CYA ;)

********************************

A couple of nit-picky things:

Drop the highlighted "a" here:

> 031
Since we already formatted the partition earlier, it seems superflous to have it formatted a second time with the same file system. It's possible to have the installer go ahead with this checkbox clear, but **[COLOR="Red"]a[/COLOR]** there would be a warning message.

Add the highlighted ")" here:

> 032
This will be my main Ubuntu operating system partition, designated with a slash symbol in Linux, '/', (shorthand for 'root file system'**[COLOR="Red"])[/COLOR]**.

*********************************

After 033 maybe just say, "Now that I've completed those four fields I can just click OK."

And, either there or after 034, should you mention that no changes need be made regarding the pre-created SWAP? I think it's beyond the scope of that guide to explain that many Linux OS's can share the same SWAP, that all SWAP partitions will be used by default unless "Do not use this partition" is selected, etc.

What do you think? Maybe just:

> 034
Our partitioning scheme is all set up now. No changes need be made to the pre-created SWAP partition.

*************************************

Things get a little bit awkward at 035. Up through 034 sda5 was root and sda6 was SWAP, but in 035 and 036 they're different :(

And, while these two things are true:

> Another location for installing GRUB's boot.img which used to be popular was the partition boot sector of the Ubuntu partition. In this case that's /dev/sda6.  Although it can still be done if you insist, this prcatice is now discouraged. GRUB's core.img cannot be embedded when we install the boot.img to a partition boot sector, and although GRUB will still work with the copy of core.img in /boot/grub, (within the file system), it would need to rely on block addressing to locate that would make GRUB less reliable. 

> It's not possible to skip it and continue the without any boot loader at all.

I have found that installing grub2 to the newly created root partition (or "/boot" if one's being created) is perfectly OK if someone prefers using another bootloader, particularly if they want to use Easy BCD. I wish I could discuss that with Colin Watson.

For now I'd say leave that section alone and I'll try very hard to get some confirmation from the devs.

***********************************

Below 036 maybe say something like:

"This is your last viable option to quit or go back if you have any doubts, if you're sure ............. click on Install Now".

************************************

Are both 037 and 038 needed? If so just a simple caption like, "here you can see the file system being created".

***********************************

At 041 perhaps mention that the username must be only lower case. Of course by default it will be, but I've seen folks get stuck on that.

****************************************

The rest is pretty much self explanatory I think.

*******************************************
*******************************************

In retrospect, if you think 037 and 038 need not both be there, what about a screenshot like this:

[ATTACH]178239[/ATTACH]

between 029 and 030? That could work well with what I'd suggested adding to 029, maybe??????????

But I'm sure it's challenging to work on a website like that so please know that I'm not so much criticizing as trying to be helpful :D

ATM probably the most confusing thing to a noob would be where sda5 & sda6 change places in the screenshots/dialog.

Please don't shoot me.

---

### Post by ping-wu on 2010-12-12
> **kansasnoob said:**
> 

#3: Only resize Windows Vista or Windows 7 using their own partitioning tools, and only after defragging and cleaning up!



Is there any reason why we should only resize Windows 7 using their own partitioning tools?

I understand we should defrag before resizing, but the Windows tool retains too much disk space for Windows and not much for others if you only have a small disk (say 250 GB).

---

### Post by kansasnoob on 2010-12-12
Well, I posted this guery at the ubuntu-installer list:

> I've been collaborating with Herman from:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

to create some new installer instructions regarding the new ubiquity and I'd really appreciate some feedback regarding grub-install options.

While what he says there is correct, "Another location for installing GRUB's boot.img which used to be popular was the partition boot sector of the Ubuntu partition. In this case that's /dev/sda6.  Although it can still be done if you insist, this prcatice is now discouraged. GRUB's core.img cannot be embedded when we install the boot.img to a partition boot sector, and although GRUB will still work with the copy of core.img in /boot/grub, (within the file system), it would need to rely on block addressing to locate that would make GRUB less reliable.", I've personally found that installing grub to a new installations "/" (or "/ boot" if one's being created) is just fine if someone intends to use a different bootloader.

In fact I've done that a number of times without ill results, and I believe that's the proper procedure if one is going to use Esay BCD. Can Colin, or anyone, confirm this?

But I got this reply:

> Your mail to 'Ubuntu-installer' with the subject

    grub install options during installation

Is being held until the list moderator can review it for approval.

The reason it is being held:

    Post by non-member to a members-only list

I reviewed and my email address is still registered so I don't know what's up?

I'll grant you I've ruffled lots of feathers.

---

### Post by kansasnoob on 2010-12-12
> **ping-wu said:**
> Is there any reason why we should only resize Windows 7 using their own partitioning tools?

I understand we should defrag before resizing, but the Windows tool retains too much disk space for Windows and not much for others if you only have a small disk (say 250 GB).

I've seen many instances of people "moving" the beginning of a Windows partition using Gparted resulting in an unbootable Win :D

Herman and I discuss that in posts 20 thru 23.

---

### Post by Herman on 2010-12-12
> I've seen many instances of people "moving" the beginning of a Windows partition using Gparted resulting in an unbootable Win Yes, because the Windows boot loader isn't sophisticated enough to be able to understand its own file system. It uses the boot sector as a sort of 'stepping stone', and relies on storing the directions to the next part of itself as a sector number in the boot sector. ('Block Addressing').
So if the boot sector and the entire file system are moved without updating the boot sector's idea of where to find the boot loader files, naturally booting will be stopped at the boot sector.
It's easily fixed just by inserting the Windows installation disk and running 'startup repair', but sometimes it's also necessary to run bootrec /fixboot from a console as well.

Unfortunately for Windows users, a lot of computers now are sold without the Windows Installation CD, some only come with a 'recovery' CD, which is useless for any maintainance or repair work, (I guess they need to take their computer to a technician for every little hiccup). Others don't even come with a 'Recovery CD', but instead have various kinds of recovery partitions in the hard disk. I guess not supplying them is one way to try and reduce piracy as well as saving the cost of the disk. It's done at the expense of the user, the hard drive real estate they steal from the user would be worth far more then the cost of a CD or DVD. People still buy computers with Windows already installed anyway though. 

It's possible to get a Windows CD or an .iso for one if people try hard enough, all they need to do is look around, and they are needed for basic repairs and maintainance work. 

Avoiding moving the partition in the first place is even better.

Don't use very old versions of GParted (still shown in many GParted how-tos), to resize Windows Vista or Windows 7. They don't have the checkbox for 'align to cylinders', so will move the Windows partition to correct the cylinder alignment.

In other more recent, but nevertheless outdated old versions of GParted it was necessary to remove the checkmark from the 'round to cylinders' checkbox. and GParted would resize Windows Vista and Windows 7 partitions perfectly safely, with no boot loader problems. 
Unfortunately the reason for the checkmark was not well explained in GParted's GUI, and trying to spread the word about it proved too great a task for one person.

In modern, up to date versions of GParted I believe the problem is solved. Use Maverick Meerkat's GParted 0.6.2 or later so you'll have the MiB alignment spinbox set to MiB by default.
Please use an up to date version of GParted.

---

### Post by Herman on 2010-12-13
:D It will be interesting to see how you get along with trying to persuade the devs to allow the GNU/GRUB boot loader to be installed to a partition boot sector or not at all.

I think the question of where a new user is going to install GRUB as something of an initiation ritual. If they're brave enough and smart enough to install GRUB to MBR, preferably in the first hard disk they pass the test. 

That's because Ubuntu is free software and open source. The developers don't want to think it will be likely to be used as a mere accessory for Windows, Ubuntu is better than Windows and is designed to replace Windows. Therefore it's sensible to presume the user will want to install GRUB to MBR. That way when they delete Windows, Ubuntu will still be bootable, so it's more convenient. 

To help you understand their point of view more, you probably need to watch a few [Richard Stallman YouTubes]("http://www.google.com.au/search?q=Richard+Stallman&tbo=p&tbs=vid%3A1&source=vgc&hl=en&aq=f"). :)

---

### Post by Herman on 2010-12-13
:) I have made most of the changes you recommended in post #[**48**]("http://ubuntuforums.org/showpost.php?p=10229995&postcount=48"), kansasnoob, thanks for your continued help. I agree with most of your ideas. I didn't get it all completed yet because I spent too much time watching some of those Richard Stallman YouTubes myself, there are a few there I haven't seen before and one was quite long, but interesting. :)

I also checked   [Ubuntu Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html") over the weekend and that one didn't need much updating.

I have a couple of other 'Alternate Installation' CD pages that are badly out of date but I haven't decided what to do with them yet. It might be fun to try something a little different with the 'Alternate Installation' CD. We'll see. 

Regards, Herman :)
[]("http://ubuntuforums.org/showpost.php?p=10229995&postcount=48")

---

### Post by kansasnoob on 2010-12-13
> It will be interesting to see how you get along with trying to persuade the devs to allow the GNU/GRUB boot loader to be installed to a partition boot sector or not at all.

Well, AFAIK it is possible "to allow the GNU/GRUB boot loader to be installed to a partition boot sector".

I filed this bug report sometime ago:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

It resulted in grub2 only being installable to any mbr and the hosts pbr post-install, as an example if I run 'dpkg-reconfigure grub-pc':

[ATTACH]178349[/ATTACH]

And you can see I have lots of OS's on this box:

```
lance@lance-desktop:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for lance: 
Installation finished. No error reported.
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (squeeze/sid) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu 10.10 (10.10) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu natty (development branch) (11.04) on /dev/sda17
Found Ubuntu 9.10 (9.10) on /dev/sda2
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda3
done

```

So, I think it's pretty darn safe now to install grub2 to the newly created "/" or "/boot".

Why anyone would create a separate "/boot" is a whole different story. I guess right now it's sometimes needed with a btrfs file system, but btrfs is still experimental.

I'd just like some official confirmation beyond that. Although, Colin Watson made those changes and he is the lead dev assigned to grub I believe.

---

### Post by Herman on 2010-12-14
> Why anyone would create a separate "/boot" is a whole different story. I  guess right now it's sometimes needed with a btrfs file system, but  btrfs is still experimental. You need a separate /boot for a LUKS encrypted file system installation too, the kernel and the initrd.img are in /boot, and the initrd.img seems to be important for decrypting the file system it belongs to. 

A separate /boot partition was once an important feature for GNU/Linux operating systems back in the days when there were BIOS hard disk drive size limitations, like the 8GB limit. People who wanted to dual boot were able to install Windows inside the 8 GB limit and as long as they left room for a /boot partition for GNU/Linux, the rest of the Linux installation could be outside the 8 GB limit because the Linux kernel contained the drivers to address large hard disks. That way someone could have say a 20 GB hard disk and be able to use it all.

I agree with you, it's not as important now to have separate partitions for everything.
Imagine how great it must have seemed for a person to be able to fully utilize a hard disk greater than 8GB in size back then though?
I remember dual booting Windows 98 and Ubuntu Warty Warthog in a 6.0 GB HDD giving 50% to each OS, and I thought that was grand. (LOL). :)

(Well, it was a big step from using a calculator and pieces of paper anyway).

---

### Post by Herman on 2010-12-14
> Well, AFAIK it is possible "to allow the GNU/GRUB boot loader to be installed to a partition boot sector".

I filed this bug report sometime ago:

[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/576724]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724")Okay, I read all that.

How about writing a few letters to Bill gates too, and see if you can  persuade him and his cronies to make Microsoft products a little more  friendly to other OSes too then?
As far as I know no Microsoft operating system has ever come with any  options about where to install the boot loader at all, they just make  themselves right at home in whatever they think is the MBR in the first  hard drive thank you very much see you later. 
Too bad if you have a GNU/Linux MBR or any other.  :smile:

Okay, so dual booting is a dirty business, neither operating system is designed to be all that friendly to the other. 
Our role is to try to educate the users and try to help them pick their way through the minefields. 
I was particularly struck with what Fred Palmer had to say in post [#42]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/42") in your link there.
That's a good point, and the terms 'MBR' and 'boot sector' are often  used interchangeably too by some people, which adds to the problem.
Really, they do need to be following a good installation guide of some kind.

Alright then, I'll go as far as letting them know they can install GRUB to a partition boot sector for the purposes of using another GNU/Linux boot manager like [GAG Boot Manager]("http://gag.sourceforge.net/") for multibooting a number of GNU/Linux distros. :)

---

### Post by kansasnoob on 2010-12-15
I haven't tried GAG since Karmic. At that time it just wouldn't work with grub2. 

I fiddled with BURG a little bit and found it to be nothing more than an added level of trouble.

I personally think that grub2 is great! I think it should work well in all but a few corner situations where hardware may be an issue.

IMHO the least knowledgeable dual-booter should just let grub install to the MBR of the boot drive, unless they're installing Ubuntu to a USB drive (and even that is supposed to be fixed, but I've not been able to test it for lack of a spare USB hard drive).

But I have installed grub2 to the PBR (root partition) of installs when I want a previously installed grub2 to pick up the new installation.

I've also installed grub2 to the / partition and used EasyBCD to boot, though it must be a newer version of EasyBCD, so if someone was using EasyBCD in Vista to boot Hardy they might have to install a newer version of Easy BCD.

BTW I learned all about legacy grub from you site :D

Seriously! Without your site I'd still be scratching my head.

And I did know why a separate boot partition is sometimes needed (learned it from you) but I've seen people try to share a "/boot" a lot of times multi-booting and I always just shake my head ;)

I better follow up on prior posts and call it a day for now, darn getting old is rough. I get worn out way too fast.

---

### Post by candtalan on 2010-12-17
> **kansasnoob said:**
>  Likewise if the user selects "entire partition" it will wipe the selected partition, usually the largest existing partition! 

Err... That is what I thought when I tested it out. But disastrously it wipes the complete drive! Obviously a bug, I used more than one machine and also spent two whole days testing it out. It is a perfectly repeatable bug, it does not change for  different file systems or anything. It is fortunate that it is an option which most people are unlikely to use.
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106](https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106)

---

### Post by kansasnoob on 2010-12-18
> **candtalan said:**
> Err... That is what I thought when I tested it out. But disastrously it wipes the complete drive! Obviously a bug, I used more than one machine and also spent two whole days testing it out. It is a perfectly repeatable bug, it does not change for  different file systems or anything. It is fortunate that it is an option which most people are unlikely to use.
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106](https://bugs.launchpad.net/ubuntu-release-notes/+bug/659106)

Thank you. I added a message there and a note at my duplicate, which is now at least marked critical:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/682429)

> It turns out that this may be a duplicate of bug 659106 but in that case, from the info provided, it appears Paul began with an extended partition so that blows a hole in my theory about this only being reproducible with only primary partitions existing :^(

I'd still refer everyone to bug 655950 and also bug 652852. Also bug 657397 may be loosely related.

After following this dilemma off and on at the forums for several weeks I'm quite convinced that displaying the "Use entire partition" and "Use entire disc" options after having already rejected the option to "Erase and use entire disc", and having selected "Install alongside other OS" instead, serve no reasonable purpose and only provide an opportunity to destroy existing data and/or any existing OS's.

If the installer finds an acceptable partitioning arrangement (ie: three or less primary partitions) it displays the option to "install alongside" as it should, so under what circumstance would a person want to use and erase an existing partition? If they're performing a reinstall over existing partitions the "manual/advanced" option provides the proper tools to do so (including the ability to not format an existing /home).

And this is an area where we must all put our "noob shoes" on. Most Windows users don't know the difference between a disc and a partition so we're simply offering potentially destructive options. Sadly this has also effected some fairly long term Ubuntu users.

OTOH since both Vista and Win7 have their own partitioning tools the "Use largest continuous free space" option was truly brilliant and IMHO the safest possible dual-boot method for a first timer, aside from possibly Wubi.

Regardless I'm not going to mark anything as a duplicate ATM, I'll leave that decision up to the devs.


I sure wish we could get the mods to sticky this thread ;)

---

### Post by candtalan on 2010-12-19
Really good that the bug is now 'critical' well done. It is a disater. I am having to turn people away from an install because they have Vista and I know they could not cope with an advanced install. Dreadful situation.

---

### Post by candtalan on 2010-12-19
> **candtalan said:**
> Really good that the bug is now 'critical' well done. It is a disater. I am having to turn people away from an install because they have Vista and I know they could not cope with an advanced install. Dreadful situation.

It was suggested to me that a new iso for 10.10 could be created with minor changes to the installer gui to make it 'safe'
YES PLEASE

---

### Post by kansasnoob on 2010-12-23
Good news I hope, Colin Watson was assigned to this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

Colin's one of the best devs I've ever worked with so I have high hopes :D

---

### Post by kansasnoob on 2010-12-24
I've been fiddling around quite a bit and I swear the only time I can get the "Use entire partition" option to fail is if only primary partitions exist. However, that's disputed, and it would be reckless to suggest that either the "Use entire partition" or "Use entire disc" options are either safe or sane to use under any circumstances.

But I've been thinking about Rubi1200's offer to write the most simplistic installation guide possible. I've not gotten very far but I keep studying and learning :D

I'm up to this:

Step #1: Make sure you can run the Ubuntu Live CD/USB without problems - maybe we should add that even Wubi installs should follow that advice since it's hard to correct Wubi boot problems with no Live media.

Step #2: I've often been a stumble-bum regarding the "readability" of fdisk so I studied parted a bit further. Not hard at all, compare the outputs of 'fdisk -l' and 'parted -l' here:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00052a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          79      625664   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              79        1121     8372224   83  Linux
/dev/sdb3            1121        9730    69151744    5  Extended
/dev/sdb5            1121        9592    68045824   83  Linux
/dev/sdb6            9592        9730     1103872   82  Linux swap / Solaris
lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary   ext3            boot
 2      21.5GB  42.9GB  21.5GB  primary   ext3
 3      42.9GB  151GB   108GB   primary   ext3
 4      151GB   500GB   349GB   extended
14      151GB   172GB   21.1GB  logical   ext4
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext4
11      280GB   301GB   21.7GB  logical   ext3
10      301GB   323GB   21.8GB  logical   ext4
 5      323GB   378GB   55.1GB  logical   ext3
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  642MB   641MB   primary   ext3
 2      642MB   9215MB  8573MB  primary   ext3
 3      9215MB  80.0GB  70.8GB  extended
 5      9216MB  78.9GB  69.7GB  logical   ext3
 6      78.9GB  80.0GB  1130MB  logical   linux-swap(v1)

```

Cool, huh? The parted output is much more "human readable" and partitions are listed in their actual order. No "Partition table entries are not in disk order" warning :D

So what if we started with the DL, check md5sum, burn properly, check live media scenario and then "Try Ubuntu" followed by the output of "sudo parted -l"?

That should make it easy to see how many primary partitions exist, and if it's FOUR then the message is STOP! If it's three or less then look at the size of each partition, warn not to move the beginning (left side) of any Windows partition, etc, etc, etc.

More to follow, just sharing my random thoughts as insane as they might be :D

---

### Post by Rubi1200 on 2010-12-24
I like it!

As I was starting to review all the material I was actually wondering where does one begin?

The use of parted should be something we use as a troubleshooting tool in general, in my opinion.

I also looked at the output of sfdisk (which was used a lot by both meierfra and caljohnsmith in the early days), but I think for both new users and more experienced members, parted offers a simple yet understandable take on the situation.

I look forward to reading more of these "ramblings" as well as Herman's take on things.

---

### Post by kansasnoob on 2010-12-24
I'd guess that for over a year I've asked for the output of "fdisk -l" and then depending on that output I'd ask for the output of "parted /dev/sdX print".

I felt silly as hell when I found out I could have just been asking for "parted -l" all along :D

I do believe that fdisk has it's place, and it's great in the Boot Info Script but for super simple diagnostics parted is way easier. The one thing it won't show is how much of the space is used and how much is free.

---

### Post by kansasnoob on 2010-12-25
I did a bit more testing and I can only assure you all that the "Install alongside" is totally broken!!!!!!!!!!!!

The options to "use entire disc/partition" are definitely flawed but even if they're ignored things still go wrong!!!!!!!!!!!!!!!!

So, only two safe options exist in 10.10! Use entire disc is fine if you want a 100% Ubuntu puter, otherwise you must use the "manual/advanced" option. That's all there is to it!

---

### Post by Herman on 2010-12-25
I think using 'sudo parted -l' for a list of hard drives and their partitions is a great idea. :D

---

### Post by Herman on 2010-12-25
:D I just installed Ubuntu Dapper Drake from my collection of obsolete Ubuntu CDs, and I really think they had it right the first time. 

When I choose 'Manually edit partition table', The Dapper Drake installer's partitioner looks pretty near like GParted from the  'System', 'Administration', 'Gnome Partition Editor', but it's a little simpler, the 'Copy and Paste', and 'Apply' options are missing from the toolbar, but the 'New', 'Delete', 'Resize/Move' and 'Undo' options are all there.
Also I noticed the 'Information' line is greyed out in the installer-partitioner's right-click menu, even though it's active and works perfectly well in the standalone GParted in the same CD.
According the the 'Help', 'About' information, the standalone used in Dapper Drake was GParted 0.1.

The great thing about it is I can easily see a fairly accurate visual representation of what the situation is in any of my hard disks as far as partitions and file systems are concerned, which is exactly the kind of information a person about to begin a GNU/Linux installation would need to know.
I can 'see' which partition is called /dev/hda1 by Linux and which one is /dev/hda2 and so on, and I can also 'see' which partitions are primary, extended primary and which are logical partitions.
I can 'see' how much space is used or not used and therefore decide exactly how much I might want to shrink a partition containing some existing operating system.

The next screen after the partition editing screen in Dapper Drake is also very simply, practical and equally functionally elegant, with a list of hard disk partitions and their proposed mount points. I was even able to deselect the option of formatting the swap area, which is shared by other GNU/Linux installations and save myself the extra work of editing /etc/fstab with a new swap UUID in each of the other GNU/Linux installations in the same computer.

Interestingly too, the installer and partitioner even as old and out of date as Dapper Drake is now, did not 'move' the partition from the 2048 sector alignment, which was really good. Back then the 2048 sector alignment idea would have been way too far in the future for anyone to have anticipated.

Any reasonably intelligent person had a fair chance of being able to make informed decisions using the Dapper Drake 'Desktop' Live CD's installer.

If there's any way you can find and download a Desktop Live/Install .iso for Dapper Drake you should take a look at it and try it out, I think you'll agree it's installer was way better than the installers we're using now. :D

EDIT: There wasn't any choice about where to install the boot loader that I can see in the Ubuntu Dapper Drake 'Desktop' installer, we needed to use the 'Alternate' CD instead I guess, if we wanted that kind of flexibility in those days.

If there was a new new Ubuntu installer made with which combined the best features and abilities of the modern ones with the ease of use and simplicity of the original 'Dapper Drake' Live CD installer, I think a lot  there would be fewer installation problems reported in the forums and more people would feel safe to install Ubuntu. :)

---

### Post by kansasnoob on 2010-12-26
Just reviewing the "use Gparted guide" that I'm linked to in my OP and, since my mind is weak, I'll list problems in the order that I see them:

Simple misspelling here:

> 041
Your name as you type it here will be used by programs such as email, so make sure you don't type anything funny here in case you forget and send an email to somebody you need to impress such as a potential **[COLOR="Red"]emplyer[/COLOR]** or someone like that.

Obviously you meant employer ;)

IMHO that's it :D

I think the screenshots that lack any caption don't really need one, but that's just my opinion.

I've been beating my old brains out trying to find a super simple option for installing Maverick that requires no knowledge of device designations, partitioning, etc, but I just can't do it :mad:

IMO the only safe way to install Maverick in a dual-boot (or muti-boot) is by using the manual partitioning option.

Using the "install alongside" option is simply a crap-shoot ATM! I've tried really hard to find a reliable work-around and I'm convinced there simply isn't one.

Reading through the aforementioned guide I just don't see anything we could get rid of and still serve the intended purpose, but I do recognize the need for a very simple dual-boot procedure like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

While the grub directions were outdated that was still easy, but the devs killed that option!

And Wubi has become a total joke! The first update is guaranteed to leave you an unbootable system, quite often with no media to restore a Windows MBR  :o

Regardless I'll soon look at this:

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

Then I'll pick any nits I see :D

Right now I'm going to try adding a post to Ubuntu bug #1. For some reason I've not been able to for the past few days. SABDFL needs to know that recent changes are resulting in very bad first impressions of Ubuntu, and that makes me sad.

---

### Post by kansasnoob on 2010-12-26
> **Herman said:**
> :D I just installed Ubuntu Dapper Drake from my collection of obsolete Ubuntu CDs, and I really think they had it right the first time. 

When I choose 'Manually edit partition table', The Dapper Drake installer's partitioner looks pretty near like GParted from the  'System', 'Administration', 'Gnome Partition Editor', but it's a little simpler, the 'Copy and Paste', and 'Apply' options are missing from the toolbar, but the 'New', 'Delete', 'Resize/Move' and 'Undo' options are all there.
Also I noticed the 'Information' line is greyed out in the installer-partitioner's right-click menu, even though it's active and works perfectly well in the standalone GParted in the same CD.
According the the 'Help', 'About' information, the standalone used in Dapper Drake was GParted 0.1.

The great thing about it is I can easily see a fairly accurate visual representation of what the situation is in any of my hard disks as far as partitions and file systems are concerned, which is exactly the kind of information a person about to begin a GNU/Linux installation would need to know.
I can 'see' which partition is called /dev/hda1 by Linux and which one is /dev/hda2 and so on, and I can also 'see' which partitions are primary, extended primary and which are logical partitions.
I can 'see' how much space is used or not used and therefore decide exactly how much I might want to shrink a partition containing some existing operating system.

The next screen after the partition editing screen in Dapper Drake is also very simply, practical and equally functionally elegant, with a list of hard disk partitions and their proposed mount points. I was even able to deselect the option of formatting the swap area, which is shared by other GNU/Linux installations and save myself the extra work of editing /etc/fstab with a new swap UUID in each of the other GNU/Linux installations in the same computer.

Interestingly too, the installer and partitioner even as old and out of date as Dapper Drake is now, did not 'move' the partition from the 2048 sector alignment, which was really good. Back then the 2048 sector alignment idea would have been way too far in the future for anyone to have anticipated.

Any reasonably intelligent person had a fair chance of being able to make informed decisions using the Dapper Drake 'Desktop' Live CD's installer.

If there's any way you can find and download a Desktop Live/Install .iso for Dapper Drake you should take a look at it and try it out, I think you'll agree it's installer was way better than the installers we're using now. :D

EDIT: There wasn't any choice about where to install the boot loader that I can see in the Ubuntu Dapper Drake 'Desktop' installer, we needed to use the 'Alternate' CD instead I guess, if we wanted that kind of flexibility in those days.

If there was a new new Ubuntu installer made with which combined the best features and abilities of the modern ones with the ease of use and simplicity of the original 'Dapper Drake' Live CD installer, I think a lot  there would be fewer installation problems reported in the forums and more people would feel safe to install Ubuntu. :)

I remember trying Dapper (Kubuntu I think) but it wouldn't work with my graphics chip. I really fell in love with Gutsy, installation was a piece of cake. I think they began to introduce that silly colored graphic showing the partitions in either Hardy or Intrepid, but the screen could still be maximized so it didn't harm anything.

ATM they've hosed a lot of really good stuff and only increased the risk of data loss. That's sad as heck!

---

### Post by candtalan on 2010-12-27
IMHO the dumbing down of the installer (even if it worked perfectly as originally hoped) is a mistaken direction. The one thing about Ubuntu is that it is not usually pre installed for users, they have to install it themselves. 

Any one who is prepared to take on that task is capable of making decisions from simple graphical displays, and hopefully the default suggestion would be viable anyway.

People who are so non technical that they do not want to do (or see) anything but click the 'Yes' option are not at all likely to be installing Ubuntu by themselves.

The 10.10 installer removes GUI  information which would be useful to the normal Windows user DIY techie and Ubuntu wannabe and forces them to use the Advanced option. I am installing all the time, as an experienced non expert, and even *I* have been reluctant to use the Advanced option for years!

It is a high probability that such Windows users will happily be able to delete a partition of their choice, I have seen this on many occasions. If they then can use the legacy type of option 'guided install into largest unused area on drive' then - job done. Ubuntu installed, dual boot. And we then have a new user in a wider Windows user family group who will soon be converts.

10.10 even when working ok, is an installer too far, and alienates the adventurous, but nervous, Windows users who would otherwise be a spearhead of our near future new userbase.

---

### Post by Herman on 2010-12-28
:D Well maybe some people just shouldn't be allowed to install Ubuntu.
Maybe there should be a competency test before the installer will start and if a person can't pass the test they can't start the installer. It would be kind of like getting a suspected intoxicated car driver to walk a straight line, except since this is in a computer they would be asked a few simple questions. 
If they can't answer the simple questions correctly they should be directed to s site where they can find out some of the basics and then come back and try again. :)

---

### Post by Herman on 2010-12-28
'Dumbing Down' isn't exactly the same thing as enlarging the display of partitions and disks to a normal size and displaying how much room is used and unused in file systems though so people can actually 'see' what they're doing and make properly informed decisions based on a decent graphical representation of their existing partition situation. :)

---

### Post by Rubi1200 on 2010-12-28
> Maybe there should be a competency test before the installer will start  and if a person can't pass the test they can't start the installer.
That is actually not such a bad idea!

I cannot tell you how it pains me to read posts from people who thought "it would be so easy and now my Windows install is gone."

Users really ought to read **first** before jumping in to something without knowing the potential risks.

---

### Post by candtalan on 2010-12-28
I think that the suggestions similar to competency testing before installing Ubuntu is a very damaging suggestion, even if (as I hope) it was intended in jest.

It is not easily consistent with the Ubuntu code of conduct, it is certainly not 'inclusive'.

It would be more constructive to work towards a safe process, one that was safe even for beginners. I believe this was the aim, from what I can see of it, of the installer in 10.10.
For example, when more than one partition is available, with the 'Side by Side' option, the user does NOT get to choose which partition is to be offered for resize, the installer software decides. And no other partition is offered.
This is what I meant by 'dumbing down'. This approach has much merit, it is certainly inclusive of competence or the lack of such.

Unfortunately, (and serious bugs aside), the 10.10 installer omits what I would suggest is the most frequently used option by Windows users experienced at home Windows DIY use  - the mid competence DIY options of full visibility GUI and the *wonderful* 'install into largest unused space'.

---

### Post by candtalan on 2010-12-28
> **Rubi1200 said:**
>  Users really ought to read **first** before jumping in to something without knowing the potential risks.

Users *ought* to do lots of things! But I am dreaming of a different world to this one.

A true short story:
I accepted an old PC for re use or disposal from an acquaintance, who brought it to my house. I talked about how I only used Ubuntu and how well it ran etc. The PC was going to have Ubuntu installed of course.

He expressed interest. I gave him a Live CD and some printed information for background. I invited and urged him to phone me before he did anything, I would happily talk him through the process.

I heard nothing. A couple of days later he phoned for help, having apparently lost his Windows.

I was shocked, but the issue was to assist now. As it happened, it was possible to sort out the problem ok by phone discussions and belated detailed help, but it took some time. I do not recall exact details I guess it was grub or similar.

Comment:
What I realised then and also on other occasions, is that apparently, many DIY Windows users have a strong tendency to try stuff alone, so to speak 'in secret'. I do not think it is their fault, it is just that a domestic Windows user is in an environment which encourages secrecy.

The Ubuntu like (free software related) culture of a strong trusted and helpful community is difficult to find in a Windows world. Such Windows users join local clubs, and use face to face contact. Online information does certainly exist but as a long time Windows user I found it was difficult to know what to trust, there is a lot of gotchas out there for Windows users, particularly home DIY level users.

The main culture shock for me when I keenly began using GNU/Linux was the effect of Community. A very non technical issue in a rather technical environment. And it was Community and how it was  managed with Ubuntu that decided me to choose Ubuntu warts and all, over other distros. 

When a long time Windows user starts to 'sensibly' use forums such as this, then I know we have a convert, however long they continue to use Windows.

---

### Post by kansasnoob on 2010-12-28
> Users *ought* to do lots of things! But I am dreaming of a different world to this one.


I think we live in the same world ;)

The addition of the "use entire disc/partition" options after choosing to "install alongside" are just wrong-minded! I did try to point that out:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

That was very close to the release date because I'd been sidelined from testing (other than using a VM) due to an unrelated bug in X.

But I certainly am aware of what a nightmare this is. ATM Wubi installs are almost sure to break on the first update, and quite often with no live media to restore their Win mbr :(

Now we've not only removed the simplest option to install (use largest free space), but we've introduced options into the "alongside" option that serve no purpose but to potentially destroy any existing data/OS and Ubuntu's reputation :eek:

Not good, I've tried to post this info at Ubuntu bug #1 several times but I can't :o

---

### Post by Rubi1200 on 2010-12-28
Dear candtalan,
I respect your experience and opinions. I have followed and learned much from your posts in the time I have been a member of these forums.

I think (assume) Herman was joking, as I was too.

But, all jokes aside, kansasnoob makes some valid points here. Namely, there is something seriously wrong with the current installer. 

I also believe that if someone wants to even consider a dual-boot with another operating system that it is incumbent upon that person to do their homework first.

In my opinion, that means finding and reading information, asking questions here or on other forums, and generally informing oneself about what one is about to do BEFORE blindly choosing options without understanding the consequences.

On the other hand, I personally think the developers made a mistake with this installer.

If they were hoping that this would encourage users to join the ranks of other happy dual-booting Windows/Ubuntu users, then I think they seriously miscalculated.

Don't get me wrong, I am all for the approach you espouse; it is this Community that has "made" Ubuntu the experience it has been for me too.

We all need to keep our eyes open and try and help other users as best we can to avoid the pitfalls of the current installer.

---

### Post by candtalan on 2010-12-28
> **kansasnoob said:**
> ATM Wubi installs are almost sure to break on the first update, and quite often with no live media to restore their Win mbr :(


You bet. I am just helping the ONLY person on the AgeUK forums who tried Ubuntu as a novice, helping him to unistall Ubuntu because it failed just after an update. Rats!

for interest:
[http://discuss.ageconcern.org.uk/messageview.cfm?catid=10&threadid=51&STARTPAGE=1](http://discuss.ageconcern.org.uk/messageview.cfm?catid=10&threadid=51&STARTPAGE=1)

---

### Post by Rubi1200 on 2010-12-28
> **candtalan said:**
> You bet. I am just helping the ONLY person on the AgeUK forums who tried Ubuntu as a novice, helping him to unistall Ubuntu because it failed just after an update. Rats!

for interest:
[http://discuss.ageconcern.org.uk/messageview.cfm?catid=10&threadid=51&STARTPAGE=1](http://discuss.ageconcern.org.uk/messageview.cfm?catid=10&threadid=51&STARTPAGE=1)
candtalan,
there is now a [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") that deals with these issues.

The fact that GRUB updates are breaking Wubi installs is another issue. I know that bcbc, amongst others, is trying to get this changed.

---

### Post by kansasnoob on 2010-12-29
Some of the things I find interesting are well displayed in this thread:

[http://ubuntuforums.org/showthread.php?p=10292283#post10292283](http://ubuntuforums.org/showthread.php?p=10292283#post10292283)

They're still confused even after looking at this thread and Herman's thread:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Now, this is where I applaud Rubi1200 for stepping forward trying to find a better way to explain things :)

Maybe Herman and I are so much on the same "wave-length" in understanding/explaining things that we can't see what's confusing to others in those instructions.

I've really looked hard at Herman's instructions and I think things look pretty darn good. I do know that Herman is open to suggestions and I certainly am.

---

### Post by irockonguitar on 2010-12-30
hey guys,

I did my best to follow the advice here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

and installed ubuntu on the entirety of my second hard drive (D in windows-speak, sdb in ubuntu-speak). It seemed to work, and took me through the whole process of creating my username and determining my keyboard layout, etc etc, and then it said that I needed to reboot in order to finish installation. When I clicked on the "reboot now" button, it ejected the live CD and shut down. Then when I tried to reboot into ubuntu, it gave an error saying that it could not find a medium with live file system (the live CD, is what I took from the message). So I popped the live CD in again and it booted into that. 

Why didn't it actually install ubuntu on sdb? Windows still seems to be intact on sda (or C, in its own words).

EDIT: when it gets to the part where it tells me it can't find the live cd, it also says "Enter 'help' for a list of built-in commands" and sits there waiting for me to give it a command. Is there something I'm supposed to do at this step that I'm missing?

---

### Post by Herman on 2010-12-30
:) Hello irockonguitar,
> could not find a medium with live file systemI think  that's an error message from GRUB, so it could be that your GRUB is  misconfigured or your file system has something wrong with it.

I would try booting with the Ubuntu Live CD and mounting the file system of the new installation first to see if it looks okay.

Probably if you can mount it the file system is okay, but if you can't find it in your 'Places' Menu, it might just need a file system check. You can use GParted for that. 

Then I would try booting it again and if it still doesn't boot I would try booting up from a different GRUB such as from a GRUB CD or Super Grub Disk, which can also be found in Parted Magic Live CD. 
You can usually boot Ubuntu if it's bootable or at least get an error message telling you why not by booting with GRUB in CLI mode. [GRUB How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")
That would help if the problem has anything to do with a misconfigured GRUB.

If it boots up without any problem from some other GRUB, just try getting updates and likely that will fix it without the need for you to do anything much.

If nothing works, since it's a new installation and you won't have any personal files in there yet, sometimes it's quicker just to try again and re-install and hope for better luck the second time. Ubuntu crams a lot of files into the Live CD, so sometimes it doesn't take much to have IO errors while copying them to the hard disk during an installation, and also there are some files that will be downloaded from the internet during the installation process. I'm not sure if those can be corrupted in any way. I do know that I can run the installation in the same machine and not get the same installation every time, it could be because I use older hardware for some of my testing too. Sometimes just trying again results in a better installation.

---

### Post by Rubi1200 on 2010-12-30
Hi kansasnoob,

Based on how things stand with your testing and the increase in the number of posts on the forums from users who seem to be confused by the options, perhaps we should concentrate on the manual partitioning aspect and tell users to steer clear of the other options (unless they want either a messed up system or really want only Ubuntu on the drive)?

If we put something together based on manual partitioning only will users go for it if we explain the dangers of the other options as things currently stand or will this put people off entirely?

---

### Post by irockonguitar on 2010-12-30
> **Herman said:**
> :) Hello irockonguitar,
I think  that's an error message from GRUB, so it could be that your GRUB is  misconfigured or your file system has something wrong with it.

I would try booting with the Ubuntu Live CD and mounting the file system of the new installation first to see if it looks okay.

Probably if you can mount it the file system is okay, but if you can't find it in your 'Places' Menu, it might just need a file system check. You can use GParted for that. 

Then I would try booting it again and if it still doesn't boot I would try booting up from a different GRUB such as from a GRUB CD or Super Grub Disk, which can also be found in Parted Magic Live CD. 
You can usually boot Ubuntu if it's bootable or at least get an error message telling you why not by booting with GRUB in CLI mode. [GRUB How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")
That would help if the problem has anything to do with a misconfigured GRUB.

If it boots up without any problem from some other GRUB, just try getting updates and likely that will fix it without the need for you to do anything much.

If nothing works, since it's a new installation and you won't have any personal files in there yet, sometimes it's quicker just to try again and re-install and hope for better luck the second time. Ubuntu crams a lot of files into the Live CD, so sometimes it doesn't take much to have IO errors while copying them to the hard disk during an installation, and also there are some files that will be downloaded from the internet during the installation process. I'm not sure if those can be corrupted in any way. I do know that I can run the installation in the same machine and not get the same installation every time, it could be because I use older hardware for some of my testing too. Sometimes just trying again results in a better installation.


Thanks,

I actually tried re-installing first, and that didn't work. So I checked the file system and it appears ok. I then followed the advice in your link and booted using a Parted Magic Live CD. I am in the process of downloading updates right now, but I don't see any in the list that pertain to Grub. Then again, if it doesn't say "grub" in the title, I wouldn't know what it was. 

I noticed though, that when I did:

```
search -f /vmlinuz

search -f /sbin/init
```

that both returned

```
hd1,msdos1
```

I'm not experienced enough to know what that really means, but the fact that msdos is involved suggests to me that something ended up on sda, the hard drive with Windows, when it was supposed to end up on sdb, where I put Ubuntu. Is that right? Can I do anything about it? Does it matter? Will getting all the updates solve it?

---

### Post by irockonguitar on 2010-12-30
Ok, apparently installing updates does not solve the problem. :(  What can I do now?


Also, just another observation, when I try to boot into Ubuntu, prior to it giving me the error about being unable to find a live medium, it also always gives this warning: 

(process:415): GLib-WARNING **: getpwid_r(): failed due to unknown user id (0)

Does that mean anything I should be concerned about?


EDIT: I just posted this in a new thread, to see if anyone else has advice, and also to make it easier to search for other people having the same problem.  New thread: [http://ubuntuforums.org/showthread.php?t=1656476](http://ubuntuforums.org/showthread.php?t=1656476)

---

### Post by kansasnoob on 2010-12-31
> **Rubi1200 said:**
> Hi kansasnoob,

Based on how things stand with your testing and the increase in the number of posts on the forums from users who seem to be confused by the options, perhaps we should concentrate on the manual partitioning aspect and tell users to steer clear of the other options (unless they want either a messed up system or really want only Ubuntu on the drive)?

**If we put something together based on manual partitioning only will users go for it if we explain the dangers of the other options as things currently stand or will this put people off entirely?**

I don't know.

Regarding the concept of keeping things simple I almost wonder if that's possible. Look at this thread:

[http://ubuntuforums.org/showthread.php?p=10300673#post10300673](http://ubuntuforums.org/showthread.php?p=10300673#post10300673)

It's worth a read, particularly post #20. Why would Ubuntu recognize drives in a different order on subsequent reboots?

Of course in that case I strongly recommend figuring out how to connect to the internet before proceeding further, but still, something that should be simple confuses even me :confused:

Not that I'm super bright, but I've installed Ubuntu literally hundreds of times.

---

### Post by Herman on 2010-12-31
> (process:415): GLib-WARNING **: getpwid_r(): failed due to unknown user id (0)@irockonguitar,
 I don't think that error message represents your actual problem, it seems to be a kind of non-specific error message, there's a thread on that one,  see[      [COLOR=#980101][ubuntu][/COLOR] GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)]("http://ubuntuforums.org/showthread.php?t=1443231") > could not find a medium with live file systemI tried googling for any more information about that one too but so far I haven't read anything that looks useful. 
Thanks for starting a separate thread about it, I'll keep on looking into it and if I find anything out I'll join your other thread.

I re-read your earlier post and I now think that's an error from your  Ubuntu system when it's trying to get started, and not a GRUB error.
That means if you can boot your Live CD again, mount Ubuntu and get into your hard-disk-installed-ubuntu's /var/log/syslog files you may find information around the bottom of your syslog, messages or kernel.log or similar files which may help someone to diagnose your problem. No guarantees, but it might help. The output from sudo lshw might also be useful to someone trying to help you.  :)

---

### Post by kansasnoob on 2010-12-31
Since I've already invested a lot of time into debugging ubiquity in Maverick I pushed things a bit further and broke out an old Win XP puter with a 160GB IDE drive, stuck in my 80GB IDE drive (on a different port), and then tried like heck to reproduce that thing where device designations change and I just can't!

Of course it also looks like that OP might be giving up and, while that's not good, it's better than hearing about a trashed system. But if I can't reproduce the bug I'm clueless :confused:

Maybe there are some corner issues where things go wrong that I've not been able to reproduce but what I know for sure is that selecting either "use entire partition" or "use entire disc" after choosing "Install alongside" will always hose things if only primary partitions exist, and sometimes even if logical partitions exist!

Does that make sense?

---

### Post by Rubi1200 on 2011-01-04
The suggestion I am about to make may come across as unhelpful or even pessimistic but this is how I see things as they currently stand:

1. we have an installer in 10.10 that has been known to destroy other operating systems

2. there seem to be some other tangential issues which may also cause problems (kansasnoob has posted recently about issues with the order of drives being recognized)

3. users are apparently confused about the options to use as well as the lack of an error message at the who are you screen when the name contains an uppercase letter

4. there is no screen to review changes before committing to the installation

5. it makes our job harder trying to troubleshoot, explain, and fix these issues

6. I fear people may well be put off from trying Ubuntu if this becomes more serious (I suspect there are people whose Windows installs were messed up who did not post here on the forums. Therefore, the extent of the damage may be greater than that which we have already seen)

Here is what I would like to recommend in terms of the advice we give to new users:

Download the image for 10.04 and check the integrity

Burn to CD

Try as a LiveCD and post the results of sudo parted -l to check they don't have 4 primary partitions already (another issue that is becoming more prevalent especially it seems with Dell and HP computers)

Install and _then_ upgrade immediately to 10.10 (to avoid, hopefully, some of the issues we often see with upgrading)

Don't get me wrong, I am not a big fan of upgrades, preferring fresh installs.

But, I don't recall seeing too many posts about Windows being overwritten with the 10.04 installer.

What do you think?

I certainly would value any and all input regarding this matter.

---

### Post by kansasnoob on 2011-01-04
@Rubi1200,

Just so you know, I'm not ignoring you :D

I've actually thought about just recommending folks stick with 10.04.1 (10.04.2 is due around the end of this month), but I know when 10.04 rolled out there was a lot of trouble with graphics/KMS. I think that improved a little in Maverick.

The real problem is that most of those who have experienced data/OS loss probably wouldn't see our warning(s)! Very early into this debacle I addressed both Ayatana, and the ubuntu-installer-team, and I was ignored. Only recently have any of my bugs even gained a status beyond "won't fix".

ATM my feeling is that I've done all I can other than helping Herman with some captions, which I need to get back to ASAP. Based on previous experience I think it's incredibly doubtful that they'll create a replacement iso for 10.10 anyway.

I even cc'ed SABDFL with my concerns about the new ubiquity and if he isn't concerned why should I be? Maybe he wants to move away from providing noobs with a safe dual-boot, I dunno :confused:

---

### Post by kansasnoob on 2011-01-04
Honestly this web page should show a huge warning:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Like: The use of the "Install alongside" option in the installer will likely result in the loss of data, etc.

---

### Post by candtalan on 2011-01-05
> **kansasnoob said:**
> Honestly this web page should show a huge warning:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Like: The use of the "Install alongside" option in the installer will likely result in the loss of data, etc.

I distribute CDs regularly at my local Computer fair (UK). In each and every 10.10 CD paper envelope is a notice as follows:

===========================
Ubuntu 10.10 Installer Bug
Warning

Most functions in this installer work fine, and are ok. However: One particular option button in this installer will cause data damage, you are advised to avoid it if you have data anywhere on the hard drive!

During the Install Ubuntu process, and from the first of three installer options:
'Install alongside other operating systems'.

You are then offered a facility to re-size a partition to allocate drive space. The re-size facility itself has no problems, if you wish to use it please do. However, two more choices are also shown in this display in a pair of buttons: 
'Use Entire Partition' and 'Use Entire Disk'

Warning:
Both of these  buttons do the same thing - they use the entire disk, and any other partitions on the disk will be lost.
(Reference:    Bug #659106)
===========================

afaik this note is suitable and valid for the worst of the bug/s?

---

### Post by Rubi1200 on 2011-01-05
That is very interesting indeed!

Are these official Ubuntu CDs distributed by Canonical?

Is there any reference as to who wrote the warning; a name, for example?

---

### Post by candtalan on 2011-01-05
> **Rubi1200 said:**
>  Are these official Ubuntu CDs distributed by Canonical?
 

Ah! Clarification - The CDs I distribute are burned by ME from downloaded images - official images - but the actual CDs are not from Ubuntu/Canonical. I cannot in all conscience hand a CD to someone in the knowledge that they might trash their hard drive. So I composed and printed the warning note. The initiative and the note, is mine. I commend it to anyone else who is handing out 10.10 desktop CDs!

---

### Post by kansasnoob on 2011-01-06
> **candtalan said:**
> I distribute CDs regularly at my local Computer fair (UK). In each and every 10.10 CD paper envelope is a notice as follows:

===========================
Ubuntu 10.10 Installer Bug
Warning

Most functions in this installer work fine, and are ok. However: One particular option button in this installer will cause data damage, you are advised to avoid it if you have data anywhere on the hard drive!

During the Install Ubuntu process, and from the first of three installer options:
'Install alongside other operating systems'.

You are then offered a facility to re-size a partition to allocate drive space. The re-size facility itself has no problems, if you wish to use it please do. However, two more choices are also shown in this display in a pair of buttons: 
'Use Entire Partition' and 'Use Entire Disk'

Warning:
Both of these  buttons do the same thing - they use the entire disk, and any other partitions on the disk will be lost.
(Reference:    Bug #659106)
===========================

afaik this note is suitable and valid for the worst of the bug/s?

I like that!

I'm fairly well convinced that getting folks to NOT click on either "use entire partition/disc" would considerably reduce the bleeding :p

---

### Post by kansasnoob on 2011-01-06
How hard can it be to explain installing?

Look here:

[http://ubuntuforums.org/showthread.php?t=1653686](http://ubuntuforums.org/showthread.php?t=1653686)

Perhaps two of the most perplexing things were the FlexNet error and the fact that the OP absolutely refuses to get past this Drive C, Drive E, nonsense!

I think that's a good example of what goes through someones mind when trying to install Ubuntu.

Any ideas?

---

### Post by Rubi1200 on 2011-01-06
> **kansasnoob said:**
> How hard can it be to explain installing?

Look here:

[http://ubuntuforums.org/showthread.php?t=1653686](http://ubuntuforums.org/showthread.php?t=1653686)

Perhaps two of the most perplexing things were the FlexNet error and the fact that the OP absolutely refuses to get past this Drive C, Drive E, nonsense!

I think that's a good example of what goes through someones mind when trying to install Ubuntu.

Any ideas?
I must admit that was a difficult case to deal with. You did a fantastic job helping out there!
Fortunately, this was, I hope, the exception rather than the rule.

As far as the FlexNet issue; that was supposedly fixed for certain software in Maverick, though I have seen problems with it anyway.

Another forum user just posted this recently:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)
I wonder if this is the solution for these types of issues?

I still think we should consider telling users to install 10.04 and then upgrade immediately to 10.10.

I know there were/are KMS issues, but for the most part the workarounds are fairly easy to deal with (at least for Intel graphics which is what I tested).

If we still recommend 10.10 then somehow we need to get the message across that the "install alongside" option can, and will, destroy other operating systems and that they MUST use the manual partitioning option.

Obviously, though, we do not want to put people off from trying Ubuntu so I am not sure how to proceed on this matter.

---

### Post by kansasnoob on 2011-01-06
I have the fastest internet available here and that would mean a minimum of 2 1/2 to 3 hours.

30 minutes to install  (including the interactive part)

1 hour to update the fresh install

1 1/2 hours to complete the upgrade from Lucid to Maverick.

IMHO it's not practical!

---

### Post by kansasnoob on 2011-01-06
Just happened to think, always a dangerous thing :lolflag:

Look how many times I tried to explain Ubuntu/Linux device designations throughout that procedure. It's like pulling teeth to teach people about Ubuntu device designations!

They just won't let go of Drive C, Drive E, etc! That's why I preferred the "use largest continuous free space" option. Super simple and almost foolproof.

I see some dancing going on:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

Assignee went to "nobody" again.

Then Colin responded to this old dead bug:

[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732)

I don't know whether to be hopeful or just cry.

---

### Post by Rubi1200 on 2011-01-07
> **kansasnoob said:**
> I have the fastest internet available here and that would mean a minimum of 2 1/2 to 3 hours.

30 minutes to install  (including the interactive part)

1 hour to update the fresh install

1 1/2 hours to complete the upgrade from Lucid to Maverick.

IMHO it's not practical!

I was able to install 10.04 on my machine in 10 minutes (tested a few times).

Nonetheless, I see your point.

The only thing is this; I find it difficult to support using an installer that has known issues with it.

I am happy to recommend manual partitioning only. But, as you saw, this has its own bag of troubles too.

---

### Post by kansasnoob on 2011-01-07
> **Rubi1200 said:**
> I was able to install 10.04 on my machine in 10 minutes (tested a few times).

Nonetheless, I see your point.

The only thing is this; I find it difficult to support using an installer that has known issues with it.

I am happy to recommend manual partitioning only. But, as you saw, this has its own bag of troubles too.

Since 11.04 (Natty) is going to the Unity desktop I expect much more trouble.

So, IMHO, we need to steer people onto the LTS, and warn them of the bugs in the 10.10 live installer.

If any of you have an idea how to get that warning displayed please do so.

---

### Post by kansasnoob on 2011-01-29
Just wanted to say I've been too busy to do much lately, and I also painted myself into an additional time consuming corner:

[http://ubuntuforums.org/showthread.php?t=1677845](http://ubuntuforums.org/showthread.php?t=1677845)

That was really stupid of me :(

Anytime we fail to back things up properly it will, sooner or later, bite you where the sun don't shine.

Anyway, I'll very soon be iso-testing Natty Alpha 2 and I wondered if someone would care to add any ubiquity bugs to this list:

[http://ubuntuforums.org/showthread.php?t=1629809](http://ubuntuforums.org/showthread.php?t=1629809)

NOTE: That was my list for Alpha 1, and for our purpose here lets focus only on ubiquity. In fact, due to time limitations, that will be my primary focus. I won't bother with Unity bugs and such ATM.

I just want to be sure I'm not overlooking something regarding ubiquity.

---

### Post by kansasnoob on 2011-01-30
One bug less according to this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/555896)

Somewhat minor I guess but progress none the less.

---

### Post by Hakunka-Matata on 2011-02-21
Whilst reading through this page, I noticed a typo, just to let you know, doesn't bother me, but thought you might want to know.  Good guide, and necessary for a specific set of new Ubuntu users.

> [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

> 
The computer used for this demonstration is one I assembled myself for less than half the price I would have paid for a factory made model with equivalent hardware.
It's a fairly standard computer, nothing too fancy, but it's capable enough to run Ubuntu and even Windows 7 or Vista. It has an ASUS P5QL PRO motherboard, and the CPU is an Intel(R) Core(TM)2 Quad CPU Q8400 @ 2.66GHz. It only has  2x1GB DDR2 800 mhz RAM at the moment, and the graphics [COLOR="Red"][SIZE="4"][SIZE="5"]**cars**[/SIZE][/SIZE][/COLOR] is a GeForce GTS 250.
My regular Ubuntu installation is in an OCZ Vertex Series SSD which can boot Ubuntu in 3.03 seconds.
I'm leaving uplugged while I'm demonstrating these dual boot installations.

The boot loader I use and recommend is called the Grand Unified Boot Loader, known as GRUB for short.

typo highlighted, oversized, bolded.  Of course not serious, just a typo........

---

### Post by Herman on 2011-02-25
:oops: Oops! Sorry about that everyone, and thanks for correcting me, Hakunka-Matata.
I fixed it, just hit the 'refresh' button in your browser if the page doesn't look corrected yet.

Regards, Herman :)

---

### Post by kansasnoob on 2011-02-25
> **Herman said:**
> :oops: Oops! Sorry about that everyone, and thanks for correcting me, Hakunka-Matata.
I fixed it, just hit the 'refresh' button in your browser if the page doesn't look corrected yet.

Regards, Herman :)

You know things are really going to change, supposedly :confused:

In my original bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

Look at post #39. Then look at Evan Dandrea's post #43.

I assume we're in for a whole new set of surprises by March 31st. I'm somewhat regretting that I talked you into changing so much :(

---

### Post by Rubi1200 on 2011-02-25
On the other hand, Quackers, coffeecat, myself and others have been directing new users to this thread as well as Herman's site because of these issues.

We have also seen less posts from users who have lost everything as a result of the bug in Ubiquity.

---

### Post by Herman on 2011-02-25
> I'm somewhat regretting that I talked you into changing so much:) No, that's okay, in fact it's great! That's what my website was originally for, trying to help new users install Ubuntu safely. Thanks for prompting me to update the web page.
I / we can always update it again when the next release comes out, and just leave a warning there for Maverick. 
Congratulations on your progress with making it known and getting something done about it. Thanks for your help too. :)

---

### Post by kansasnoob on 2011-02-25
> **Rubi1200 said:**
> On the other hand, Quackers, coffeecat, myself and others have been directing new users to this thread as well as Herman's site because of these issues.

We have also seen less posts from users who have lost everything as a result of the bug in Ubiquity.

Maybe some people actually do read the release notes :D

---

### Post by kansasnoob on 2011-03-03
Some progress :D

The silly buttons are gone:

[ATTACH]184941[/ATTACH]

And "Use largest continuous free space" is coming back according to post #30 here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852)

But since the UI is not complete we have a new bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/727842](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/727842)

I'm sure that'll be fixed fairly soon.

The one real drag is this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/628097)

It earned a won't fix status :(

Be sure and look at post #7 there as I included a tar.gz of the comparison between Lucid's manual partitioning window and Natty's. It's a bummer.

So I need to file a new bug report specific to improving only that window. I'd really appreciate some help and/or suggestions regarding that. I suppose the simplest fix would be a rewrite of the bootloader installation options.

It wouldn't make me angry if someone else jumped on filing that one :D

---

### Post by kansasnoob on 2011-03-03
OK, I filed the new bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/728615](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/728615)

I hate the title I chose :(

But I hope I explained it well :confused:

---

### Post by ormosia on 2011-05-31
As a new user to Ubuntu and linux, after playing around with it for a while I fall nto the category of new user who may have lost everything in vista during the installation phase. I wish I had read this thread before I started. Anyway thanks to Kansasnoob and rubi1200 for theior ongoing advice which seems to be heading to an unintended ubiuity wipeout installation. However, I am not deterred. The reason I chose ubuntu was to move away from an ever-increasing computer software support cost and depndency. So I will probably cry a bit, then slwly reinstall all my files, bar some two months worth which, though backed up on a 1 terabyte usb drive that encrypted them as a progressive backup. The bulk of my research is however backed up. We live and learn. I think my error was resizing the partitions during installation instead of within Vista. Thhis whole partition thing needs to be simplified if ordinary mortals are going to move across from windows environments. That said ubuntu was up and running without a hitch. I was impressed with that side of it. Thanks for all your help :KS for us novices

---

### Post by kansasnoob on 2011-05-31
> **ormosia said:**
> As a new user to Ubuntu and linux, after playing around with it for a while I fall nto the category of new user who may have lost everything in vista during the installation phase. I wish I had read this thread before I started. Anyway thanks to Kansasnoob and rubi1200 for theior ongoing advice which seems to be heading to an unintended ubiuity wipeout installation. However, I am not deterred. The reason I chose ubuntu was to move away from an ever-increasing computer software support cost and depndency. So I will probably cry a bit, then slwly reinstall all my files, bar some two months worth which, though backed up on a 1 terabyte usb drive that encrypted them as a progressive backup. The bulk of my research is however backed up. We live and learn. I think my error was resizing the partitions during installation instead of within Vista. Thhis whole partition thing needs to be simplified if ordinary mortals are going to move across from windows environments. That said ubuntu was up and running without a hitch. I was impressed with that side of it. Thanks for all your help :KS for us novices

What version of Ubuntu did you install?

This only applied to 10.10.

---

