---
title: "Installation Errors"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by ubuntisms on 2007-03-24
Hello,

I thought ubuntu would be difficult to install, but later I thought that I would be guided through easily. I even used [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) to help me in installing ubuntu. The first concern I had was that the installation windows were different in mine and that website, although they both are recent. The problem is that  it has different choices and it is basically a different screen at the step of "Prepare disk space" - the exact step I feared something would go wrong at. My installation says 1. erase entire disk (I immediately said no to that); 2. use the largest continuous free space (I thought this was the right one); 3. manually edit partition table (I don't know what to do there so I won't use that). So I chose option 2 as I want to dual-boot. What I got in the next step was a confirmation screen that included:

"GRUB will be installed to (hd0)***
No partition table changes and no creation of file systems have been
planned.
If you plan on using already created file systems, be aware that existing
files may prevent the successful installation of the base system."

*** (hd0) exists as a button where the "device for the boot loader installation" is changeable. However, I have no clue to what I would change that to...

Moving on, I click install and it runs up to 15% where I encounter an error dialog:
"No root file system is defined.
Please correct this from the partitioning menu."

I hope I didn't confuse you literate people with my illiteracy, but I'm obviously doing something wrong that I cannot see. In addition, the CD was checked for errors and returned no faults.

Hopefully you have some solutions to please guide me through the installation.

Thank you for your time - I'm awaiting your wise responses to finally install ubuntu!

---

### Post by eapache on 2007-03-24
What is your current hard-drive setup? Please include other os' installed.

---

### Post by ubuntisms on 2007-03-24
Thank you for your reply,

I have Windows XP installed on the hard-drive and trying to install ubuntu Edgy 6.10. It is the only OS installed and I have not  partitioned anything before, which would mean that the hard drive was in no way disturbed. Is there anything else regarding the setup of the hard-drive?

---

### Post by eapache on 2007-03-24
This sounds like a bug in the os detection settings, but it is easily fixed by manually editing the partitions. First you should defragment your xp(start - all programs - accessories - system tools)to make it easier for the partitioner. Then click manually edit partitions, and tell me what is in the list that shows up. I should be able to give you a brief walkthrough after that.

---

### Post by ubuntisms on 2007-03-24
Ok, thank you. It's going to take some time to partition in windows so I'll report to you soon! In the past, I've had problems with defragmenting in windows as it would not defragment everything; I'll try again and see, but I hope the defragmenting is not an essensial process.

---

### Post by ubuntisms on 2007-03-25
The defragmenting is finally done and it was partly successful with some files that could not be defragmented. Now I have a screenshot of the partitioning step attached, after the defragmenting. So what do I do here if I want my files intact so that the drive is not erased and that I can have a dual boot system.

---

### Post by eapache on 2007-03-25
Ok, the ntfs drive is definitely your main windows drive. Do you actually use the other two fat drives? They may be left over from an upgrade if the pc used to have ME or '98 running on it. They are what messed up the auto-installer. I'm just not sure if it's ok to delete them, or if you'll have to work around their bizarre locations.

---

### Post by ubuntisms on 2007-03-25
The pc did not have any other operating system installed on it (it was bought brand new). Personally, I have no idea what the fat drives are and that's why I didn't wanna mess with manually editing the partition :p

What do I do now? Any ideas?

---

### Post by zvacet on 2007-03-25
Download Gparted Live CD from 
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
burn it and boot with it.If you have no data on your far patitions, delete them and you will have more free space.As far as I see you installed Ubuntu on fat too.Ubuntu format is ext3.So,basicly delete all partitions you don´t need and Ubuntu partition too.That will give you cca 20Gb of space wich is enough for Ubuntu.in installation procedure when you come to partition step choose manual way.I will do that like this(doesn´t mean it is the only option):
1.root =9Gb
2.home=restof free space exept 
3.swap=1GB

---

### Post by ubuntisms on 2007-03-26
> **zvacet said:**
> If you have no data on your far patitions, delete them and you will have more free space.

I suspect you mean the fat partitions. I don't think I should delete them as they have memory used. If memory is used, then it should mean that there is data on it, right?

> **zvacet said:**
> As far as I see you installed Ubuntu on fat too.

I'm running ubuntu from a LiveCD; I didn't install anything.

> **zvacet said:**
> Ubuntu format is ext3.So,basicly delete all partitions you don´t need and Ubuntu partition too.

As I said, it seems that I want the ntfs and the two fat partitions. What does the ext3 have to do with all these. In addition, I don't think I have an ubuntu partition as I did not install ubuntu yet.

> **zvacet said:**
> 1.root =9Gb
2.home=restof free space exept
3.swap=1GB

The problem was that I don't know how to manually partition the drive to look like that. If I knew, then I would do it like that.

In the meantime, I will download, burn, and boot GParted - but I don't know what to do with it.

Thanks for replying to my problem!

---

### Post by eapache on 2007-03-26
does your windows install have multiple drives? It probably has a main c: drive, and it has to have a cd drive as well, but are there other drives?

---

### Post by ubuntisms on 2007-03-27
The main drive C: and the cd drive is D:. There are no other drives, exept possibly some drives that are virtually created by usb memory sticks, or even an iPod.

---

### Post by eapache on 2007-03-27
Ok, that means that unless they are being used by some background program, these FAT drives contain no important data. To verify this, please boot up Ubuntu from the cd, go to Places > Computer (the equivalent of My Computer in XP), and look at what it displays.

There should be several drives (other than 'Filesystem' and the cd/dvd drive). Double-click on each of the unknowns in turn to find out what files it shows. What unknown drives exist and what files are in them should give us a clue as to where these partitions came from, as there is no immediately apparent reason why they should exist at all.

Some screenshots (Applications > Accessories > Take Screenshot) would be useful  as well. Hopefully we can resolve this quickly, as instructions for correct partitioning will take almost no time at all once we know what those FAT partitions are doing there.

---

### Post by ubuntisms on 2007-03-29
I was hoping I would just find those places and that after we know what it is the problem would seem resolved. However, there were absolutely no other drives except "CD-RW/DVD±R Drive" and "Filesystem" in the computer:/// directory. So, in conclusion, we have not determined where those FAT drives come from, and I'm pretty sure I'm not doing something wrong.

---

### Post by eapache on 2007-03-29
All right, if they're not showing up in Ubuntu, let's try getting at them from XP.

1.	Log on as administrator or as a member of the Administrators group.
2.	Click Start, click Run, type compmgmt.msc, and then click OK.
3.	In the console tree, click Disk Management. The Disk Management window appears. Your disks and volumes appear in a graphical view and list view.

It should look somewhat similar to the Ubuntu partitioner. Right-click on the ntfs partition and click 'properties'. In the properties window, find the bit that says that it is available as disk C: Then find that same window for the fat partitions, and browse in windows explorer to whatever drive/location it says. If there isn't anything listed in the properties, click 'add' (or whatever it says, I haven't been in XP in a while) and assign it a drive you aren't using (Q or X should work fine). Then browse their, and hopefully we'll figure out what is on those mystery partitions.

---

### Post by ubuntisms on 2007-03-31
For the NTFS partition I get the dialog of the "Local Disk (C:) Properties". However, when I right click on the FAT partition, the only option I have is "Help". Similarly, with the FAT32 partition I get the options "Delete this partition..." and "Help". There is a screenshot of the "Disk Management" window attached.

---

### Post by eapache on 2007-03-31
How old is your computer? You said it was bought brand new with XP, but EISA is an extension slot technology (like PCI) that came out in the eighties and has long since been replaced by newer technology. I find it hard to believe that a computer that came with XP could have EISA slots on it at all...

This does make some sense though. Most EISA cards made were for SCSI, and since your hard drive is a SCSI drive, that's probably what it's being used for.

Whenever you got it, your computer has a really bizarre set-up. I can't guide you through the partitioning, because EISA and SCSI set-up is beyond me. It's entirely possible that moving those FAT partitions to a better spot wouldn't mess something up, but it's not likely, and you probably don't want to take that chance. The best I can suggest is to go to the manufacturer's website and find the specs on whatever model you bought. See if they say anything about SCSI or EISA.

---

### Post by ubuntisms on 2007-03-31
I only bought my computer 7 months ago and it is not an old model (Dell Inspiron 6400). I found absolutely nothing on the computer about SCSI and EISA, but instead the PCI you mentioned. I've also done an image search on those and I know my computer does not have such things. I also searched throughout the manual, again only finding PCI. I may also add that the laptop has both usb and firewire, as I understood were the suggested newer connections instead of SCSI.

EDIT: Forget everything I just said :p 
I just did a quick search and I found this site that explains specifically about Dells: [http://www.bay-wolf.com/harddrive.htm#23](http://www.bay-wolf.com/harddrive.htm#23).
That site lead me to the manual. Dell has something called "Dell PC Restore" that restores the computer to the original state, like when I bought it. That explains what the partitions are. These partitions can be removed as instructed in the manual, but it also strongly recommends that they are not deleted, even for extra disk space. Therefore, is there a way to go around these partitions?

---

### Post by eapache on 2007-04-02
That's exactly what we needed to know. Problem solved. Now here are your instructions to manually partition your hard-drive (keep in mind that you should back up data before-hand just in case, very unlikely to mess up, but not impossible).

Right click on the ntfs partition and click Resize/Move. Then drag the far right end of the image down to size. You'll want to leave your windows partition some free space, but you should free up probably around 15GB. Now click the OK and the resize will appear on the Operations Pending list at the bottom.

Next, click on the newly created block of free space and click New. Now click on the list that says Primary and select Extended (or Logical, don't remember) instead. The other options list should grey-out. Again, click OK.

In the free space that is now under the Extended partition (like a file in a folder), click new and resize the selected amount to about 1GB (this will be your swap, you can change the size if you want). For this partition choose logical in the upper list, and Linux-Swap underneath.

Now select the remaining 14GB or so under the extended partition and create a logical ext3 partition. Click OK.

Your operations pending list should look something like this:
-Resize /dev/sda2
-Create extended partition /dev/sda3
-Create logical partition /dev/sda5 linux-swap
-Create logical partition /dev/sda6 ext3

Assuming all looks good, click Forward, and let it work. Once it's done, it will ask to select mount points. For the ext3 partition, select "/". For the swap partition, select "swap". You should be able to ignore any others. Click forward, and away you go,

Good Luck!

---

### Post by ubuntisms on 2007-04-03
Thank you! I'm happy to have this explained by someone that clearly knows what's going on :p :D

Your instructions were very easy to follow, that a friend watching me thought I've done this more than once :p

I've gone up to the point where you instruct:

> **eapache said:**
> 
Now select the remaining 14GB or so under the extended partition and create a logical ext3 partition. Click OK.


When I have that partition selected, the only options I have are "Delete", "Resize/Move", and "Information". The "Resize/Move" option opens a dialog, but it does not have the drop-down menus for "Create as:" and "Filesystem". Instead, those menus can be found in the partitions called "unallocated" under the extended partiotion, where the "New" right-click option is available. (I've included a screenshot of the partitioning screen to show this, where the 14GB or so partition is selected).

> **eapache said:**
> 
Your operations pending list should look something like this:
-Resize /dev/sda2
-Create extended partition /dev/sda3
-Create logical partition /dev/sda5 linux-swap
-Create logical partition /dev/sda6 ext3


Also, as it can be seen in the screenshot, the operations pending list does look something like that. However, I was concerned that the first says /dev/sda2 (as you explain), but the others are all /dev/sda (with no increasing number after sda). I just thought it was worth bringing this to your attention.

Thank you once again! The installation is getting closer... :D

---

### Post by eapache on 2007-04-03
For the operations pending list, I though they assigned the partition number before the actual change, but I guess they leave it until the operations are applied, so as not to confuse people trying various things. No biggy.

When first created, the extended partition should have only one solid block of free space inside it (approximately 15GB).

Create the swap partition so that 'free space preceding' is 0, 'new size' is however many MB you want (probably around 1000), and 'free space following' is the rest of the extended partition (14000 or so). The easiest way to achieve these approximate numbers is to grab the right end only of the coloured bit of the graphic, and drag it to the left so that the coloured bit the takes up the far left 1/14 or so of the graphic, and the rest is grey. In your screenshot, the preceding would have been 50, and the following would have been 1000.

After that looks right, then you can create an ext3 in the remaining ~14GB.

Hopefully this clarifies matters somewhat.

---

### Post by ubuntisms on 2007-04-04
Actually, the part you explained I already had, as it is already seen in the screenshot provided. The part after that is what I was asking for:

[Quote=eapache]After that looks right, then you can create an ext3 in the remaining ~14GB.[/Quote]
[Quote=eapache]Now select the remaining 14GB or so under the extended partition and create a logical ext3 partition. Click OK.[/Quote]

In the screenshot you can see that I went up to the part where I have to create the ext3 in the remaining ~14GB. What I saw, though, was that there were no options to create the ext3 when having the "linux-swap" partition selected (no "New" right-click option).
This would mean that I would have to select one of the two "unallocated" partitions. (Both "unallocated" partitions have the "New" right-click option, where I can make a logical, ext3 partition). Which one do I chose (and how big do I make it)?

---

### Post by eapache on 2007-04-05
In your screenshot, you made the swap 13.62 GB. You only need to make it 1GB.
Make sure it is at the very beginning of the extended partition so that it looks like:

fat16
ntfs
extended (14.65GB)
 - - linux-swap (1GB)
 - - unallocated (13.65GB)
fat32

then make the unallocated into ext3.

---

### Post by ubuntisms on 2007-04-06
Just when I thought everything was resolved, of course there came more problems. I feel like I'm bothering you too much, but this time I'm pretty sure I didn't do anything wrong. I took a screenshot of the partition configuration seen on 1.png (attached). After I clicked forward I got the "applying pending operations" dialog. I waited for some time watching at the bar going left and right (!) and then I got this error seen on 2.png. (3.png shows the applying pending operations dialog with the error icon on the first operation; this icon appeared after the error). I clicked "OK", the only option, on the error dialog and then "Close" on the "Applying pending operations" form. Then I got screen 4.png, so I decided to stop.

Do you know what I'm doing wrong? I feel doomed with this situation :p and I'm dragging you into this... Thank you in advance!

---

### Post by eapache on 2007-04-06
Ok, you set everything up properly, so that's not the problem. Try defragmenting xp again, it's possible that the confusion of files made the partitioner wary of moving stuff around. If you get the same error message, try resizing the ntfs partition using xp instead. In the computer management area I talked about before, right-click on the ntfs and there should (I think) be a resize option. If that works, than do the rest from Ubuntu.

It is possible that Dell "locked" the windows partition as part of the same security measures that inspired them to create those restore partitions. In that case, I'm not sure what we can do. It may depend on your bios, but I'd prefer not to get into that if possible.

Try my suggestions, and if they fail, try doing the partitioning from the gparted cd. It will have more recent drivers that might be able to work around whatever is causing the ubuntu partitioner problems.

---

### Post by ubuntisms on 2007-04-07
I defragmented xp and tried partitioning from ubuntu but got the same error again. I cannot resize the ntfs partition from xp in the disk management. So, I'm going to get gparted cd and try to partition with that.

---

### Post by ubuntisms on 2007-04-21
Hello, it's been long since I replied because I had to burn gparted. However, gparted caused the exact same problems. Just letting you know - I don't know if you can do much now. Thanks for your help anyway!

---

