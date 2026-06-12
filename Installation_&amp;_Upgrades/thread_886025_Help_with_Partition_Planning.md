---
title: "Help with Partition Planning"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by MillerD on 2008-08-10
Hello,

I have been contemplating using Linux, Ubuntu to be exact, on my Vista machine. I have everything set, its just planning the Partitions that gets me. I don't know if my set up is weird but either way, I want to get this to work.

The way I'm set up is: I have 1 HDD on this machine. It is split into two partitions (C: and D:). One has a recovery tool (D:) for getting back vista and that is the entire partition. I would like to keep it just in case. The other Partition (C:) has Windows but it also has all my files for everything (It's how it was set up when I got it). Both are in NTFS format.

I would like it so I have it set so I have: One Partition for Just the Windows OS. One more for the Ubuntu OS. Another For the /home Part of Ubuntu that I hope could have the files that Were in C:. (And of course a swap).

So I want:    ||  Vista (NTFS)  |  Swap  |  /home (Ext3)  |  Ubuntu (Ext3)  |  Recovery Partition  ||

I have a tool for vista that lets it read and write in the Ext2/3 format so that not a problem. So far I know that I don't need to touch D:, and just make the /home partition after installing Ubuntu, the only part that bugs me, is getting the non OS related files (this would hopefully include stuff in program files, so just all that's needed for the OS) to the shared data of /home.

Any help for how I could accomplish this?

Greatly appreciated,
D. Miller

---

### Post by Pumalite on 2008-08-10
You first have to allocate space for Ubuntu with Vista's Partitioner. How much can you allocate?

---

### Post by MillerD on 2008-08-10
Well here is a screenie of how everything is set up: 

[[IMG]http://img257.imageshack.us/img257/2885/screenshot002kk6.gif[/IMG]](http://imageshack.us)

There's about 40GB open in C:, but a lot of the stuff in C: is all my personal files and stuff that I plan on moving out of it and then into thew shared area of /home. I checked and the User and Program Files folders are about 70 GB, but there gonna stay on the drive, just moved. Either way I have 40 open gigs. The external hard drive I'm going to use for back up so i can't really use that. So end story there are 40 open gigs on my computer.

---

### Post by mvdberg112 on 2008-08-10
If I have a choice on a new system, I like it always to setup as follows:
Partition one: primary, relative small - boot partition
Partition two: logical partition one in extended partition - OS partition. about 8-10 GB, usually enough to hold Windows or Linux including applications. If not enough, applications can be installed on a next partition.
Partition three: logical partition one in extended partition - DATA partition


one - this is a boot partition that only contains boot files, or a boot loader or DOS. If something goes wrong with the system, I can it to install an temporary OS, to copy an OS-CD to, to copy an NTFS file system reader, so I can read NTFS in case windows is broken  and the like
two - here goes the OS. If the OS crashes, I can safely reformat this partition without touching my data
three: easy to backup - I am sure that I never backup the OS or apps if I do not want to, because the DATA is only realy valueable thing-the OS can always be reinstalled.

---

### Post by MillerD on 2008-08-10
Yea well if I knew more about partitions when I got this compy a year ago, I would have made another partion right away for my real data and files, It would have made things so much easier.

---

### Post by Pumalite on 2008-08-10
With your 40 GB of 'free space', make 3 'New' partitions:
10 GB for'/'
The rest minus your RAM for /home
Then /swap=RAM
Use Gparted Live CD to do the job:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by MillerD on 2008-08-10
Okay, ty. a little bit of verification though. '/' is the main bit of ubuntu right? Also Gparted will make the /swap for me? And do i make these after installing ubuntu or before?

Thanks.

---

### Post by Pumalite on 2008-08-10
YOU will make the partitions. Read the Gparted Documentation.
After you have the partitions ready, remove Gparted, plug in Your Ubuntu Live CD, go Manual and use the prepared partitions.

---

### Post by MillerD on 2008-08-10
Ok after some searching and reading. What I think I am to do is to 1st shrink my partition on vista all the way. Then install Ubuntu with the auto sizing option. After that I then use Gparted to split that up into the partitions as you described.

Is this correct or am i gonig the wrong way completly.

Edit: I posted this right after your edit, ok that clears up alot ty.

---

### Post by Pumalite on 2008-08-10
Don't use the resizing option with the Ubuntu installer. Go Manual instead. More control. Less poss. of loosing your Windows.

---

### Post by MillerD on 2008-08-10
Okay that cleared up so much. I'm not going to do it quite yet but you have cleared up so much. Yea the only thing that reall confused me was how to use Gparted until I realized you need to change my BIOS

---

### Post by Pumalite on 2008-08-10
When you do it, make sure to backup everything before you start.

---

### Post by MillerD on 2008-08-10
Of course. I'm just getting all preparations together, making up a checklist of everything I need to do getting all isos burned, etc.

Edit: Would this be all the steps?

1. Back up all data.
2. Shrink Windows partition.
3. Set computer BIOS to "read from disk on start up".
4. Put in "GParted" and power on.
5. Make 3 'New' partitions: 10 GB for'/', The rest minus your RAM for /home, Then /swap=RAM.
6. Power off.
7. Put in Ubuntu Installer, use manual, and use the prepared partitions.
8. Ubuntu is ready! :D

Or can I just shrink the vista partition in Gparted?

Lastly Is it possible to move files from an NTFS system to an EXT3?

---

### Post by MillerD on 2008-08-11
Sorry for the bump, but I would like my question answer if they can be.

Thank you.

---

### Post by Pumalite on 2008-08-11
You cannot partition with the Ubuntu Live CD. Do it the way I told you.

---

### Post by MillerD on 2008-08-11
I don't quite see where you got that from. Where did I say I'd use the Live CD to partition?

---

### Post by sandysandy on 2008-08-11
also defragment windows before resizing.


here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by Pumalite on 2008-08-11
> **MillerD said:**
> I don't quite see where you got that from. Where did I say I'd use the Live CD to partition?

The Live CD uses gparted
You can 'see' Ubuntu from Windows with this driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
Ubuntu reads and write to an ntfs partition (Windows) by default.

---

### Post by MillerD on 2008-08-11
> **sandysandy said:**
> also defragment windows before resizing.


here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

Yes I do plan to,I plan to clean and optimise as much as possible.

Okay so Puma, with that driver I wont have to worry about moving stuff all around between everything. Also what Are your suggestions on how I should back up my data? Also what about the idea of having ubuntu on an external hard drive?

---

### Post by MillerD on 2008-08-12
What if I were to have like a 200 GB usb HDD, could I like part it into 2 parts, 1 will have liek soem windows stuff like a back up while the other will have ubuntu installed, what about that?

---

### Post by Pumalite on 2008-08-12
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

