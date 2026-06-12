---
title: "Naughty 10.10 installer - partition takes over disk"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-10-16
I think I saw this yesterday also but at the time it looked like I had a hardware problem. However, today I used a different hard drive and created a couple of partitions with unallocated space in between. 

A sequence of screen shots are attached.

I note that the ntfs partition was smaller than the ext4 partition. This was intended, so that the action centred around the (larger) ext4 partition.

I used the 10.10 desktop (live) CD, checked and self checked, for the gparted activity and the install.

For the install I chose the option
'Install alongside other operating systems'

The installer chose the largest useful partition and offered to resize it. I did not want this, I wanted to use the whole *partition* (/dev/sda2)

So I used the button
'Use Entire Partition'
(there are two buttons,  the other is labelled 'Use Entire Disk' Note I did NOT choose the Disk one!)

The install, however, took over the entire disk regardless. This is repeatable (although time consuming....)

---

### Post by ajgreeny on 2010-10-16
You should have chosen the "Specify partitions manually (Advanced)" that shows as the third option on your second screenshot.  You would then have been able to choose the unallocated space between the ntfs and ext4 partitions already on the disk and used that for the new OS.

If you already have partitions which you want to use, that is the only way to do it in Ubuntu, as far as I'm aware.  I don't think it is a bug of any sort, but simply the way the installer works

---

### Post by candtalan on 2010-10-16
Oh really?
Then - what is the meaning of
'Use Entire Partition'
?

---

### Post by candtalan on 2010-10-16
I have now seen this on two different, single hard drive, machines.

I have tested it each time starting with two partitions, NTFS and ext4, of different sizes, either with some large unallocated space on the drive, and alternatively with no unallocated space.

Tests:
I only tested the situation starting with the selection of the option
  'Install alongside other operating systems'
I then did a number of different tests as follows, always again starting from the above situations. (It did take some time....)

1) If I then chose the inviting and very reasonable further option button
  'Use Entire Partition'
then the entire DISK (not partition) was formatted and the install took over the drive.
This is treacherous. In my case (on a test reference machine) I had lost a Windows installation and an Ubuntu installation. The second drive was unaffected.
The partition was ignored and the whole disk was formatted and taken over regardless of whether I was faced with the ext4 or the NTFS partition, (depending on their relative sizes). A number of different tests were run.

2) If however, I simply accepted the resizing option, either at the offered size or even moving the slider so that the original partition was as small as possible, then the installer partitioner worked correctly. The smallest residual partition that could be made was somewhat less than 1GB.

3) I tested the option button
'Use Entire Disk'
and this worked as expected, correctly, with the useful reassurance of a /dev/sda indication.

4) With some tests in 1) above, on some occasions I tried the go 'Back' option to return to an earlier stage and also the 'Split Largest Partition' following the choice of 'Use Entire Partition', which has a similar 'go back' effect. Interestingly, although none of these should lead to a format of the whole drive, on occasions a different (!) gui was shown which I believe was that as shown in 3) above. The whole drive.

Although the option I have seen problems with will probably not be the most frequently used, it is clearly offered. And clearly is going to spoil someone's day.

---

### Post by psusi on 2010-10-16
Use entire partition means just what it says: use that whole existing partition.  As opposed to splitting it in two, one with the old system, and one with Ubuntu.

---

### Post by candtalan on 2010-10-16
> **psusi said:**
> Use entire partition means just what it says: use that whole existing partition.  As opposed to splitting it in two, one with the old system, and one with Ubuntu.

My experiences as described indicate the option certainly does not do what it says!

---

### Post by psusi on 2010-10-16
> **candtalan said:**
> My experiences as described indicate the option certainly does not do what it says!

No, it does exactly what it says.  You just misunderstood what it said.

---

### Post by arubislander on 2010-10-16
I agree with candtalan. The option clearly does not do what would be expected of it. 

Any option that says 'Use the entire partition' as opposed to 'Use the entire disk' should only replace the selected partition, and not all partitions on the disk.

Although I can understand what the developers were thinking when implementing this feature I agree that it is dangerously misleading.

---

### Post by arpanaut on 2010-10-16
+1 [I] arubislander

What the OP could have done was choose the advanced option and specified partitions to use since he had already prepared the disk for that.
Side by Side usually means within partition that holds the existing OS.  
Still I don't see how the "entire disk" was used from the options chosen. Or at least it shouldn't have.
[/I]

---

### Post by VectorVictor on 2010-10-16
The changes in 10.10 installation process is horrible.  It was very simple to install 10.4 with an existing Windows 7 operating system and now it's ridiculous.  I originally used the Ubuntu Windows Installer for 10.04 and tried to 'upgrade' my ubuntu to 10.10.  This killed my grub menu and was no longer to boot to Linux.  It only took me to a grub prompt.  So I uninstalled Ubuntu from Windows7, and tried it again.  The default windows installer is still using 10.4 which is incredibly annoying since I was supposedly downloading it from the 10.10 download site.  So, I downloaded the full desktop ISO and made a bootable disk.  During the installation process is asked if I wanted to 'install alongside existing OS'.  When I selected this option it then wanted to USE MY ENTIRE HARD DISK AND DELETE MY WINDOWS 7 PARTITIONS.   Of course I didn't proceed.  Until it's intuative to install alongside my existing Windows 7 I guess I will just reinstall 10.04.  Was very disappointed in these changes of the installation process.  I've installed the last 4 versions of ubuntu and never had these problems.  I guess I'll wait until 11.4 to see if they make it friendly again.

---

### Post by candtalan on 2010-10-16
> **psusi said:**
> No, it does exactly what it says.  You just misunderstood what it said.

Have you seen what my tests actually did please? And the  earlier screenshots?

There are two clearly different buttons. One says Partition. The other says Disk.

I do not believe I misunderstood anything. 

I believe the detail option button (for 'Entire Partition') as I have described does *not* work as intended. I attach here a screenshot of one circumstance of choosing 'Entire Partition' and it is (in this case) clearly marked as a drive (sda) not a partition (sda5 or whatever). This is what I referred to in note 4) in my earlier message.

As I have found and described, both buttons 'Entire Partition' and 'Entire Disk' do exactly the same thing!

If you have genuinely used the tests from a current Live CD as I have described, and found a different result I would be grateful if you would please explain?
Thank you for your attention.

---

### Post by candtalan on 2010-10-16
> **arpanaut said:**
> 
Still I don't see how the "entire disk" was used from the options chosen. Or at least it shouldn't have.
[/I]

That is my point precisely

---

### Post by psusi on 2010-10-16
> **arubislander said:**
> 
Any option that says 'Use the entire partition' as opposed to 'Use the entire disk' should only replace the selected partition, and not all partitions on the disk.


That is exactly what it DID do, but what he wanted it to do was split the existing partition and install ubuntu to the new one.

> **candtalan said:**
> Have you seen what my tests actually did please? And the  earlier screenshots?

There are two clearly different buttons. One says Partition. The other says Disk.

I do not believe I misunderstood anything. 

I believe the detail option button (for 'Entire Partition') as I have described does *not* work as intended. I attach here a screenshot of one circumstance of choosing 'Entire Partition' and it is (in this case) clearly marked as a drive (sda) not a partition (sda5 or whatever). This is what I referred to in note 4) in my earlier message.

As I have found and described, both buttons 'Entire Partition' and 'Entire Disk' do exactly the same thing!

If you have genuinely used the tests from a current Live CD as I have described, and found a different result I would be grateful if you would please explain?
Thank you for your attention.

When you only have one partition on the disk, there is no difference between using that partition, and using the entire disk.

I can see how you became confused and it does not make much sense to have a button to cancel splitting the partition and just overwrite it, after you have already chosen to do a side-by-side install, but the button still says use the whole partition, and that's what it did.  It is referring to the one partition that already exists on the disk, not the new one that it was proposing to create.

In other words, it is not a bug in the software, but rather a poor user interface choice that is likely to confuse people, as it did to you.

---

### Post by candtalan on 2010-10-17
> **psusi said:**
>  what he wanted it to do was split the existing partition and install ubuntu to the new one.

If you refer to me (OP) then this is incorrect.
I wanted to install Ubuntu into the whole of the currently offered partition, in a drive which contained more than one partition. The installer had chosen a likely partition, the target partition was explicitly labelled in the GUI, and it was the partition (not the drive) which was referred to and was in use as a target.
I am not and I was not, confused!

In my case I had previously lost a multi OS, multi partition, drive, although my subsequent, detailed, and repeatable, tests were done on drives with two partitions.

A disk containing two partitions, is not an uncommon situation. Many Windows machines contain a couple of restore or recovery partitions. Many of the more adventurous (Windows) users have created a second user partition often for data. I run a regular monthly Ubuntu centric FOSS display at a local computer fair..

> 
it does not make much sense to have a button to cancel splitting the partition and just overwrite it, after you have already chosen to do a side-by-side install


With respect, it *is* very useful in a common situation where a user simply has two partitions and wants to retain a system (Windows maybe) ie 'Side-by-Side', and wants to make use of their second (data) partition for an alternative OS.

> 
but the button still says use the whole partition, and that's what it did.


No, it did not, it took over the DRIVE, not the 'Partition' it as it offered. Please do tests for yourself? They are easy and repeatable. I am not confused.

> 
It is referring to the one partition that already exists on the disk


It is referring to the one partition it displays as the current target for action. It names the partition correctly, eg /dev/sda5. It handles a two partition disk (or a multi partition disk) perfectly well (impressively well). The target partition changes according to relative sizes of the available partitions. The installer seems to choose a target partition which has space and which is the largest available. This is a perfectly valid and useful approach.

The only problem is that if resizing is not accepted, but a partition takeover is chosen, then the whole DRIVE is wiped!

---

### Post by psusi on 2010-10-17
> **candtalan said:**
> If you refer to me (OP) then this is incorrect.
I wanted to install Ubuntu into the whole of the currently offered partition, in a drive which contained more than one partition. The installer had chosen a likely partition, the target partition was explicitly labelled in the GUI, and it was the partition (not the drive) which was referred to and was in use as a target.
I am not and I was not, confused!

THAT is your confusion.  There WEREN'T two partitions on the disk.  There was one partition containing windows, and it was proposing to split it in two.  You chose to use the one existing partition for ubuntu.  That is an easy mistake to make when you are looking at the screen it was on, and it does not make sense to have a button there that effectively reverses the previous choice of doing a side by side install, but that is exactly what the button means, and exactly what it did.

> **candtalan said:**
> No, it did not, it took over the DRIVE, not the 'Partition' it as it offered. Please do tests for yourself? They are easy and repeatable. I am not confused.

Do you not see that when there is only one partition on the disk, that using the whole disk, and using that one partition are the same thing?  The partition the button is referring to is the one containing windows, not the new one in the picture that was proposed to be created for ubuntu.


> **candtalan said:**
> 
It is referring to the one partition it displays as the current target for action. It names the partition correctly, eg 

That is where you are wrong.  It might make more sense if this were the case, but it isn't.

---

### Post by Mark Phelps on 2010-10-17
In sympathy with the OP, I've been doing multi-boot installations of Linux distros since the 7.04 days, and when I installed 10.10 yesterday, this was the first time I felt nervous about what the installer was going to do.  I, too, was unsure (since I wanted the same options as the OP) as to whether or not the installer was going to use the free space or overwrite my existing partitions.

What I did, which I think was different, was click the link about using the advanced partitioner, and IN THERE, I selected the free space.

But, I went back first and imaged off the other two partitions -- just in case.

And, while I agree that "technically" if you tell it to use the whole partition, when in fact, you want it to use the free space, and it then overwrites the partition, it DID do what you told it to do ... the way it is presented by the installer, it's confusing.

And unfortunately, in the case of the 10.10 new installer, confusion leads to lost data -- which, really, should NEVER be the case!

---

### Post by candtalan on 2010-10-19
Please see bug #659106
'Maverick installer lost Windows partitions'

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

Status New, Confirmed

---

### Post by kansasnoob on 2010-10-19
> **candtalan said:**
> I think I saw this yesterday also but at the time it looked like I had a hardware problem. However, today I used a different hard drive and created a couple of partitions with unallocated space in between. 

A sequence of screen shots are attached.

I note that the ntfs partition was smaller than the ext4 partition. This was intended, so that the action centred around the (larger) ext4 partition.

I used the 10.10 desktop (live) CD, checked and self checked, for the gparted activity and the install.

For the install I chose the option
'Install alongside other operating systems'

The installer chose the largest useful partition and offered to resize it. I did not want this, I wanted to use the whole *partition* (/dev/sda2)

So I used the button
'Use Entire Partition'
(there are two buttons,  the other is labelled 'Use Entire Disk' Note I did NOT choose the Disk one!)

The install, however, took over the entire disk regardless. This is repeatable (although time consuming....)

I started a thread in Natty testing discussing just this:

[http://ubuntuforums.org/showthread.php?t=1595807](http://ubuntuforums.org/showthread.php?t=1595807)

I filed a bug report during Maverick final iso-testing:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

You'll notice it earned a "Won't fix" so I'm trying to put something together for Ayatana in hopes that the design can be reconsidered for Natty.

I also filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/657397)

That actually may exacerbate the problem.

Hopefully I'll get something posted at Ayatana within the next few days, I'm just buried with unrelated projects at the moment.

---

### Post by A_T on 2010-10-19
Agree the new installer is a menace. The option in earlier editions of "Use the largest continuous free space" which was so easy to use has inexplicably disappeared. Now it's almost as if it wants you to unknowingly wipe data.

---

### Post by Mark Phelps on 2010-10-19
> **A_T said:**
> Agree the new installer is a menace. The option in earlier editions of "Use the largest continuous free space" which was so easy to use has inexplicably disappeared. Now it's almost as if it wants you to unknowingly wipe data.

+1 ... and we can expect to see a rash of "I installed Ubuntu and it wiped out my Windows 7!" posts when people guess wrong with the new installer.

---

### Post by kansasnoob on 2010-10-19
> **A_T said:**
> Agree the new installer is a menace. The option in earlier editions of "Use the largest continuous free space" which was so easy to use has inexplicably disappeared. Now it's almost as if it wants you to unknowingly wipe data.

I didn't address that in my Ayatana request. I'd thought about it but I decided to initially address just the confusing options offered.

If my Ayatana request fails the only option is to keep firing comments at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by arubislander on 2010-10-21
> **psusi said:**
> THAT is your confusion.  There WEREN'T two partitions on the disk.  There was one partition containing windows, and it was proposing to split it in two.

The OP states that there were several partitions on his drive, and he has the screenshots from GParted to prove it.

> **psusi said:**
> Do you not see that when there is only one partition on the disk, that using the whole disk, and using that one partition are the same thing?  The partition the button is referring to is the one containing windows, not the new one in the picture that was proposed to be created for ubuntu.
You are right that there was only one partition in the dialog you are referring to, but it is one of the several that were on the disk. Take your time to go over the first post in this series, and especially the first screenshot in that post.

---

### Post by psusi on 2010-10-21
> **arubislander said:**
> The OP states that there were several partitions on his drive, and he has the screenshots from GParted to prove it.


On the screen in question there is one partition.  The two options are to split it in two, or use it as-is.  He chose to use it as-is.

---

### Post by arubislander on 2010-10-24
> **psusi said:**
> On the screen in question there is one partition.  The two options are to split it in two, or use it as-is.  He chose to use it as-is.

Correct. The installer chose one of the available partitions (one of the three) and elected to show that it would split that one, or you could choose to overwrite it.

But the overwriting one partition is not the same as overwriting the whole disk if there are more partitions available... But as the OP has repeatedly said: Try it yourself if you have the time, you'll see what is meant.

---

### Post by Quackers on 2010-11-15
FWIW I have added my comments to the bug report

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by jehiva on 2010-11-22
This screwed me over, I really wish I would have looked it up prior to using the option.

I had three partitions all set and ready to go.  One was my existing NTFS partition with Windows 7 on it.

Another was my Ubuntu 10.10 32 bit partition. 

Lastly I had a third partition formatted as ext4, I had that partition selected and chose to Use Entire Partition.

The damn installer took the entire hard drive for the new Ubuntu 10.10 64 bit install.

Claiming that what I wanted to do was split partitions or something is ridiculous, I had 3 distinct partitions - each formatted completely different (NTFS, ext3, ext4) and the thing used the entire disk.

If I had wanted to use the entire disk, I would have chose that option.

VERY misleading and aggravating.  The 10.04 installer worked perfect to allow me to dual boot Windows 7 and Ubuntu 10.04 while the 10.10 installer just screwed me over and erased all my data.

---

### Post by kansasnoob on 2010-11-22
> **jehiva said:**
> This screwed me over, I really wish I would have looked it up prior to using the option.

I had three partitions all set and ready to go.  One was my existing NTFS partition with Windows 7 on it.

Another was my Ubuntu 10.10 32 bit partition. 

Lastly I had a third partition formatted as ext4, I had that partition selected and chose to Use Entire Partition.

The damn installer took the entire hard drive for the new Ubuntu 10.10 64 bit install.

Claiming that what I wanted to do was split partitions or something is ridiculous, I had 3 distinct partitions - each formatted completely different (NTFS, ext3, ext4) and the thing used the entire disk.

If I had wanted to use the entire disk, I would have chose that option.

VERY misleading and aggravating.  The 10.04 installer worked perfect to allow me to dual boot Windows 7 and Ubuntu 10.04 while the 10.10 installer just screwed me over and erased all my data.

I've been trying everything humanly possible to get this addressed:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I'd appreciate if you'd comment at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

I know it won't now be changed in Maverick but I hope to see it improved in Natty. The following link is probably the most intensive peek at the confusion inducing options:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

---

### Post by jehiva on 2010-11-22
Posted on Launchpad, this really needs to be fixed.

---

### Post by bcampbel on 2011-03-25
I've just been screwed by this bug and yes, it is a bug!

I have (sorry, had) a dual boot Windows / Linux machine. Having rejected the "Entire **Disk**" option, I was shown an image of my Linux partition with the existing Ubuntu 9.4. The installer offered to split the Linux partition in two and install 10.10 next to the existing one.  I had backed up my data from the Linux partition in the Windows partition, so I was happy to blow away 9.4 and replace it with 10.10. I was presented with two buttons - "Use entire **partition**" and "Use large partition" (Windows was on the large partition). The installer only showed the Linux partition, so it is perfectly reasonable to expect that "Use entire partition" was referring to that. Surely, the ability to replace an old version of Linux with a new one in an upgrade procedure is not so uncommon that it needs to be the subject of fiddling with the advanced options.

In future, I will be getting my distro's from a company that knows the difference between a disk and a partition, and considers an installer that causes people to inadvertently wipe their entire PC as a serious problem that needs an urgent fix.

](*,)

---

