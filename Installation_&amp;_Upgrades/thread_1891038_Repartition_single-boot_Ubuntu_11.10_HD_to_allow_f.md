---
title: "Repartition single-boot Ubuntu 11.10 HD to allow for Linux multi-boot set-up?"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by ts3 on 2011-12-04
I have single-boot Ubuntu on a new hp dm1 laptop with a 320GB hard drive & 4 GB RAM.  Love Linux & want to try other distributions so figured now is the time to re-partition to allow for future installs.

The current set-up is the one created by default during the Ubuntu install (it's in a thumbnail at the end of the post, no idea how to embed images, sorry!) 

I read up on partitioning for multi-boot systems and have an idea what I want but will appreciate some specific advice on what the set-up should look like.  I want Ubuntu as the first system with say a 15GB / partition and then two empty 15GB / partitions for two other distributions (I figure by the time I want to run more than three distros I will know how to re-partition :) ) 

Obviously there should still be a swap partition but I wonder whether I should leave the size as it is or increase as I plan to buy more RAM eventually.  I understand swap partition size is a matter of some controversy :) This will leave me with at least about 245 GB of empty space and I wonder how to allocate that.  Currently I am not too worried about sharing data between different distros so I was thinking of either just allocating the 245GB to Ubuntu (how?) or giving 200 GB to Ubuntu and setting 45 GB as a shared partition (/data? but again, how does that work exactly?)

I did read some excellent guides and posts so I have a rough idea of how things work; problem is that a lot of the examples and guides are for dual-boot systems with Windows or for grub legacy, neither of which apply here.

Some step-by-step suggestions or, even better, screen shots of actual partitioning schemes with multi-boot Linux will be greatly appreciated.  Of course, if there are posts that address exactly this issue please point me in that direction.  Also, please let me know if I should post more detailed info about the system.  Thanks from a new Linux convert :)

---

### Post by drs305 on 2011-12-04
Just a few basic points.

Your Linux installs can be in extended, logical partitions. They don't have to be on a Primary partition. If you think you may ever entertain the possibility of installing Windows, you might want to leave unallocated space in a primary partition for it. The latest Windows may not have to be on a Primary partition, but it would be worth checking.

You only need 1 swap partition, which can be shared by all the Linux installations.

You might want to check your BIOS on boot to ensure it sees the entire drive. Some BIOS's only 'see' the first 137GB of your drive. If that is your case, just keep it in mind: your entire OS should be contained in the first 135GB or so, or keep the controlling Grub in an installation within that area.

I have a lot of 20GB partitions for installing various Ubuntu releases (and others). I have one on a primary partition, another primary partition as 'reserve' should I ever need a primary partition for something, and everything else in logical partitions (including swap).

If you are really adventurous, you might consider using one of the newer partitioning setups such as GPT, etc.

Gparted does a great job shifting Linux partitions around, so nothing is really etched in stone. Back up critical data, and have fun.

---

### Post by ts3 on 2011-12-04
That was very fast, thank you!  To answer some of the points you raised: I'm hoping to avoid Windows entirely on this laptop.  I made a Win7 recovery USB before installing Ubuntu so I figure I can try out a VM if worse comes to worse.  I also have an old laptop that dual boots XP and Ubuntu, and that should tide me over till 2014 when XP support ends :)  

I took a peek at the BIOS but couldn't figure out how much of the HD it sees; will have to look into it a bit more.  Ubuntu should have the controlling grub: from what I read chainloading is the way to go but I'm not clear how to do that yet; guess I'll figure it out once I actually start installing other distributions.

Googling GPT as we speak: I might try something like this a bit further down the road; just the idea of re-partitioning a hard drive is heady stuff for a newbie like me.

>  I have a lot of 20GB partitions for installing various Ubuntu releases  (and others). I have one on a primary partition, another primary  partition as 'reserve' should I ever need a primary partition for  something, and everything else in logical partitions (including swa). That's roughly what I'd like to achieve, if I can figure out how :)  Perhaps keep Ubuntu on a primary partition (now it is on one, dev/sda1) but I also want it to have a separate / partition to allow for clean re-installs.  This is the one that should have grub2 and that is flagged "boot" in Gparted, I gather.  So I'm thinking that I should shrink dev/sda1 to say 20GB and then create a new primary partition, dev/sda3, say 200GB, for Ubuntu to keep papers, music, etc.?  One would be / and one would be /home but how do I actually do this? Is this what the mount point refers to? (Sorry, complete newb here!)  

Then I can add more space to the dev/sda/2 (the extended partition), keep the swap in sda5 and add sda6 and sda7 logical partitions of say 20Gb each, mark them as root and use them for other distributions.  This should leave around 40GB for an sda8 to that be shared between distros if I can figure out how that works.

Are there any obvious flaws with this plan?  I have very little data as yet so I reckon in a worst case scenario I'll do a new Ubuntu install from scratch unless of course I screw something up royally and make the laptop completely unusable :)

---

### Post by drs305 on 2011-12-04
Installing an Ubuntu release is very easy. You just have to make the partition and then designate where it is in the installer (more later).

I don't use a separate /home partition since I like having all my data in a partition completely separate from my OS. This also makes is a bit easier for me to have totally independent OS's and a shared data partition.

But many users have separate /home partitions so when they upgrade they can keep their customizations. 

If you want a separate /home partition, here is how I would use gparted to set it up. It's just one way, and others have different ideas.

* Primary partition, 15-20GB, for /  (sda1)
By the way, every Linux installation has its own / (root).

* Primary swap partition (depends on your RAM), normally 2-4GB. (sda2)

Extended partiton with all the rest of the space.

** /home  First logical partition. (sda5 - the logical partitions start with 5).
The size depends on whether your data will be stored here.

** DATA partition (Data, music, video, etc) My preference, maybe not yours. (sda6)

** Other OS #1  20GB
The rest can remain unallocated until you decide to add a new 20GB partition for another OS.

Partitioning. 
There are plenty of good partitioning and Gparted howto's. Generally you need to use a LiveCD/USB/recoveryCD because the partitions cannot be resized while mounted.

Installing.
My advice is to make the partitions before you install. Initially, you will need a primary for your OS and a small swap partition. 

When you install the OS, you select "Choose something else" or something like that to take you to the manual partitioner. Don't let Ubuntu do it for you.

Select your partition from the graphic, click the mount point dropdown menu and choose / for your Ubuntu OS partition or 'swap' for the swap partition, tick 'format' the partition if you don't have anything on it you want saved.

Again, there are good installation guides on the Net.

Note 1: On subsequent installations, you won't need to designate the /swap partition. Ubuntu will see one already exists and use it.

Note 2. Each OS will try to install it's own bootloader. Grub 2 is very good and can handle almost all of them. If you have the opportunity, I would try not to install a second OS's bootloader if this is possible, With Ubuntu, you currently don't really have a choice. After installing, you just have to change back to your original OS. But that's for another thread...  ;-)

---

### Post by ts3 on 2011-12-05
[FONT=Verdana]DRS305, thanks again for the detailed advice :)  

I did some experimenting last night with Gparted and managed to repartition on top of the existing 11.10 install, without damaging it (I think).  I shrunk the large primary partition and then repartitioned with the following result: 11.10 on a 20GB primary, a 4GB primary swap partition (I am not sure that Ubuntu is actually using it, don't know yet how to check); an extended partition (sda3) with an empty logical partition sda5 (200GB for data) and another empty logical partition sda6 (20GB for future installs).  

So far so good and again, thanks for the advice. 

A few notes to self: 
[/FONT]
[LIST]
[*][FONT=Verdana]Don't forget to right click on the swap partition & click on swapoff while in the main install, before booting Gparted on a live USB, saves a reboot or two :)[/FONT]
[*][FONT=Verdana]I still don't know if the BIOS sees beyond 137GB: rummaged around the BIOS a bit more and still could not see anything HD-related which is rather strange;  [/FONT]
[*][FONT=Verdana]Upon re-boot the screen said that a partition was unmounted & gave me a few choices; I picked Manual & mounted the swap later manually [/FONT]
[*][FONT=Verdana]The default format in Gparted is ext2: do not forget to change to ext4 [/FONT]
[/LIST]
[FONT=Verdana]
I can see the 200GB and 20GB under Devices in the file manager, both mounted; for some reason the directories for each are /media followed by a long alpha-numeric string (UUID?); I can't put anything in the big data partition (no permissions) so next step is reading up on how to create the permissions.  

One more thing: I thought I'd try another version of Ubuntu and made a live USB with Ubuntu 10.04 but it would not boot at all, even from the USB, let alone install: got a black screen with error messages and the line "boot:" reappearing every so often. No idea whether this had anything to do with the new set up or if there was something wrong with the USB. Will try again.  

All in all, ended up with mixed results - the partitions are there, now have to figure out how to use them.  If anyone wants to chime in & tell me what I did wrong and how to fix it please feel free :)[/FONT]

---

### Post by oldfred on 2011-12-06
You need to understand ownership, permissions and mounting. You can manually mount or permanently mount by adding entries to fstab.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

A 777 means everyone and his brother can read, write & execute. Most may think that is too permissive.

Your /home is somewhat permissive:
Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access]("https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access")

I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 777 /mnt/data

# Make permanent mount point (unmount if already mounted) use what ever name you want:

mkdir /mnt/data
chown $USER:$USER /mnt/data
chmod 777 /mnt/data
# Find your UUID:
sudo blkid

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Example of an fstab entry use your UUID & mount  use ext3 or ext4 depending on format:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2

# Anytime you edit fstab always do this before rebooting. If no errors  it just remounts everything, but if errors you have to fix before  rebooting or you may not be able to:
sudo mount -a

---

### Post by ts3 on 2011-12-06
Oldfred, thank you for the great explanation and the links :) I'd found some of them earlier and now am printing from the rest to add to the reading list.  

Yesterday I took a look at etc/fstab and from what I could understand it's a small miracle that anything at all mounts on the laptop right now.

I plan to mark this thread as solved and again, many thanks to both of you for the help.  I'd also like to keep posting here as I figure things out and perhaps end up with a roadmap to setting things up just right :)

P.S. I'll probably go with more permissive rather than restrictive settings, at least to start with; as the only user on that particular laptop I reckon that should work until I get more familiar with the system.

---

### Post by ts3 on 2011-12-17
Finally got around to sorting out the mounting and permissions for the new partitions and it worked.  Thank you guys again for the great feedback and advice.  

As mentioned earlier, I repartitioned the hard drive following pretty closely drs305's advice and ended up with a 20 GB partition with the current Ubuntu install, a 4GB swap partition, a 200GB logical partition for data and a spare 20GB partition for other OS installs; this left me with around 60GB to spare.  I couldn't access the new partitions though so I had empty 200GB just sitting there and a 20GB install that was filling up pretty quickly.

I printed the info from the links from oldfred's post above and spent some time reading so that helped :)  The /etc/fstab file is really useful and from it it was clear that the new swap was not mounted and neither were the two logical partitions (which we knew anyway).

First I thought I'd try the GUI tool, pysdm, to mount the swap partition but that did not work at all.  It insisted on mounting swap on /media/sda2 which is plainly wrong, swap partitions have no mount point as far as I understand.  It was also using the name of the partition, say sda5, rather than label or UUID, which works but is not best practice.

Second, I mounted the partitions manually as follows:
 a) got the UUIDs by using [FONT=Courier New]sudo blkid[/FONT]

b) made the mount points with 
[FONT=Courier New]sudo mkdir /mnt/data[/FONT] for the big partition
[FONT=Courier New]sudo mkdir /mnt/somethingelse[/FONT] for the 20GB

c) [FONT=Courier New]gksudo gedit /etc/fstab[/FONT] to open /etc/fstab with root privileges then added the lines for the three partitions I wanted to mount (root was already there with the right options); I also deleted the entries for sda2, sda5 and sda6 made by pysdm

UUID=longnumberwithletters  none  swap sw 0 0 for the swap partition
UUID=anotherlongnumberetc  /mnt/data   ext4  auto,users,rw,relatime  0  2 for the big data partition
UUID=yetanotherlongnumberetc /mnt/somethingelse  ext4 auto,users,rw,relatime 0 2 for the smaller partition

For the options I basically used what oldfred gave me in the post above, except I have ext4 rather than ext3.  
 
d) [FONT=Courier New]sudo mount -a[/FONT] to make sure it works

Re-opening the /etc/fstab file showed the partitions as they should be but it also showed the original entries created by pysdm (e.g. sda5  /media/sda5 defaults) that I had deleted when making my entries.  However, after I rebooted those disappeared so it's all good :)  Also, before rebooting the system would not mount a USB flash drive, but this worked after the reboot as well.

The file manager showed the partitions where they should be, filesystem -> mnt.

Third, I changed the ownership for the partitions, as they were still owned by root and completely unaccessible.  These instructions are for a computer with one user which is its own group as well, for multiple users it might be slightly different.

a) confirm the user name just in case :)
[FONT=Courier New]echo $USER[/FONT]

b) [FONT=Courier New]sudo chown username:username /mnt/data[/FONT]
then repeat for the other partition

c) wait a bit, then open the file manager to /mnt/data and go to File -> Properties then to the Permissions tab: the owner/user should be able to create and delete files and the group able to create files, the Allow executing file as program box is unchecked (before all the entries were greyed out and root was owner).  

I could put in and take out files from the partition already but I decided to run the chmod command for good measure as well.  

So, fourth,

[FONT=Courier New]sudo chmod -R a+rwX /mnt/data[/FONT] 

which added rw and execute for executable files only (hence, the capital X); in the Permissions tab, as expected, others also got create and delete access; the Allow executing file as program box remained unchecked, as it should be, I reckon.

Anyway, I am not sure how changing the permissions allowed me to do more than I could already do after changing the ownership, apart from adding permissions for "others" (because of the "a" in "a+rwX).  I am the only user for this laptop so I am not particularly concerned with permissions for group and others, although I am considering changing the permissions to slightly less permissive with

[FONT=Courier New]sudo chmod -R 755 /mnt/data[/FONT] 

This I reckon will allow group and others only to look but not touch :)

The other way to do the same with letters would probably be

[FONT=Courier New]sudo chmod go-w /mnt/data[/FONT] 

to remove the write permission for group/others and leave only the read and execute (which should be the equivalent to the two 5s above in octal notation).

Fifth, and last, I fixed the hibernation, to finish on a high note:

a) [FONT=Courier New]cat /etc/initramfs-tools/conf.d/resume[/FONT] 
to check the contents of the file that controls the hibernation/waking up process

b) [FONT=Courier New]cat /etc/fstab | grep swap[/FONT] 
to grab the UUID for the swap partition

c) the UUID in the resume file was different (I reckon it was for the first swap partition that Ubuntu created before I re-partitioned); so 

d) [FONT=Courier New]gksudo gedit /etc/initramfs-tools/conf.d/resume[/FONT]

then deleted the old UUID and pasted the correct UUID for the swap partition

Worked like a charm, the laptop goes to sleep and wakes up beautifully, just as it did right after install, before I started fiddling with partitions.

Sorry about the long post.  Everything I did was based on the posts and links above, so thank you again.  What helps me most is seeing examples of what other people have done with their systems, on top of the wikis and guides which outline the theory.  So perhaps this wordy post might help someone else; plus I'll be referring to this the next time I mess with partitions.

Cheers :)  and onwards to figuring out the graphics driver, which is next on the to-do list :confused:

---

### Post by oldfred on 2011-12-17
Glad that worked.

I purposely mount in /mnt/data so my data partition(s) do not show in Naulitus without having to drill down. But I link folders from that into /home so I have easy access to those folders. Some are the standard Ubuntu folders like Music & Documents that I replace.

I like to use links, others modify the entries in fstab to use bindfs. There are some advantages to the bindfs method, but if using only Debian based systems the links work just fine.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by ts3 on 2011-12-18
> **oldfred said:**
> Glad that worked.

I purposely mount in /mnt/data so my data partition(s) do not show in Naulitus without having to drill down. But I link folders from that into /home so I have easy access to those folders. Some are the standard Ubuntu folders like Music & Documents that I replace.

I like to use links, others modify the entries in fstab to use bindfs. There are some advantages to the bindfs method, but if using only Debian based systems the links work just fine.

Thank you, that's brilliant and very timely, I was just starting to wonder if there was an easier way to access the /mnt/data folder without having to click down multiple levels.  The links are printing as we speak so there'll be a bit more reading to do over the next few days.

Cheers :)

---

### Post by ts3 on 2011-12-27
The system is finally up and running the way I want it to, more or less.  Thanks again for the posts with advice and links :)

I read the links from the post above and also, completely by accident, came across this recent thread

[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

where Morbius1 explains the use of bind (rather than bindfs) and offers a short tutorial.

So I created new directories in /mnt/data/ as follows:

```
 sudo mkdir /mnt/data/Documents /mnt/data/Pictures /mnt/data/Music /mnt/data/Videos 
```

Then 

```
 sudo mount --bind /mnt/data/Documents /home/myusername/Documents 
```

then rinse and repeat for Pictures, Music and Videos

Important caveat - move out stuff from /home/myusername/Documents, Music etc BEFORE performing --bind because the files will disappear afterwards.  I had already made copies of my files from /home to /mnt/data earlier and then just moved the files to their respective subdirectories (docs, pictures, etc); the original files in /home/myusername/Documents were nowhere to be found after --bind.

It has been working so far.  I also want to experiment with linking but haven't gotten around to this yet.

Finally, I installed Ubuntu 10.04 LTS in the 20GB partition and it is working as well.  I can access and save data to the /mnt/data partition from there so am pleased as punch.  

Next step: format some of the unallocated space at the end of the hard drive and install something adventurous but not drastic (I do not feel up to installing arch linux just yet).  Suggestions for other distributions to try out are welcome :)

---

### Post by ts3 on 2012-01-02
A few more notes on partitioning & multi-boot:  finally got around to partitioning the unallocated 60GB at the end of the hard disk and found out that (a) you can only have 4 primary partitions (knew that) and (b) only one of those partitions can be extended (the implications of that had not registered properly for some reason).  The end result being that I could not split the 60GB further; I probably could've added them to the extended partition and created more logical partitions but decided not to muck around with something that's working.  So ended up formatting the 60GB as the last primary partition (sda4), mounting and setting permissions as above and installing Mint 12 to try out.  For this partition I set the permissions as 755 and that seemed to work. 

Also went back and changed the permissions for /mnt/data and mnt/othersystems to 755 and no problems so far.  After installing 10.04 and Mint the ownership of both reverted to root rather than mysername, the permissions stayed as I had set them.

A few notes to self for next time I start from scratch:

[LIST=1]
[*]Update the BIOS before deleting Windows 7
[*]Create 3 primary partitions (say 20GB, 20GB and 4 to 8 GB for swap) and make the rest one extended with one large logical partition for data and several smaller, say 20GB each, for other OSs)
[*]Set permission as 755 from the start
[*]Don't forget to make the bind permanent
[/LIST]

So far so good, really liking the way Ubuntu, and Linux in general, work.  The flexibility is amazing and I'm still slightly power-drunk from learning to use the terminal.  Found a few books and a few online courses to look into :)

Cheers and thanks for the help again.  Hope this thread might be useful to other people; I definitely plan to use it for future reference.

---

### Post by oldfred on 2012-01-02
Glad it is working.:)

---

