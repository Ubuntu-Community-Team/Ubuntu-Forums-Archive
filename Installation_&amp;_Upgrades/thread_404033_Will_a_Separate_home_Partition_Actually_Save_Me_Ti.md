---
title: "Will a Separate /home Partition Actually Save Me Time?"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by odelay on 2007-04-07
I recently did a clean reinstall of Kubuntu.  Because I was in the position to, and knew that I'd be upgrading to Feisty soon, I installed with my /home directory on a separate extended partition.

Everyone recommended doing so as it would save you a lot of time when doing future clean installs.  The more I think about it, the more I wonder what is actually going to still be there when I do a fresh Feisty install.  I have an extremely small /home folder because I keep all my music and photos on a separate FAT32 partition to share with Windows.  So will I actually benefit much from having a separate /home partition?

Here are the most time-consuming things I do when installing Ubuntu:
*  Set up proprietary ATI drivers
*  Set up ndiswrapper and configure my wireless card
*  Install non-repo software like Mathematica
*  Install proprietary codecs (mp3, aac, wma, mov, mpg, avi, etc.)
*  Get Samba working with my mac
*  Mount read-only NTFS partition at startup
*  Install Flash plugin
*  Download/Install Jave Runtime Environment (JRE) and Firefox plugin

Out of this, what exactly will be saved when I do a clean install?  This takes up 90% of the installation time for me, but it seems most of the steps require files or applications that wouldn't be stored in my /home directory.

If I'm still going to have to do most of this anyway, are there any other steps I can take to make updating/reinstalling less painful?

Thanks

---

### Post by cantormath on 2007-04-07
it can save your files if you brick your linux distribution.  If you need to reinstall linux for any reason your personal files will be stored on a separate partition.

---

### Post by az on 2007-04-07
Maybe five or ten years ago, when storage media was expensive and slow, a seperate home partition was a cool and geeky thing to do.  Today, it is far easier to just boot a live cd, rescue your files to an external drive and start over.  It is far more complicated to set up a seperate home partition and people typically end up running out of space because one of the two partitions is full (something that probably would not have happened if they just used all the space for the root partition which shares the space with home)

Not to mention the headache of fixing a configuration problem that is saved in your home folder dotfiles....  If you screw up your panel, (and are left without a useful desktop, for example) you will reinstall and still be faced with the same problem.

---

### Post by cantormath on 2007-04-07
> **az said:**
> Maybe five or ten years ago, when storage media was expensive and slow, a seperate home partition was a cool and geeky thing to do.  Today, it is far easier to just boot a live cd, rescue your files to an external drive and start over.  It is far more complicated to set up a seperate home partition and people typically end up running out of space because one of the two partitions is full (something that probably would not have happened if they just used all the space for the root partition which shares the space with home)

Not to mention the headache of fixing a configuration problem that is saved in your home folder dotfiles....  If you screw up your panel, (and are left without a useful desktop, for example) you will reinstall and still be faced with the same problem.

i still find a separate partition alot simpiler then rescueing my system with a live cd.

---

### Post by odelay on 2007-04-07
But will any of the things in my previously mentioned list be saved, or will I have to reinstall them regularly?

---

### Post by cantormath on 2007-04-08
you may have to reconfigure stuff, but you wont need to recover lost data.

---

### Post by odelay on 2007-04-08
Sorry...but I'm still not really getting a clear idea of what you mean.

Take wireless for example.  I had to go in firefox and download both Dell's drivers and ndiswrapper.  Then I had to properly install the driver through ndiswrapper.  What I'm asking is, will I need to download ndiswrapper and the Dell driver again to get everything working...or will my wireless function just as it did before the installation?

I understand how configuration files are sometimes stored in /home but I'm pretty sure the actually ndiswrapper and Dell driver files are located elsewhere.

Appreciate it.

---

### Post by Stephen Howard on 2007-04-08
Dedicating a partition to /home will not help you with those tasks as they're essentially 'global' rather than being specific to a user.  The advantage of a separate /home partition is that you don't need to format it when you do an upgrade, and therefore it will keep each user's current desktop customisations after upgrade (ie your personal desktop look'n'feel won't need to be tweaked afterward).

The other advantage that might help you is that a separate /home partition can be used as an archive of the files that don't really change much.  For instance, after an upgrade I need to reinstall java.  Java doesn't change very often, so I keep the download file in an archive in /home, and just re-install without downloading it again.  The same would apply to the ndis stuff and the ATI drivers (eg I keep my nvidia driver download file in my /home archive directory).

---

### Post by Stephen Howard on 2007-04-08
oh, and the other advantage of a separate /home partition is that you can install commercial games there and not have to go through the hassle of reinstalling them from CD after each os upgrade.  In fact, I keep my commercial games in their own partition /usr/local so that other users on my lan can access them.

---

### Post by az on 2007-04-08
> **cantormath said:**
> i still find a separate partition alot simpiler then rescueing my system with a live cd.

Yes, but you know about partitioning and feel comfortable doing that.  To someone else, learning about partitions, and guesstimating how big they should be, what filesystem and so forth is a lot more involved than just offering them a sane backup solution (which now exists in current versions of Ubuntu.  Even for Dapper, it's still just clicking on the disk icons and then dragging and dropping...)  The learning curve for partitioning your drive is steeper than just learning how to copy files.

There is no requirement to even know what partitioning is to install and run Ubuntu.  Encouraging people to create a separate home partition only introduces unneeded complexity to the install process, and that for very little purposeful gain.

---

### Post by Stephen Howard on 2007-04-08
> Encouraging people to create a separate home partition only introduces unneeded complexity to the install process, and that for very little purposeful gain.

I entirely disagree.  Most new users already have to deal with partitioning because 99% will keep ms-windows on a separate partition 'just in case'.  Additionally, a separate /home partition will make life easier for the new user who perhaps decides to reinstall the whole  system over again because they've managed to screw some system setting up while they've been experimenting - I know I did that a few times when I first started playing with linux.  Also, most distros will provide sane default sizes for partitions.

---

### Post by az on 2007-04-09
> **Stephen Howard said:**
> I entirely disagree.  Most new users already have to deal with partitioning because 99% will keep ms-windows on a separate partition 'just in case'.  Additionally, a separate /home partition will make life easier for the new user who perhaps decides to reinstall the whole  system over again because they've managed to screw some system setting up while they've been experimenting - I know I did that a few times when I first started playing with linux.  Also, most distros will provide sane default sizes for partitions.

By default, the Ubuntu installer will take care of the partitioning for you.  That's the extent the average user should have to care about partitions.  99 percent of users can dual boot without mucking about.  And one reason why there is no easy "keep a seperate home partiton" option in the installer is because the size required differs drasticaly between users.

It is actually a nightmare to run out of room in your home partition.  And a lot of people do.

And to get back to the point of this thread, the average user does not know what is kept and what is lost when reinstalling and keeping a seperate home partition.  It is just a lot more straightforward to back things up by hand.  You would have no questions and no unpleasant surprises.

---

### Post by odelay on 2007-04-09
Running out of space in my /home partition isn't really an issue for me, and I suspect many other users are in this position.  I have a separate "media" FAT32 partition that I share with Windows.  My music library is about the only thing that takes up any space...and that is kept on the Fat32 partition, not /home.  Mac OS X is my primary OS, which I use on a 3-year-old laptop.  I use Windows for engineering applications, and I use Ubuntu mostly just for educational purposes and to see what's going on in the Linux World.  So I don't really see myself running out of space in either my "/" or "/home" partition.

Since Ubuntu is more of a hobby for me, and I plan on continually upgrading to the latest, greatest version every few months, I'd really like to make this a less time-consuming process.  It pretty much takes me an entire weekend to do a clean install (that's about 20 hours).  I usually feel sick, exhausted, and completely disinterested in trying out my new OS by the time I finish.  I've even made a text document describing every single thing I have to do.  But it seems I *always* run into problems and find myself scouring the forums for hours trying to figure out what broke my wireless, or why my computer can't go to sleep, or why I can't install JRE the same way I did last install...

I'm really having a hard time convincing myself I value my time when I waste an ungodly number of hours configuring Ubuntu.  When I think about it, it's starting to seem like an awful addiction.  I've spent 99% of my time setting up Ubuntu and about 1% actually using it.  Maybe I'm just bored from using a Mac all my life---there's never anything to fix.

Sorry that devolved into a rant...but back to my original question:

What can I actually *do* to make reinstalling ubuntu less painful?!?

Thanks for the feedback guys!

---

### Post by az on 2007-04-09
> **odelay said:**
> 
What can I actually *do* to make reinstalling ubuntu less painful?!?


I suggest dist-upgrading instead of re-installing all the time.  To make that easier, avoid thrid-party packages.

*  Set up proprietary ATI drivers
What's wrong with the proprietary drivers that ship with the latest Ubuntu?  

*  Set up ndiswrapper and configure my wireless card
Ndiswrapper is on the install disk.  You do not have to compile it from source.  Just pop the install disk into the drive once you have installed Ubuntu and follow the instructions about starting the package manager.  Search for and install ndiswrapper-utils and you are done.  That should take three minutes, tops.

*  Install non-repo software like Mathematica
I dunno.  Anyway, if you need the toolchain to compile it, that, too, is on the install disk.  Just install build-essential in the same way as ndiswrapper-utils.


*  Install proprietary codecs (mp3, aac, wma, mov, mpg, avi, etc.)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
    [I]Click Applications &#8594; Add/Remove. In the top right, change the setting to "All available applications". Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.
     To play most DVDs you'll need the libdvdcss2 package. This package is available using Medibuntu. This is a third party package, and not supported by Ubuntu.[/I]

*  Get Samba working with my mac
I dunno.  Maybe this:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

*  Mount read-only NTFS partition at startup
[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)
or
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

*  Install Flash plugin
Already done in step four.

*  Download/Install Jave Runtime Environment (JRE) and Firefox plugin
install sun-java6 (sun-java-6-bin and sun-java6-plugin)

Done.

---

### Post by odelay on 2007-04-09
> **az said:**
> *  Set up ndiswrapper and configure my wireless card
Ndiswrapper is on the install disk.  You do not have to compile it from source.  Just pop the install disk into the drive once you have installed Ubuntu and follow the instructions about starting the package manager.  Search for and install ndiswrapper-utils and you are done.  That should take three minutes, tops.

I have a BCM4311...I could have sworn I read that you have to compile it from source for it to work properly.  Perhaps things have changed since then.  I can never keep track....sigh.

Thanks for the info.  On paper it always seems like it should only take an hour or so to update everything, but something always goes wrong.  ](*,)

---

### Post by az on 2007-04-09
> **odelay said:**
> I have a BCM4311...I could have sworn I read that you have to compile it from source for it to work properly.  Perhaps things have changed since then.  I can never keep track....sigh.


The version of ndiswrapper in Warty ( I think) did not support some broadcom cards.  All subsequent versions work fine.  

Out of all the hundreds of cards out there, only about two or three require a new upstream version of ndiswrapper in the current version of Ubuntu.  You can check the ndiswrapper changelongs to see which cards are newly supported since the last release.

---

### Post by Stephen Howard on 2007-04-09
> * Install non-repo software like Mathematica

This is a great example of the advantage of using separate partitions.  If you install mathematica on the separate partition (in my case I call it /usr/local), you won't need to reinstall the commercial software each time you reformat your system partitions during a major distro update.

---

### Post by odelay on 2007-04-09
> **Stephen Howard said:**
> This is a great example of the advantage of using separate partitions.  If you install mathematica on the separate partition (in my case I call it /usr/local), you won't need to reinstall the commercial software each time you reformat your system partitions during a major distro update.
Well that's good news.  I guess I'll see how it all works out next Thursday.

---

### Post by Huffalump on 2007-04-21
> **odelay said:**
>  I have a separate "media" FAT32 partition that I share with Windows.  My music library is about the only thing that takes up any space...and that is kept on the Fat32 partition, not /home. 

If other Windows users are in this same situation, you might consider a different arrangement.  I faced the same issue:  how to access my media from both Windows and Ubuntu.  In the end, I used ntfs-3g which allows read/write to NTFS drives without error.  

That allowed me to keep things on NTFS without resorting to a special FAT32 intermediary partition.  If you wanted to keep your media on Ubuntu, then jsut install an Ext3 reader on Windows (there are free ones available for download, read-only)

---

### Post by odelay on 2007-04-21
Just as an update--I installed Feisty last night.  I also recently switched out my BCM4311 for an IPW3945 (best decision ever) so I didn't have to worry about ndiswrapper.

With all the fixes in Feisty...setup was almost non-existant.  Here's all I had to do:

Install ATI fglrx drivers
Edit my xorg.conf to disable "tap click" on my touchpad as well as remove all the Wacom entries that cause problems
Install Firefox, Krita
Run Amarok - install mp3 codecs automatically
Flash, Java, Codecs, MS Fonts, Everything: Menu>System>Add/Remove - in "Other", install Ubuntu Restricted
Install samba (adept "samba")
Fix Hibernate/Suspend - edit four lines in the acpi file

Tada!  That's it.  I especially love having Flash, JRE6, Java Firefox plugin, MS Fonts, and more taken care of in one single step.  It's a shame Suspend was broken (worked fine in Edgy)...but the fix wasn't a big deal.

In conclusion, I couldn't be more happy I made a separate /home partition.  It allowed me to get back to work within a matter of minutes.  Great stuff.

---

### Post by mhansen on 2007-04-21
Just remember that it's still a good idea to back up /home anyway.  I kinda got a little lax on that when I had a separate /home directory, and once it came back to bite me in the rear.  Now I keep everything on one partition, but tar up my /home directory once a week or so and keep it on an external drive.  Since u say you have a FAT32 parition, u can go ahead and keep a backup there.  You'll be glad you did!

You should probably also do a dpkg --get-selections > installed-software.log and back that up too.  Later, if needed after a fresh install, for instance, you can do a dpkg --set-selections < installed-software.log and use dselect to reinstall those packages.  It makes it a lot easier than trying to remember what you had installed.  :)




Regards,
Mike

---

