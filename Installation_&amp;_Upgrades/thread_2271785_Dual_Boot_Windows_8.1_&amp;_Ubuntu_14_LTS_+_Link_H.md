---
title: "Dual Boot Windows 8.1 &amp; Ubuntu 14 LTS + Link Home folders to Data partition"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by rishav2 on 2015-04-01
Still fairly new to the linux scene but I have a pretty old laptop with none of the UEFI problems that plagues more modern laptops. Note, I have disabled all fastboot/hibernate options form Windows 8.1 as required. Previously, I've set it up with an 70GB Windows 8.1 primary partition, along with a 20GB / root partition, 4GB (my ram size) swap area, 80GB for /home partition, and the rest allocated to a NTFS data partition which both Windows and Ubuntu 14.04.2 LTS could access. This had worked well enough but the main problems was overlap of the /home and data partitions which served mostly for the same use of storing documents & media while I would have to manually mount the Data partition every time (I've read that this can be resolved but not entirely sure about the process). It's easy enough in Windows to redirect all the main folders found in the libraries to read and save to the Data partition 

Hence, soon after, I did a full wipe of my laptop to start completely afresh with Windows and all. Currently, I'm at 350MB System Reserved and 60GB NTFS Windows 8.1 partitions while the rest is unallocated space. Not extended partitions or anything: just unallocated space so I have full freedom to work with it as seen in the screenshot from Disk Management below.

[ATTACH=CONFIG]261026[/ATTACH]

So this is where I could really do with you help; how can I go about back to dual-booting Windows with Ubuntu in such a way so I no longer face my previously problems: Windows' libraries and Ubuntu's home reads & writes to the same Data partition without manually remounting upon each boot. Furthermore, this is where I'm really getting out of my depth, can I triple boot by adding Xubuntu 14.04.2 LTS to top it all of? Can Xubuntu use the same swap area & home partition as Ubuntu? Honestly, I would like to check how my usual browsing habits impact both of the Ub/Xub performances then decide to stick with one.

---

### Post by oldfred on 2015-04-01
When I still had XP on one drive and Ubuntu on another I created two shared partitions. Anything I wanted in both Ubuntu & Windows was in my shared NTFS data partition including my Thunderbird & Firefox profiles. And then I had a shared Linux data partition for other data. Now without XP I have obsoleted the NTFS shared partition.

You do want to create a mount point and permanently mount using fstab, so Ubuntu automatically finds everything in the same place as soon as you reboot.

You can share swap if not hibernating, otherwise one install will overwrite the other installs hibernation. Best not to use /home as some settings may conflict.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformatting a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by rishav2 on 2015-04-01
> **oldfred said:**
> You do want to create a mount point and permanently mount using fstab, so Ubuntu automatically finds everything in the same place as soon as you reboot.

You can share swap if not hibernating, otherwise one install will overwrite the other installs hibernation. Best not to use /home as some settings may conflict.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformatting a /home partition accidentally. I never reformat my /data and just configure / for install.


Many thanks for your prompt reply, really appreciate it. If you don't mind too much, I had a few more questions regarding the best way to go about it all:

1. During the install, should I choose "Something else" for the install directly and assign the partitions as such on my single 500GB HDD:
- (350MB System Reserved Windows).
- (60GB Windows Primary Partition).
- 20GB Primary Ext4 mounted at / (root)
- 4GB Primary swap area.
- Where or how would I select /data partition, its format, and its mount point?

2. Do I need to add /home partition to the above list or would the 20GB / (root) cover it? If I do need to add /home, would its function not overlap with that of /data? Maybe I'm not appreciating the difference between the two and how they play with Windows.

3. What is /mnt and is it important for this dual-booting to go seamlessly? I've been reading through the links you shared and this came up quite often as well as symlinks which I'll have to get round to once I get Ubuntu 14 LTS all set up in the first place.

Again, many thanks for your help.

---

### Post by oldfred on 2015-04-01
A data partition is not a standard install option. So either leave room during install or partition in advance with all the partitions you want. You still have to use Something Else and manually edit fstab with mount. If dual booting with Windows better to have a separate NTFS data partition, but Windows 8 does not seem to have a way to unmount extra partitions, so you must have the fast boot or always on hibernation off. You can set Windows system partition as read only and the data partition as read/write. Or not mount Windows system at all. Windows cannot easily read Linux partitions. You have to add third party drivers and most really only work as read only. Windows does not know about Linux ownership & permissions. So Windows cannot use Ubuntu's /home. 

Not even sure if still the case. But /mnt is not seen in Nautilus except by opening system and drilling down to /mnt then /mnt/data. If in /media which newer Ubuntu is now /media/$USER where $USER is your name are mounted in Nautilus so only you have permissions). And if you add to fstab it used to add it a second time with an underscore and that mount would not work often confusing users as underscore was not obvious.
There are many discussions over the official or best place to mount and I do not think there really is a correct answer for a home user.

I keep /home inside my /. I normally allocate 25GB and currently use 11GB of /. And about 2GB of that is my /home which most of is .wine for Picasa. But everything else that starts to have any amount of data is moved to /mnt/data folder and linked back or profile edited to find correct location. A standard /home has your user settings for everything you install, and in many cases some data. I find my /home without .wine and without Firefox & Thunderbird profiles is only 250MB, but that may depend on apps and where default data is stored.

---

### Post by rishav2 on 2015-04-02
> **oldfred said:**
> A data partition is not a standard install option. So either leave room during install or partition in advance with all the partitions you want. You still have to use Something Else and manually edit fstab with mount. If dual booting with Windows better to have a separate NTFS data partition, but Windows 8 does not seem to have a way to unmount extra partitions, so you must have the fast boot or always on hibernation off. You can set Windows system partition as read only and the data partition as read/write. Or not mount Windows system at all. Windows cannot easily read Linux partitions. You have to add third party drivers and most really only work as read only. Windows does not know about Linux ownership & permissions. So Windows cannot use Ubuntu's /home. 

Not even sure if still the case. But /mnt is not seen in Nautilus except by opening system and drilling down to /mnt then /mnt/data. If in /media which newer Ubuntu is now /media/$USER where $USER is your name are mounted in Nautilus so only you have permissions). And if you add to fstab it used to add it a second time with an underscore and that mount would not work often confusing users as underscore was not obvious.
There are many discussions over the official or best place to mount and I do not think there really is a correct answer for a home user.

I keep /home inside my /. I normally allocate 25GB and currently use 11GB of /. And about 2GB of that is my /home which most of is .wine for Picasa. But everything else that starts to have any amount of data is moved to /mnt/data folder and linked back or profile edited to find correct location. A standard /home has your user settings for everything you install, and in many cases some data. I find my /home without .wine and without Firefox & Thunderbird profiles is only 250MB, but that may depend on apps and where default data is stored.

- How did you create /home under / (root)? I don't see this as an option when installing Ubuntu, instead I can create /home in /dev/sda# depending on partition number.
- If I create a NTFS formatted Data partition using Windows' Disk Management as a Simple Volume, would that be available to Ubuntu through /mnt/data be sufficient to create symlinks to from /home folders like Documents and Downloads?
- How would I go about not mounting Windows in the first place while setting read-write permission on the Data partition?
- If I were to have multiple Ubuntu installations (eg. Ubuntu, Xubuntu, Voyager), I assume I would have to assign them each about 20GB / (root) and another 20GB or less /home partitions while they can all share the 4GB swap area and save any actual data (documents, downloads etc) to the separate Data partition? I understand Voyager is not an official Ubuntu flavour but is based Xubuntu, I believe.

I can't emphasise enough how much I appreciate your efforts to educate me on the ways of Linux, huge thanks.

---

### Post by oldfred on 2015-04-02
Standard install is just / & swap or /home is inside / partition. And because I have lots of test installs, I make sure all data is in my data partition. So then /home in / is tiny except for my .wine which I understand is more difficult to move. Then I only have multiple / partitions for each install and one large data partition for all data. When still using XP some data was ine NTFS and some in my Linux formatted partition.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

You have to be careful using Windows to create partitions. It does not normally use the extended partition and logical partitions, but converts to dynamic partitions and there is no undo by Windows. And dynamic does not work with Linux or even some Windows tools.


 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only. Better to use UUID example, not device like sda1.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

---

### Post by rishav2 on 2015-04-02
> **oldfred said:**
> Standard install is just / & swap or /home is inside / partition. And because I have lots of test installs, I make sure all data is in my data partition. So then /home in / is tiny except for my .wine which I understand is more difficult to move. Then I only have multiple / partitions for each install and one large data partition for all data. When still using XP some data was ine NTFS and some in my Linux formatted partition.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

You have to be careful using Windows to create partitions. It does not normally use the extended partition and logical partitions, but converts to dynamic partitions and there is no undo by Windows. And dynamic does not work with Linux or even some Windows tools.


 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only. Better to use UUID example, not device like sda1.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0


That is brilliant, thanks. For some reason, I completely missed that /home is already under / (root). Just two more questions and I think I'll be set to put everything I learnt into practice:

- Each Ubuntu install will need their own / (root) and /home partitions? And these partitions will be all primary (as opposed to logical)? I think 20GB for / (root) and 10GB for /home will be more than enough, but please correct me if I'm wrong.
- What should the formatting in the Data partition be? NTFS and primary or logical or something else?

Hopefully, this concludes my questions for a long while! Still can't thank you enough for your time.

---

### Post by oldfred on 2015-04-02
Windows is the one that requires primary partitions with MBR(msdos) partitioning. And that actually is only for the bootable copy of Windows, but if more than one Windows better that all are primary.
And you have a 4 primary partition limit, so 4th primary must be the extended partition which then can have an unlimited number of logical partitions.
I prefered to have have Windows on its MBR drive, but have Ubuntu on its own drive so I could use the newer slightly better gpt partitioning. But Windows only boots from gpt with UEFI which is on all newer hardware. Ubuntu can boot with BIOS or UEFI from gpt partitioned drive.

If you want a separate /home partition then each install should have one, or your main working install could have one, but test or experiment installs not have one. And all installs can be configured to mount the data partition(s). 
I was doing enough test installs and realized I was doing the same reconfiguration every time. So I tried to do as much from command line as I could and copied history into a text file and converted it to a bash script. Semi-auto install configuration. :)

If only giving 20 to / and 10 to /home, it just is easier to have one 30GB /. Then if one grows faster than the other you do not have to reconfigure partitions. 

Windows reads logical NTFS partitions so if dual booting with Windows a NTFS data partition is usually a good idea.

Partitioning, configuration and systems you install all are personal and each user may have different requirements. In fact my own optimal configuration a year or two later is not so good. But by then its a new hard drive (I do not trust older drives for daily use) and I reconfigure anyway.

---

### Post by rishav2 on 2015-04-03
> **oldfred said:**
> Windows is the one that requires primary partitions with MBR(msdos) partitioning. And that actually is only for the bootable copy of Windows, but if more than one Windows better that all are primary.
And you have a 4 primary partition limit, so 4th primary must be the extended partition which then can have an unlimited number of logical partitions.
I prefered to have have Windows on its MBR drive, but have Ubuntu on its own drive so I could use the newer slightly better gpt partitioning. But Windows only boots from gpt with UEFI which is on all newer hardware. Ubuntu can boot with BIOS or UEFI from gpt partitioned drive.

If you want a separate /home partition then each install should have one, or your main working install could have one, but test or experiment installs not have one. And all installs can be configured to mount the data partition(s). 
I was doing enough test installs and realized I was doing the same reconfiguration every time. So I tried to do as much from command line as I could and copied history into a text file and converted it to a bash script. Semi-auto install configuration. :)

If only giving 20 to / and 10 to /home, it just is easier to have one 30GB /. Then if one grows faster than the other you do not have to reconfigure partitions. 

Windows reads logical NTFS partitions so if dual booting with Windows a NTFS data partition is usually a good idea.

Partitioning, configuration and systems you install all are personal and each user may have different requirements. In fact my own optimal configuration a year or two later is not so good. But by then its a new hard drive (I do not trust older drives for daily use) and I reconfigure anyway.

Righto, that tip on the 4 primary partitions limit and extended partitions were ideal for me to do some solid reading upon. With all that said and done, please see the screenshots below describing my partitions set-up.

GParted:
[ATTACH=CONFIG]261066[/ATTACH]

Ubuntu installation:
[ATTACH=CONFIG]261065[/ATTACH]

To put it into words:
- sda1        NTFS           System Reserved      - 350MB
- sda2        NTFS           Windows 8.1 install   - 60GB
- sda3        NTFS           Data storage             - 200GB
- sda4/5?   EXTENDED   Extended partitions    - 205.42GB
    - sda5      LINUX-SWAP   Swap                           - 4GB
    - sda6      EXT4               Ubuntu install / (root)   - 30GB

The only slightly worrying part is that GParted refers to extended as sda4 while Ubuntu installation assigns that label to linux-swap and does not show any signs of partitions being extended at all. Is this normal?

Here is the final screenshot before the point of no return:
[ATTACH=CONFIG]261067[/ATTACH]

Am I set for the go ahead then? Any final changes I should make? When I want to install another version of Ubuntu, would I just create another logical / (root) partition for it under the extended partitions and be done with it all?

---

### Post by oldfred on 2015-04-03
Looks ok.
And the installer is saying swap is sda5 & / sda6. The format of / is ext4.

I usually make swap the last partition as it is one that will not get moved around. If somewhere in middle it may later get in the way of moving/changing partitions.

---

### Post by rishav2 on 2015-04-03
> **oldfred said:**
> Looks ok.
And the installer is saying swap is sda5 & / sda6. The format of / is ext4.

I usually make swap the last partition as it is one that will not get moved around. If somewhere in middle it may later get in the way of moving/changing partitions.

Huge thanks for your help throughout. The laptop is now installing Ubuntu and I'll try to create the symlinks myself following the guidance links you shared. Will be marking this thread as solved.

---

### Post by rishav2 on 2015-04-03
> **oldfred said:**
> [FONT=arial]Looks ok.[/FONT]
[FONT=arial]You did not leave a lot of room inside the extended for another / ?[/FONT]
[FONT=arial]And the installer is saying swap is sda5 & / sda6. The format of / is ext4.[/FONT]

[FONT=arial]I usually make swap the last partition as it is one that will not get moved around. If somewhere in middle it may later get in the way of moving/changing partitions.[/FONT]

Hey oldfred,

I noticed that your original post mentioned that I didn't leave enough space inside of extended for additional / (root) of other Ubuntu installations before you redacted this statement. Here is the current view from GParted:

[ATTACH=CONFIG]261074[/ATTACH]

When I created the partitions, I distinctly remember allocating all remaining 205GB of free space to extended partition. However, I now see that it is only 34GB in size: the total size of the / (root) and swap of Ubuntu. I quite certain I didn't choose that in GParted or Ubuntu installation. Since you've amended your post since then, does it mean that this is normal and the expected behaviour? I imagine that I can follow up with other Ubuntu installations from a Live boot and allocate its / (root) under the existing extended partition just like the current Ubuntu?

---

### Post by oldfred on 2015-04-03
I missed that you had the remaining 200GB and when rechecked noticed it. You must have read post quickly.

You must expand extended partition first, then you can create as many logical partitions as you want in the unallocated space.

The little lock symbols show mounted partitions and if swap is mounted, then extended partition is mounted. So you have to use live installer & gparted from it to edit partitions. Live installer often mounts swap to speed things up, so you may have to unmount it or swap-off before you can edit the extended partition to expand it.

---

### Post by rishav2 on 2015-04-04
> **oldfred said:**
> I missed that you had the remaining 200GB and when rechecked noticed it. You must have read post quickly.

You must expand extended partition first, then you can create as many logical partitions as you want in the unallocated space.

The little lock symbols show mounted partitions and if swap is mounted, then extended partition is mounted. So you have to use live installer & gparted from it to edit partitions. Live installer often mounts swap to speed things up, so you may have to unmount it or swap-off before you can edit the extended partition to expand it.


Not that fast considering I've subscribed to this thread to be notified by email immediately, hence I received the original post you made... Wish I was Speedy Gonzales though!

In any case, I was playing around with burg bootloader to improve the aesthetics of the grub menu when I somehow managed to break in such a way that it was stuck with an old theme which looked worse than grub's one. Purging and re-installing didn't help and I'd only just installed Ubuntu so I threw caution to the wind and simply re-installed Ubuntu. This time round, I ensured everything was set as intended in GParted and the resultant screenshot it shown below:

[ATTACH=CONFIG]261096[/ATTACH]

All free space is now allocated to the extended partition for future Ubuntu installations. I decided on stationing linux-swap at the top of the partition as I figured the / (root) would follow below the previous installation (eg. 1. swap, 2. Ubuntu 14LTS, 3. Voyager, 4. etc) so the swap should never get in the way. Now, back to playing around with burg bootloader: hopefully, with better results. Once again, many thanks for your help and advice throughout.



Cheers.

---

### Post by oldfred on 2015-04-04
I do not recommend burg, it has not been maintained for a while.
Some with older installs have installed it and had it work, others have had major issues.

I am not in grub menu long enough to care what it looks like.

---

### Post by rishav2 on 2015-04-05
> **oldfred said:**
> I do not recommend burg, it has not been maintained for a while.
Some with older installs have installed it and had it work, others have had major issues.

I am not in grub menu long enough to care what it looks like.

No worries oldfred, when it initially broke down, I was still able to easily reinstate grub bootloader through the terminal. It's just that the 10 second wait can get pretty annoying when either of my OSs take about 20 to boot up. Furthermore, every now and then, I lend my laptop out to some who are somewhat technologically challenged (read: my family) who would freak out at the sight of the grub menu but can just about manage choosing between pretty pictures. 

Currently, it's set at 3 seconds delay and has a Windows 8 Metro theme for a more cohesive experience. Unfortunately, I can't figure out for the life of me how to change the resolution from 1024 x 768 to my laptop's 1366 x 768. Otherwise, it seems to be stable enough.

---

### Post by oldfred on 2015-04-05
Depends on video card/chip.
Some Intel chips requires a boot parameter with the correct size.

I always had to use nomodeset with my nVidia cards, you add any boot parameter the same way to test then you can make it permanent by editing grub.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Update:
 kernel 3.19 which is implemented with all needed intel graphic stuff
[http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951](http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951)

---

### Post by rishav2 on 2015-04-07
> **oldfred said:**
> Depends on video card/chip.
Some Intel chips requires a boot parameter with the correct size.

I always had to use nomodeset with my nVidia cards, you add any boot parameter the same way to test then you can make it permanent by editing grub.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Update:
 kernel 3.19 which is implemented with all needed intel graphic stuff
[http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951](http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951)

Hi Fred,

My laptop doesn't have any dedicated graphics card, just a really old Intel one whose name escapes me as I don't currently have access to my laptop. In any case, this isn't too big of a issue currently since I've chosen a dark, minimal theme where the lower resolution is not as apparent. Will come back to this, thought, at some point.

So I was looking at these posts in chronological order: [Link 1]("http://ubuntuforums.org/showthread.php?t=1734233&p=10698683#post10698683"), [link 2]("http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384"), and [link 3]("http://ubuntuforums.org/showthread.php?t=1901437&page=3&p=11602913#post11602913"). These were some of the links you shared when guiding me on how to connect my separate NTFS Data partition to the Ubuntu one (note: separate partitions, same drive). As an example, here are two folders I would like to be connected and my drive's UUIDs:

Under home:
[ATTACH=CONFIG]261155[/ATTACH]

Under data partition:
[ATTACH=CONFIG]261154[/ATTACH]

UUIDs:
[ATTACH=CONFIG]261156[/ATTACH]


How can I select Videos under home but be re-directed to the Videos under data partition? Can I edit this script of yours to fit:

sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 auto,users,rw,relatime 0 2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

If so, what should I change to accomplish what I set out above: link the default folders under home to their equivalents in the data partition?

Maybe I should re-title the thread...

---

### Post by oldfred on 2015-04-07
Backup or make sure current default folders are empty. I normally do this first thing so I do not have to backup or rename, just delete the standard Documents, Video, Music, etc folders.
And this one line script run from /home will link all the folders you have created in /mnt/data.
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done
If you mount at another location like /media/data or with a different mount point/name you have to change that.

If you just want one or two folders, you repeat this with each folder. Folder must exist in /data, so if first time with a data partition create those first.
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Videos oldVideos
# Videos then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data /Videos

You must have the data partition in your fstab so it is auto mounted when you reboot or you will have issues.

Afterwards, it should look like this:
fred@trusy-ar:/mnt/data$ ls -l
drwxrwxrwx  2 fred fred  4096 Nov 17  2011 Videos

fred@trusy-ar:~$ ls -l
Many other folders & links:
lrwxrwxrwx 1 fred fred    16 Sep 30  2014 Videos -> /mnt/data/Videos

If ownership is root, you can change it. Note -R is recursion and you do not run on any system partitions or you have to reinstall. Only on /home or a data partition.
 sudo chown -R $USER:$USER /home/$USER

---

### Post by rishav2 on 2015-05-04
> **oldfred said:**
> Backup or make sure current default folders are empty. I normally do this first thing so I do not have to backup or rename, just delete the standard Documents, Video, Music, etc folders.
And this one line script run from /home will link all the folders you have created in /mnt/data.
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done
If you mount at another location like /media/data or with a different mount point/name you have to change that.

If you just want one or two folders, you repeat this with each folder. Folder must exist in /data, so if first time with a data partition create those first.
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Videos oldVideos
# Videos then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Videos

You must have the data partition in your fstab so it is auto mounted when you reboot or you will have issues.

Afterwards, it should look like this:
fred@trusy-ar:/mnt/data$ ls -l
drwxrwxrwx  2 fred fred  4096 Nov 17  2011 Videos

fred@trusy-ar:~$ ls -l
Many other folders & links:
lrwxrwxrwx 1 fred fred    16 Sep 30  2014 Videos -> /mnt/data/Videos

If ownership is root, you can change it. Note -R is recursion and you do not run on any system partitions or you have to reinstall. Only on /home or a data partition.
 sudo chown -R $USER:$USER /home/$USER


Wee bit of a late update (if you count 3 weeks as a wee bit), but I finally managed to find some time to sit down and make some progress on what I had originally set out to achieve with the help of this thread. Things we've ticked off the check list: install Windows, create Data partition, install Ubuntu, and successfully dual-boot between the two. Recently, I managed to figure out how to mount the Data partition to the fstab so that it auto-mounts upon boot. For the sake of future-me who would appreciate the record of how I went about things:

```
sudo blkid                            // Make note of the Data partition's UUID number
sudo mkdir /media/Data                // Make new directory under Media so it shows up in Nautilus 
sudo cp /etc/fstab /etc/fstab.orig    // Take backup of original fstab
gksudo gedit /etc/fstab               // Open fstab in gedit and paste the following without quotes, making sure to edit the UUID appropriately
"UUID=XXXXXXXXXXXXXXXX  /media/Data  ntfs-3g  defaults,auto,uid=1000,gid=1000,umask=002  0 0"
sudo mount -a                         // To mount the partition and test the success of this operation
[Link to the Ubuntu community guide]("https://help.ubuntu.com/community/MountingWindowsPartitions#Manual_Configuration").
```

With that surprisingly easy procedure out of the way, there now remains the final hurdle of linking the default Ubuntu folders to their equivalent folders in the Data partition. I'll set the scene of what I want to achieve: I have a set of folders in the Data partition. These folders are called "Documents", "Pictures", "Downloads", "Music", etc, you get the idea. Now, on my Windows install, I've re-directed the default libraries to these folders in the Data partition. So, say, when I download any document, it gets saved directly to the "Downloads" folder in the Data partition. When I upload photos from my camera, they get saved directly to the "Pictures" folder in the Data partition. All user data gets saved directly to the Data partition so the System partition only consists of the essential programme files it needs function.

And, long story short, I want to achieve the same result on Ubuntu. If I were to click on "Documents" in the Nautilus sidebar, I'd like to land inside the "Documents" folder on the Data partition. Same for "Pictures" folder and some other folders of my choosing. For example, I might not want "Desktop" and "Videos" connected to their equivalent in the Data partition. Hence, I would prefer to connect the individual folders manually for the greatest control.

Now I'm trying to get my head around your last post and, honestly, I'm not too sure of how to go about it. Say if I wanted to connect the "Music" folders, would I type the following:

```
mv Music oldMusic
ln -s /media/Data/Music
```

Will be actively trying to resolve this over the next week so any help/guidance would not go amiss. Thanks again for sticking through.

---

### Post by oldfred on 2015-05-04
Looks like orginal post has a space missing before /Music.

S/B:
 # Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data /Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by rishav2 on 2015-06-13
> **oldfred said:**
> Looks like orginal post has a space missing before /Music.

S/B:
 # Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data /Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Just over a month late but I couldn't simply abandon the thread unresolved in good conscience. So here's my current solution as it stands.

We've successfully [dual-booted Win 8.1 and Ubun 14LTS]("http://ubuntuforums.org/showthread.php?t=2271785&page=2&p=13258662#post13258662"). We've ensured that a tertiary [data storage partition mounts automatically]("http://ubuntuforums.org/showthread.php?t=2271785&page=2&p=13278696#post13278696") on-boot for both operating systems. Connecting some of Ubuntu's home folders to their relevant folder on the data partition was the final piece of my puzzle. And I believe you've helped me achieve just that.

Just a few points before getting to the code: this is purely for one folder at a time as I only want to connect a select few folders across the partitions; sudo is required; and, I can't seem to delete anything through the symbolically-linked folders without having to confirm I want to delete it permanently (ie. skip the rubbish bin). The last one is the most bothersome as it indicates that this can't be the complete/ideal solution. In any case, here it it:

```
sudo rm -r ~/Documents                     // Delete the current Documents folder under Home
ln -s /media/Data/Documents ~/Documents    // Connect the Documents folder in the Data partition mounted under /media/ to a new one created under Home
sudo chown -R rishav:rishav /media/Data    // Take ownership of the Data partition
```

I'd be more than happy mark this thread down as resolved at this stage, and even more appreciative if someone could provide additional guidance as to how I could make the same symbolic-link between the aforementioned folders while preserving the basic delete-to-rubbish-bin feature.
And, of course, I'm hugely grateful for your time and knowledge, Oldfred.

---

