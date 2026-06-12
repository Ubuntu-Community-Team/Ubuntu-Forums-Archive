---
title: "What's Missing In Install Process?"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-06-30
The title is stated as a question, but actually I am about to mention what I feel is missing, and then you decide for yourselves or contribute your own ideas.

The first group involve the Partitioner.  Lack of options include:  No way to designated a particular drive or partition, unless you do it manually.  The other choices all deal with the idea of a single drive and single partition system.

Second is the lack of ability to designate a partition label if a reformat is done.  A choice of retaining the existing label or providing an new one would be nice.  A reformat also causes a new UUID to be assigned.  Why not a choice of keeping the existing one instead?
.
Third is the fact that instead of seeing partitions in the order of first
to last across the disk, the partition table updates so that they are seen in order of being added, resized, deleted and readded, and instead
of limiting the designations to /dev/sda1 on up, the numbers just go up, so you would lose the use of designations for partitions that got modified, as they would be given a new one at the end of the present list.  May not seem significant, but it means you may end up with four partitions on the first disk designated /dev/sda12, /dev/sda9, /dev/sda5, /dev/sda8.  Try dealing with that later.  And while you can decide to just get a new partition table, that means a complete wipe of your hard drive with no chance to recover what gets lost in the process.

Ought to be given a chance to designate which drive or partition houses /home for this install, and you can even decide to use the same /home for multiple installs on different partitions.  Yes, you can indicate /home as it stands now, but not if you want /home to just reside on the same hard drive as / or any other designated partition.  Trying to use the same /home for multiple installs has another flaw as well.  Configuration settings unique to each user account then get applied to the new install as well.  That could mean an existing flaw in an account would carry to the next install as well.  There seems to be no easy escape from this.

And that brings up another choice option that should come with a fresh install.  If the partition that will be used for /home already has a /home on it, should the installer ask if the configurations for all users be set back to default, or should the configurations for any designated user be reset to default?  This could be a help.  But it might be more important to come up with a tool or process to have a user's settings all set back to default in an effort to just clear any hangup with just that account.  A reinstall as a means of dealing with one account would be miss-targeted because of all the updates and add-ons that would have to be downloaded and reinstalled as well.  And a reinstall effects all users, and not all users work with the same set of add-ons.  So now everybody suffers because of a screwup with just one account?  Not a good approach.

---

### Post by dabl on 2010-06-30
I semi-disagree (I agree the Ubiquity installer is pretty underwhelming -- it has been for the 5 years I've used *buntu ...).

I would not wish to see the Live or Alternate Install CD get any more cluttered with partitioning-related stuff than they already are -- it's a waste of space that could be far better used for OS features.

The smart bunny (IMHO) makes a [[COLOR="Green"]**Parted Magic Live CD**[/COLOR]](http://partedmagic.com/download.html) (or better yet a bootable Parted Magic USB stick) and uses that to take care of partition table-making, partitioning, formatting, flag-setting, and all of that prior to ever loading the *buntu installation CD.  If you do it this way, (a) you have a clear and effective understanding of how your hard drive and partitions are laid out, and (b) you don't need Ubiquity's crummy partitioner to do anything but find your partitions and filesystems.

That's my two cents' worth on it.  :guitar:

---

### Post by darkod on 2010-06-30
1. If I'm not mistaken you can select a particular disk by temporary selecting (even if you don't plan to use it) the Erase and use whole disk option. That will enable the drop down list to select a disk. After that simply select another option for installing, the selected disk remains the same.

2. I don't get your idea when you say you can't select particular partition except manually. If you want to specify exact partition, not just a disk, isn't that manual process already? It works fine as it is.

3. The same applies for /home, don't understand your point. Yes, you can select which partition to be used with /home mount point, regardless on which disk it is. The manual partitioning windows allows you to do this and it shows all disks with all partitions listed.

4. As far as asking for making "default" settings in existing /home, that's opening a Pandora's box. How will you decide which setting needs changing and which not? If you want "default" settings doesn't simply installing new /home do that? Simply tick the format box for /home also, usually you wouldn't precisely because you want to keep the data and settings.

I think the installer is quite good as it is. The only comment I have personally, is the side-by-side option. In the ideal world users should investigate first whether it's better to shrink the windows partition with the ubuntu installer or not. Vista and 7 have a resize tool included in Disk Management now and because windows is picky, you should rather use that.
Unfortunately, a new user simply sees the "install them side-by-side choosing between them on start up" and says, great, just what I need. And in those cases where shrinking windows like that makes it corrupted, the user thinks ubuntu broke my windows.
The fact that most machines these days don't come with windows install media doesn't help either to simply and efficiently repair windows. And using a restore partition would wipe your new ubuntu and your windows data, so it's not really a solution.

But you can't explain all of this in the installer after all. If you want to install an OS yourself, you do need to educate yourself first. Maybe renaming the "side-by-side" option is the first step so it doesn't make users go for it right away when they see it.

As I tell a lot of users, especially if you have a single hdd, regardless how you install ubuntu the OSs will be side by side. Where are they going to go? :)

---

### Post by darkod on 2010-06-30
> **dabl said:**
> 
The smart bunny (IMHO) makes a [[COLOR=Green]**Parted Magic Live CD**[/COLOR]]("http://partedmagic.com/download.html") (or better yet a bootable Parted Magic USB stick) and uses that to take care of partition table-making, partitioning, formatting, flag-setting, and all of that prior to ever loading the *buntu installation CD.

I semi-disagree with this. :)

Why another cd when you already have the ubuntu cd? I haven't seen the Parted Magic LiveCD but it sounds to me like if you know how to use it then you would:

a) know how to use Gparted from ubuntu live mode to create your partitions in advance if wanted
b) know how to create your partitions using the manual partitioning in the installer itself

I prefer b) because you set mount points while creating the partitions right away. With any other method to create partitions in advance, it's double work because you are first creating them, and then again use manual partitioning in the installer to set them Use As with mount points, filesystem, etc.
The manual partitioning in the installer already gives you total control.

---

### Post by dabl on 2010-06-30
> **darkod said:**
> I semi-disagree with this. :)

Why another cd when you already have the ubuntu cd? I haven't seen the Parted Magic LiveCD but it sounds to me like if you know how to use it then you would:

a) know how to use Gparted from ubuntu live mode to create your partitions in advance if wanted
b) know how to create your partitions using the manual partitioning in the installer itself

I prefer b) because you set mount points while creating the partitions right away. With any other method to create partitions in advance, it's double work because you are first creating them, and then again use manual partitioning in the installer to set them Use As with mount points, filesystem, etc.
The manual partitioning in the installer already gives you total control.

It's a reasonable view.  But "double work" is an efficiency argument, and assumes (as you say) that the user "already knows" how to do this work.

For the novice who _doesn't_ already know, efficiency is not the most important consideration.  Effectiveness is what he/she needs, and the simpler the task at hand, the better his/her chances are of getting it done effectively.  These forums are full of posts resulting from partitioning mishaps during installation from the "consolidated" Live CD.  I believe those mishaps are a result of just a little bit too much complexity for the novice.  By splitting the partitioning job away from the OS-installing job, you make it simpler.  Simpler is better, in this case, even at the expense of efficiency.

BTW, Parted Magic just happens to be my favorite, because of the other benchmarks and utilities that come bundled with it. Any Live CD that has gparted on it will suffice for partitioning, just as you say.  :)

---

### Post by oldefoxx on 2010-07-01
> **darkod said:**
> I semi-disagree with this. :)

Why another cd when you already have the ubuntu cd? I haven't seen the Parted Magic LiveCD but it sounds to me like if you know how to use it then you would:

a) know how to use Gparted from ubuntu live mode to create your partitions in advance if wanted
b) know how to create your partitions using the manual partitioning in the installer itself

I prefer b) because you set mount points while creating the partitions right away. With any other method to create partitions in advance, it's double work because you are first creating them, and then again use manual partitioning in the installer to set them Use As with mount points, filesystem, etc.
The manual partitioning in the installer already gives you total control.

Sorry, but in this respect you are quite wrong.  The partitioner used with the installer gives you limited control, and limited information with which to work with, on top of which it offers limited options.  The boil down to this:

(1)  Give up Windows completely, at least on my first drive
(2)  Leave it to the  partitioner to decide how to divi-up the first drive, rendering new partitions, and which comes first:  Windows or Ubuntu?  If I've more partitions than one in use on the first drive, the excess and their contents will of course be blown away.  Have you made that clear enough so that anyone and everyone understqnds?

Why not an option to install to an added-in or added-on hard drive?  And how should that effect the boot choices, especially if the added on drive is not present?

The present installer process is simplistic almost to the extreme.  Yes, you have alternative choice with how to engage with the LiveCD when first booting up, but what do all those choices represent, and when should they be used?  The first two are likely the only ones considered, since no one outside the Linux community has any insight into the rest.

Even the manual process is flawed.  Does it tell me where my existing Windows install reside?  Does it tell me which partitions currently haqve data or other operating systems>  Does it report the present label used with a drive or partition?  Does it allow me to add a new label, with or without reformatting first?  Does it relate the UUID assigned to any partition if I feel I need to know it, and is there ever an option to reformat but keep the same UUIDv to minimize effects elsewhere?  And would it not be nice that the Ubuntu install also gave me the option to back up the contents of any partition before making any changes to it?

You and others cry for more options in the installed OS.  I say bull to that.  If you are connected to the internet, or able to read another CD or even a DVD, that can all come later.  Right now a single install.of Ubuntu 1 0.04 LTSis followed by the download and install of 205 updates.  Not it might be nice if all those updates could be burned to a CD or DVD so that a lot of download time is not needed in the future. but it might also make sense to just update the images themselves before they are downloaded again.  I never really understood why the only update to the parent image for delivery as such was with XP and SP2.  And even today, you get set up with Microsoft Update, it starts you with the oldest updates first, even though they were likely later incorporated into the service packs.  Most could therefore be dropped with Windows 3000, which
by the way, would allow an initial install of Windows 2k to work natively with huge drives by having EnableBigLba added and enabled in the registry, a feature not supported until SP3.

Microsoft at least has reason for what it does:  Make existing versions of Windows more appealing might mean killing prospective sales of any newer versions.  So they focus on the new versions, run ads to pursuade customers it is time to move on, and you might never hear that a fix was finally provided for the earlier version.  More likely though, is that therw will be no fixes sought for the earlier version.

I cannot see the Linux community being involved the same way.  So to borrow from the commercial method just means we are leaving something out, because that is what they are geared to do.

---

### Post by darkod on 2010-07-01
> **oldefoxx said:**
> Sorry, but in this respect you are quite wrong.  The partitioner used with the installer gives you limited control, and limited information with which to work with, on top of which it offers limited options.  The boil down to this:

(1)  Give up Windows completely, at least on my first drive
(2)  Leave it to the  partitioner to decide how to divi-up the first drive, rendering new partitions, and which comes first:  Windows or Ubuntu?  If I've more partitions than one in use on the first drive, the excess and their contents will of course be blown away.  Have you made that clear enough so that anyone and everyone understqnds?


You obviously didn't read my first post, just the last (or chose to ignore it).

1. Yes, you can select to install on another disk. Read the other post.

2. No partition will be blown away at all, even with the guided methods. Yes, ubuntu installer might offer to resize another partition than the one you planned, but it will NOT DELETE any. Stop confusing people.
And this is precisely the reason why I prefer the manual partitioning option, it does allow you to create your ubuntu partitions where you want them, and with the size you want them.

> Even the manual process is flawed.  Does it tell me where my existing  Windows install reside?

And what does someone who doesn't even know on which partition their windows is installed doing installing an OS? Leave it to someone who knows what to do.

You want the machine to do everything for you? It can't, deal with it. And I hope it never will, because at that moment, you and I, my dear friend, become obsolete!!!

I don't even want to start with the other things you mentioned, no point as far as I can see...

---

### Post by oldefoxx on 2010-07-02
Well, more bull I see.  Sometimes it isn't what will actually happen, since evidence of that only comes after the event, but you have to decide on what you are told.  And the install process says it will either wipe the disk or divide it evenly between Windows and Ubuntu.  I admit the choices in that regard are between bad and worse.  The first method means a complete commitment to Ubuntu and abandonment of Windows, so the second choice looks better.  But if you decide to revert to just Windows, where is the means of restoring the reformatted partitions into one whole one?  Windows won't even let the Windows user see anything except All that built in there as well?  And made so that anybody can just do it on the strength of a choice?  Afraid not.

If you haven't been through each process, then you don't know.  And I admit, what is said up front is enough to keep me away from choices 1 and 2.  Let's say you picked 2, a total erase and reformat.  Any warning that the present contents will be wiped out completely?  And which file system will be installed instead?  Now most people have a hidden partition where all there Windows install is stored, there for a full recovery effort, and does that get wiped out as well or not?  You say do it first and then find out?  I say that is rank nonsense.  But that may be just a difference of opinion.

To my mind, I do all that I can to present the broadest base for justifications and thought for what I get into, and yet someone like you says that you cannot even follow what I had to say about it.  To me, that just translates into your having such limited experience in that area that you truly just do not know what I am speaking of, but you assume that you do, and since your experience is so limited, somehow I must somehow be the one the wrong.

I have a refurbished desktop on hand to install Ubuntu to.  For the moment, I am toying with using 9.04 instead of 10.04, because 10.04 is turning out to be like the beaches along our gulf shores right now.  Go a few inches down into the sand, and you find particles of oil that will come up and plague us for years. So 9.04 is very tempting, but support has been dropped for it.

Anyway, I have the 9.04 drive in the CD drive, and trying to find a decent connector for converting PS/2 mouse and keyboard to work with USB with plugging into the desktop.  Reason is, the KVM switch is only for PS/2, and without it, I would have to have multiple keyboards and mice at hand rather than just one of each.

So for confirmation of what I said, I used the mouse to go up to the point where the partitioner is engaged.  I have only one drive on display, and no choice for viewing or picking between multiple drives.  Whatr is hooked up by USB is not apparent at this point, leaving out external and thumbdrives.  The choice is /dev/sda, and that is it.  So you have one strike against you.

I can install 9.04 along side what ever is already there.  The first three partitions are marked this way:  Windows Vista (loader), and the hardware name and size of the first partition.  The second partition is marked Windows Vista (loader) the next partition name and size.  No details about either.  The rest is marked as /dev/sda3 and size given.  It's brown, so maybe it isn't the same file system as the first two.  No way to tell at this point.  Is there anything more?  Three choices.

The first one starts off saying Install them side by aide, chosing between them each startup.  I sem to remember earlier releases indicating that the disk space would be divided between them.  But which partition here?  There are three showing, and no way of knowing which one is really available.  Besides, at this point I don't see that I will have a choice later.  Maybe not the best way to go.

Second option is to just use the entire disk.  This dives me a drop down list ,but only SCSI(0,0,0)(sda) is listed.  Under that it says this wsill delete Windows Vista (loader), Windows Vista (loader) and install Ubuntu 9.04.  Looks like your second strike.  It is really talking about redoing the whole hard drive here.  You do this, you are likely giving up the Windows Recovery option as well.

Third choice says  Specify partitions manually (Advanced), so even if you if you just want to use the third partition, /dev/sda3, this is considered an advanced setting.  And of course, when you go that route, there are numerous decisions to be made, and a beginner would not know where to start. 

Right. So three great coices, and you really can't back up from any of them. unless you have done your backups, but we are talking about beginners, right?  Maybe not strike three, but definately a foul ball.

---

