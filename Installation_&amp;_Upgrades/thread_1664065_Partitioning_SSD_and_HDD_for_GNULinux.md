---
title: "Partitioning SSD and HDD for GNU/Linux"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by coldcut on 2011-01-10
Hi guys

I don't know if this thread is in the right place, I had a hard time finding the right subforum, but here it goes. If admin's think this is not the right place it would be nice if they could move it for me.

I was wondering what would be the best partitioning scheme for my new build that I will be purchasing in a few days.
The build will include a 40-60GB SSD and a 1.5 TB HDD.

My plan was to arrange the partitions so that my SSD would handle everything except my files.
I want the partitioning to be so that my programs will be on the SSD but my videos, music, school-related projects etc. will be on the 1.5 TB HDD.
I don't remember if the programs install into the /home folder or into some other "folder".

So if the default behaviour is that the programs install in the /home folder, how do I go about makin them not do that?

I hope I have made myself clear enough, you'll have to excuse if I haven't as english is not my first language.

Thanks in advance

---

### Post by coldcut on 2011-01-12
Only 61 views...I'm certain that someone out there has the answer or has at least thought about this! :)

---

### Post by coldcut on 2011-01-12
Sorry that I'm bumping this so soon.

Are installed programs stored in /usr/local like I read somewhere?

---

### Post by oldfred on 2011-01-13
Do you also have windows or any other operating system planned? 

I have installed lots of programs and my / (root) is only 6GB used out of 20GB. You may need another 4GB of tmp space if you write DVDs and I like to only use about 50% of root. I only keep my hidden folders & files that are user settings in /home so I do not use the separate /home but use a /data. My /home is less than 1GB but I even move hidden data folders like Firefox, Thunderbird, Kmymoney etc to my /data partition.

My standard recommendation for the Total space you want for Ubuntu, you may not want the /home:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

I would keep all the system partitions on the SSD so you can alway boot it. You may want to also have an install on your data drive. I have Ubuntu or windows installed on every drive and each drive can be booted independently.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by coldcut on 2011-01-13
> **oldfred said:**
> Do you also have windows or any other operating system planned? 

I have installed lots of programs and my / (root) is only 6GB used out of 20GB. You may need another 4GB of tmp space if you write DVDs and I like to only use about 50% of root. I only keep my hidden folders & files that are user settings in /home so I do not use the separate /home but use a /data. My /home is less than 1GB but I even move hidden data folders like Firefox, Thunderbird, Kmymoney etc to my /data partition.

My standard recommendation for the Total space you want for Ubuntu, you may not want the /home:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

I would keep all the system partitions on the SSD so you can alway boot it. You may want to also have an install on your data drive. I have Ubuntu or windows installed on every drive and each drive can be booted independently.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Thanks for a great answer! No I will not have a Winblows partition. This is a new build I'm putting together and it will consist of 4GB RAM, 1.5TB HDD and a 40-60GB SSD.
I want to put everything except the /home folder on the SSD so my computer will be as fast as possible ;)

---

### Post by oldfred on 2011-01-13
The /home has two uses - your user settings that control how all your software looks which your really should keep on the SSD (in hidden files & folders with .) and all your data folders like music, Documents etc. I would do like I did with /data and move the user data folders that you see but keep your hidden settings on the SSD.

There are several ways to mount your data partition. Since all my installs are Ubuntu the user id is always 1000, but other installs may not have the user id as 1000, so other ways of mounting /data may be better. I just mount it in /mnt/data and link all the data folders back into /home.

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
To mount all folders in one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by coldcut on 2011-01-31
Okay thanks olfred. 
Not sure I understand all of that, but it would be great if you could take the time to "draw" up a partition scheme for me. 
The SSD will be 60GB as I've said before and it doesn't all need to be allocated because I might want to have a tiny partition for OS-testing. So how would a partition scheme like that look?
Also I didn't quite understand what you were meaning about the /data partition. Do I have to move my user settings to the SSD or does it do so automatically if I allocate a /data partition.
As I've said I want all my programs on the SSD. Small user-files can be on the HDD because I always back them up for faster installation.

Hope you have time to help me.:tongue:

---

### Post by oldfred on 2011-02-01
With a 60GB SSD you have room for two 25GB root partitions and a small swap. Actual size will be somewhat less since GiB is not GB. I would put a small swap (but never hibernate) into the SSD. Swap will probably not be used, but system runs a little better if it does not have to search for swap and not find it. Some users with lots of memory run without swap or use a swap file in /.

I would just let it do the full install into the SSD. I would also create one or more 20 to 30GB partitions for / (root) on the 1.5TB drive. If that seems too large and you do not think you will ever use them for testing other installs then just do the small install like the link to knoppix recommendation (I use Ubuntu on every drive).


You create a separate data partition(s). and mount that with fstab so the data is availble. I have all my data folders from a default install like Music, Documents etc (I have 13 or 14 folders since I move some hidden data folder from /home also). I then use links to replace the default folders in /home with the ones from /data.

I do not like to have one large data partition. One it is harder to backup, but if you make it too small then you have to reorganize. Some suggest LVM, but it adds another level of complexity. I Just buy another drive.:)

I posted previously the exact commands I use to mount, add to fstab and link my data folders. See also links. Since I redo this for my portable and for every install, since I now do clean installs, I copied history into a bash file so I can semi-automate the process.

---

### Post by coldcut on 2011-02-02
Okay thanks olfred. I think I get what you're saying and I'm just gonna list how I imagine the partitioning.

SSD

/boot - 100MB
/ - 20GB (programs)
/home - 5GB (configuration and hidden files and folders)
empty - 20GB (for testing other OS'es)

HDD

/data - 1,496GB (all my files (music, videos, school-things))
swap - 4GB (at the end)


I hope I'm not understanding your advice wrong and I beg you not to get annoyed as english is not my language (my brother corrects my text) but if you could set up your preferred partition scheme considering my setup I would be most thankful.

On another note...would you advice partition alignment?

---

### Post by tarnall on 2011-02-02
I wonder if I can jump in here...I have a PC with Ubuntu OS.  If I had installed Win7 first I could have installed Ubuntu with a double boot, but I did not.

Is there any way I can install Win7 with Ubuntu already on the HDD? (choose the boot?)

Thanks, Terry, Hayward, CA - [email]terry.ubuntu@gmail.com[/email]

---

### Post by oldfred on 2011-02-02
Terry, please do not hijack a thread. You should start a new thread and many of us can help you. Yes, you can. You also can search forum or search forum with Google to find the answers. I have posted many times also your exact answer.
Google is often better than the forums search function.
Just append site:ubuntuforums.org to your search terms.

Coldcut,

Your (or your brothers) English is fine.

SSD
[COLOR=Red]
/boot - 100MB[/COLOR]  Delete this it just adds complications
/ - 20GB (programs)
swap - 2GB (memory overflow)
empty - 20GB (for testing other OS'es)

HDD

/ - 20GB  also future or another install just to be able to directly boot this drive without SSD.
/data - 1,496GB (all my files (music, videos, school-things))
swap - 4GB (at the end)

May be good to have swap on every drive.

You may not want all data in one huge partition as that may be harder to backup. But too many small partitions may make it difficult if one gets full and the other has lots of space. It is a trade off.

I have not partitioned a SSD and there are special rules for that. 
SSD info
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment#post373226)
[http://thunk.org/tytso/blog/category/computers/ssd/](http://thunk.org/tytso/blog/category/computers/ssd/)

Look at this users's partitioning:
kansasnoobs multiboot:
[http://ubuntuforums.org/showthread.php?t=1679088](http://ubuntuforums.org/showthread.php?t=1679088)

---

### Post by coldcut on 2011-02-03
Thank you so much for all your help olfred, this was just what I needed. Now I will be ready on saturday when I set up my new computer.

---

### Post by coldcut on 2011-02-06
Hi again olfred

I had tiny problems with your advice.

```
sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 auto,users,rw,relatime 0 2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic           [COLOR="Red"]**// this is where I went of track**[/COLOR]
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
To mount all folders in one command:
for i in `echo /mnt/data/*`;do ln -s $i; done
```

This did not work for me...I also followed this link you gave me: [http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

I'll just list my command history here and hopefully you'll see what to do next.

```
mkdir mydata
sudo fdisk -l
sudo mount /dev/sda2 /home/gisli/mydata
sudo chown -R gisli:gisli /home/gisli/mydata
sudo emacs /etc/fstab (I put the sda2 into the file)
sudo blkid
sudo emacs /etc/fstab (put the right UUID into the file)
```

after this I copied all my /home folders to the /data (mydata) partition. Now I just have to symlink/hard link my folders.
As you probably know I want to be able to access, for example, my Music folder in /mydata by just double clicking the Music folder in /home, and the same with all the other folders. But I don't want music/video/pictures files written to my SSD which has the /home folder.
Isn't this the best way or do you have a better solution.

Maybe all that I've done is bad...but I hope not :oops: Hope you can help me.

---

### Post by oldfred on 2011-02-06
Anytime I edit fstab I run this to make sure it is ok. If it just returns then it is ok, otherwise it posts errors.

sudo mount-a

I do my linking on all my new installs. So I delete my folders in /home including Music, Documents, etc. I used to  delete in 2 steps just in case I somehow already saved something. so I rename it with  mv command and then add all my links.

I did this all from command line the first time, then listed history & copied into a bash script.

from my script, I haved edited over time and used # to comment out my earlier version.

#mv Music oldMusic
#mv Documents oldDocuments
#mv Pictures oldPictures
#mv Videos oldVideos
#mv Downloads oldDownloads
Make sure these are empty before deleting. But, you cannot add links if they exist.
rm -rf Documents/
rm -rf Downloads/
rm -rf Music/
rm -rf Pictures/
rm -rf Videos/

#This one line does all the lines below that start with ln - links all folder from /home msut be run in /home as that then is default location of link (or second parameter must be added as location)
for i in `echo /mnt/data/*`;do ln -s $i; done
# I just link my windows shared into home
ln -s /mnt/shared

#Before I figured out the one line version above I did this 
#ln -s /usr/local/fred/data/Music
#ln -s /usr/local/fred/data/Documents
#ln -s /usr/local/fred/data/Downloads
#ln -s /usr/local/fred/data/Pictures
#ln -s /usr/local/fred/data/Videos
#ln -s /usr/local/fred/data/PDF
(I now have 13 or 14 folders as I have moved some data from hidden folders in /home or created more)

Try it with the individual lines for one or two of your folders. If it makes sense then try the automatic one. 
Run this and then copy to bash file for next install:
history

---

### Post by coldcut on 2011-02-16
Thank you so much olfred. Everything worked as a charm \\:D/

---

### Post by oldfred on 2011-02-16
Glad it worked. Happy Ubuntu-ing.

---

### Post by coldcut on 2011-02-17
Thank you...although I Ubuntu-ed for like 4 years (2005-2009) the SSD thing was kinda getting in my way :p But thanks to you...it's all good now!

---

### Post by Rulius on 2011-03-07
Hi guys,

I have a similar configuration as coldcut, 80Gb intel SSD and 1Tb WD mechanical. I found Oldfred's advice very helpful, but I have a question. Currently I'm running windows 7 in the SSD and have the mechanical for data storage. I want to install ubuntu on the mechanical so that I can also use it as a stand alone disk. I'm thinking - and correct me if I'm wrong - that I should stick with ntfs for the part of the disk where data will be stored, since I want to use this data with both windows and ubuntu. So my question is should I use the recommended above by oldfred configuration with the data partiton being ntfs or should I use the configuration: 

20 Gb: / (ubuntu, file system:ext4)
6GB ( this the ram I have): swap (file system: swap) ---- (Does it really have to be in the end of the disk?)
the rest(most likely in two partitions): data (file system: ntfs)

And one last thing: I partitioned my disk through the windows tool in three ntfs partitions - all looking good. When I used Gparted it showed me 1Mib unallocated in the beginning of the disk and 1Mib unallocated between the 2nd and 3rd partition. Should I bother with those?Are they important to keep for windows? If I was to use only windows or only ubuntu I wouldn't be confused, but I want to use this mechanical disk under both. I also plan to dual boot the SSD but I'm still working on that.

Thanks.

---

### Post by oldfred on 2011-03-07
I highly recommend a shared NTFS partition for sharing data between windows & Linux. I allow reading from foreign system partitions but do not write into them unless I have to make repairs. 

I also like each drive to have a system that has all of its boot files on the same drive including MBR. Then if the other drive fails I can still boot a drive. If system partitions are on more than one drive, any drive failure may prevent booting either drive.

If you have 6GB of RAM you may never use swap. Some run without it, I suggest having at least some. You do not want to use swap as it is very slow compared to RAM. Since you probably are not using it, then it does not matter where it is. And where it is on a drive barely makes any difference anyway.

The 1K boundaries are now because of SSDs & 4K drives. With LBA which has been used for years CHS rounding has not made sense. There always was some space at the beginning of a drive and usually between partitions with MBR. Now it is a little larger to round to 1K boundaries and now gparted shows it.

---

### Post by XBMC old School on 2011-03-09
Nice Thread Coldcut. Nice Input OldFred.

OldFred maybe you can make a Tutorial/discussion thread for this type setup?  With SSDs being good and cheap, it looks like it might be a common setup  +-Variation. With a designated Tut/discussion thread there is no  hijacking. Anyways.

Here is my proposed setup.
_Device      Type  Mount point    Format     Size_
/dev/sda                
/dev/sda1  ext4       /boot          Yes       512mb usb key

/dev/sdb                
/dev/sdb1  ext4       /                                      Yes          60GB SSD (LVM encrypted)
                
/dev/sdc                
/dev/sdc1  xfs    /home          Yes         2TB HDD (LVM Encrypted)
                
/dev/sdd                
/dev/sdd1    xfs                                                     Yes            2TB HDD  (SAMBA)  (LVM Encrypted)
                
/dev/sde                
/dev/sde1    xfs                                                      Yes           Old 1TB  (Backup) (LVM Encrypted)

* See signature for existing specs

Questions:

1) I intend to use the /dev/sdd drive as a samba share/back-up for a  Win7 laptop and XBMC(ATV). I read that the XFS is a performance format,  is it worth it or does it make for complications? Is it better to go  with NTFS or ext4?

2) I intend to have 3 accounts. 1-admin, 2-Parents (desktop user) and  3-Kids (desktop user). Does locating the /home folder on the SSD and  /data on the spinner complicate things with multiple user accounts?  Should i just set it the way I have it above? My goal is speed though. *Where is the /data folder located?*

3) Is my bios boot drive need to be set to the USBKey(/boot)? This is a Ubuntu machine only. I leave windows at the office.

Thanks if you respond. I'm a noob with some chops in ubuntu (exWindows power user).

XBMC OS

---

### Post by oldfred on 2011-03-09
If your goal is speed, I do not understand your LVM Encrypted settings. Those will reduce speed and it sounds like a home computer where security would not be a main concern.

I have seen several comparisons of different file formats on 
[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)
I do not have a specific link.
My general impression was ext4 was better overall, but not one system was best for all uses. Other formats may be better from some specific uses. But most repair tools seem to be orientated towards the standard ext family.

Why boot from USB key. Again is this security?

I do not have a multi-user system. My wife & I just use the same - fred.

Some links on data partition UID/GID settings.
Shared users using bindfs:
[http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)
HowTo: Create shared directory for local users (with bindfs). 
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

Some suggest a NTFS format. Then you have no permissions nor ownership. Mounting controls it.  But you need a windows repair disk to run chkdsk regularly. I only use NTFS for my windows shared data.

---

### Post by XBMC old School on 2011-03-16
Hey olfred,

I loaded Ubuntu 10.04.2 (64bit) via usb installer;

/dev/sda                
/dev/sda1  ext4          /                                      Yes 56GB SSD primary (OCZ Vertex II)
                /dev/sda2 Swap      Yes 4GB SSD 
/dev/sdb                
/dev/sdb1 ext4    /home          Yes         2TB HDD
                
I wanted to keep it simple. But the install finishes and hangs on the "loading software"

XBMC OS

---

### Post by oldfred on 2011-03-16
Has the install finished, or is it the install of grub to the MBR that is hanging up. 

Do you really want one partition that is 2TB? That is a lot to backup at one time. Of course partitions that are too small create management issues and reformating/editing partitions. There is no one right answer.

---

### Post by XBMC old School on 2011-03-16
It says the install (10.04.2 64bit) is complete and reboots. Then I guess it fails on loading into grub. I don't plan on dual booting. Can i skip installing grub?

I have an additional 2tb and 1tb drive as well. The important stuff i backup is only 3-400Gb, so I'm loaded with space.

Again, thank you for the fast response.

---

### Post by oldfred on 2011-03-16
You need grub2 or some boot loader that recognizes Ubuntu to boot Ubuntu. You can install different boot loaders in the MBR of each drive. Generally you want the boot loader for system installed in the drive in that drive's MBR. Grub2 will give you the choice to boot every system.

If you want to know what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

