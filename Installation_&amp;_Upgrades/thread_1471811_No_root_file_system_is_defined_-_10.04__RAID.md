---
title: "No root file system is defined - 10.04 / RAID"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Ramzy on 2010-05-03
[I have searched through many websites so far](http://i44.tinypic.com/11kv7uu.png), and have been unable to find an actual answer to this issue.

I am running a RAID0 array, with Windows 7 Ultimate x64 installed.

When i install LL10.04 through Wubi, it installs fine, reboots, continues the installation procedure, then it gives me an error box "No root file system is defined".

I have attempted pressing the "OK" button 10 or 15 times, however it does not progress. The box just keeps on popping up. My only option is a hard reset.

[img]http://i44.tinypic.com/144a0ht.jpg[/img]

I've tried downloading the latest version of Wubi from the official website, and allowing Wubi to download ubuntu itself, and still nothing.

Please offer suggestions.

Side note: I do not want to create a new partition for Ubuntu and use the GRUB loader. I have a multi boot system and would like to stick to the windows boot loader.

---

### Post by Ramzy on 2010-05-04
Nothing at all?

I have found posts of people complaining of this issue since version 6 of Ubuntu.

There must be some information.

---

### Post by pjok on 2010-05-06
Hi, I'm afraid I can't get you an awnser. Though I get the same error on one of my computers installing Ubuntu via Wubi. I installed it earier yesterday on my laptop, but when I install it on my PC at home, I get the exact same error. 

Someone please find an easy solution to this issue.

---

### Post by dino99 on 2010-05-06
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by pjok on 2010-05-06
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

I'm sorry, my CD doesn't work and I don't have an USB stick, that's why I use Wubi. How do I fix this issue installing Ubuntu with Wubi?!

---

### Post by Ramzy on 2010-05-06
> **pjok said:**
> Hi, I'm afraid I can't get you an awnser. Though I get the same error on one of my computers installing Ubuntu via Wubi. I installed it earier yesterday on my laptop, but when I install it on my PC at home, I get the exact same error. 

Someone please find an easy solution to this issue.

Same issue for me. Installed Ubuntu 10.04 on my work laptop with no issues, via Wubi, however my home PC is getting the error.

@dino99
Thank you for taking the time to post an answer, however like i mentioned before, i would very much prefer to keep to the windows boat loader, as i have a few operating systems installed and don't want to change everything drastically.

---

### Post by dino99 on 2010-05-06
wubi= linux inside a windoz file :lolflag:

instead install virtualbox on windoz, then the guest (ubuntu) is installed in it easily

---

### Post by Ramzy on 2010-05-06
Already have... But that's just a workaround... Not a solution.

Why is this issue so readily ignored by the community? It has been around for multiple Ubuntu releases now.

[img]http://i44.tinypic.com/5pnedv.png[/img]

---

### Post by pjok on 2010-05-06
> **Ramzy said:**
> Already have... But that's just a workaround... Not a solution.

Why is this issue so readily ignored by the community? It has been around for multiple Ubuntu releases now.


I agree

---

### Post by pjok on 2010-05-20
Still no solution to this?

---

### Post by almigi on 2010-05-20
Found a solution on ubuntugeek:

[http://ubuntugeek.com/forum/index.php/topic,237.msg816.html#msg816](http://ubuntugeek.com/forum/index.php/topic,237.msg816.html#msg816)

This seems to work.

** Update **

Also, looking through the MULTIPLE bug reports regarding this in launchpad, another solution is to download the .iso with the text installer and use that instead.

---

### Post by paulhide on 2010-06-18
> **Ramzy said:**
> [I have searched through many websites so far](http://i44.tinypic.com/11kv7uu.png), and have been unable to find an actual answer to this issue.

I am running a RAID0 array, with Windows 7 Ultimate x64 installed.

When i install LL10.04 through Wubi, it installs fine, reboots, continues the installation procedure, then it gives me an error box "No root file system is defined".

I have attempted pressing the "OK" button 10 or 15 times, however it does not progress. The box just keeps on popping up. My only option is a hard reset.

[img]http://i44.tinypic.com/144a0ht.jpg[/img]

I've tried downloading the latest version of Wubi from the official website, and allowing Wubi to download ubuntu itself, and still nothing.

Please offer suggestions.

Side note: I do not want to create a new partition for Ubuntu and use the GRUB loader. I have a multi boot system and would like to stick to the windows boot loader.

Did you ever get a solution to this? I have the same problem.

Paul Hide

---

### Post by Hans Upp on 2010-09-30
After many years of deliberating, shall I/shan't I go to Linux, today I decided to take the plunge . . . 
. . . and the same as above is as far as I got with installation.

and I thought it was supposed to be better than Micro$not?:mad:


If you bought a new car, and couldn't get it to drive off the sales forecourt, what would YOU say to the salesman?

---

### Post by ronparent on 2010-09-30
A usual result when you elect to manually partition and neglect to designate '/' as the mount point.

---

### Post by Hans Upp on 2010-09-30
> **ronparent said:**
> A usual result when you elect to manually partition and neglect to designate '/' as the mount point.
and how would one know to designate '/' as the mount point (whatever that might be) if it doesn't say so?

Anyway done that now, so instead it then tells me that no mount point is assigned for the file system in the other 2 partitions I created.

OK so I gave them both one, as previous. 
But then it tells me "two file systems are assigned the same mount point" "Please correct this by changing mount points"

Change to what . . . and how?

---

### Post by Hans Upp on 2010-09-30
[SIZE=2]Struggling on . . . managed to get around the hurdles constantly being thrown up, and its starts the installation - :) (but short lived)

Just when the screen comes along saying "Ubuntu is made to be easy" it pops up with[/SIZE]
[SIZE=2]*"ubi-migrationassistant failed with exit code 141. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken"*[/SIZE]

Well, against such a dire warning, how could one not try again? . . . and again . . . and again . . . and again . . . and . . well you get the idea.

If this is the bit that Ubuntu made to be easy, I'm dreading the hard part

EDIT: after many attempts to "try again" I gave up trying and decided to "continue anyway" and it just takes me round in a loop back to the same pop-up. So there is no way you can move forward with the installation regardless.  Now the only option left is "quit".   Hmmmm, I might just do that.

---

### Post by psusi on 2010-09-30
Wubi is evil, don't use it.  Plonk down $5 for a usb flash stick and do a real install.  Plus you will have a rescue system if you ever need it.

---

### Post by Hans Upp on 2010-09-30
wtf is Wubi?

I have a flash stick, several actually . . . so I don't need $5

---

### Post by psusi on 2010-09-30
> **Hans Upp said:**
> wtf is Wubi?

I have a flash stick, several actually . . . so I don't need $5

Wubi is the Windows installer that installs Ubuntu inside a file on Windows instead of in its own partition.

---

### Post by Hans Upp on 2010-09-30
But I don't have Windows, why would I?
I thought the whole purpose of Linux was to get away from Windows.

Are you now telling me that I can't install Ubuntu unless I install Windows first?

---

### Post by psusi on 2010-09-30
> **Hans Upp said:**
> But I don't have Windows, why would I?
I thought the whole purpose of Linux was to get away from Windows.

Are you now telling me that I can't install Ubuntu unless I install Windows first?

The other guy was using WUBI because he didn't have a working cd to install from.  You are choosing to manually partition and not assigning a / partition.  If you don't have a reason to manual partition ( and it sounds like you don't ) then just let it use the whole disk and automatically partition.

---

### Post by Hans Upp on 2010-10-02
But I _**do**_ want to manually partition, its just that Ubuntu seems to just take over control of everything and allows you to do nothing.

I have to say, since taking the decision to install it, this has been the most frustrating 3 days of my life. Most "everyday" people would probably classify me as a computer geek (i.e. they bring me their problems to fix) - but I certainly am not one, and somewhere in there is an indication of my normal user level.

So, these are the partitions I'd like to have created:
1 - named Ubuntu - to install the OS
2 - named Programs - where I'd install my programmes in logically grouped folders
3 - named Data - where I'd store my docs/s-sheets/presentations etc
4 - named Music & Video - take a guess what its for

Why is it, that when you install things you can not control where its installed to, and can't locate the installed files afterwards?

---

### Post by psusi on 2010-10-03
You have some very strange ideas.  Maybe if you could explain why you feel just taking the default option to have one partition is not good enough for you it might help.  If you insist on having multiple partitions, then to address the title of the thread for the issue you started with, you just have to define one partition to be the root ("/").

---

### Post by Hans Upp on 2010-10-03
> You have some very strange ideasI can think of lots of people who, in my opinion, have very strange ideas in life, but I am sure they all have very good reasons for pursuing them and its not for me to question.

However, mine are more simple. They are based on segregation, which facilitates management and organisation.  It also means that, for example, should my OS become so corrupt that repair is impossible, I can format the partition and do a clean install without affecting all my other stored data on other partitions.

Right now, I am tending toward thinking of formatting it to clear Ubuntu off that computer and installing Windows, though I had promised to rid myself of all things Micro$oft.  A decision taken before I had any idea what a total nightmare Linux was.  

Now, just think how much easier it is to do that when it has its own separate partition.

> Maybe if you could explain why you feel just taking the default option to have one partition is not good enough for youFor the same reason that in my office I have a 4 drawer filing cabinet and I know exactly what files are going to be in each drawer.  Imagine for one moment how life would be hell if every time you wanted to locate something you had to search through the randomised contents of one huge box.

Why does a department store have departments?
Why does a hospital have neurology, maternity, and A&E?
Why does a library have sections on criminology, politics, science and fiction?  Should I ask them why the default option of having one big open room with piles of books is not good enough for them?

Yes, indeed these are strange ideas!

---

### Post by psusi on 2010-10-03
You use folders for organizational purposes.  Where on the disk the files in those folders are stored doesn't matter does it?  If you want to separate the OS from your personal data, then create a separate /home partition, but you have to have a root partition to hold the OS, which is what the error is telling you.

You can't keep programs separate from the rest of the OS since the OS itself consists of many programs.

---

### Post by Hans Upp on 2010-10-03
Yes, folders are another layer of organisation. So each partition has its own set of folders.

> You can't keep programs separate from the rest of the OS since the OS itself consists of many programs. 	And so, if I install a program it gets lost in the melèe.

There appears to be no way to see the file structure. And if you want to include an "add-on" you can't see the sub-folder to copy it into.  Say, for a media player e.g. VLC you'd need to see the folder to copy the plugins to

---

### Post by psusi on 2010-10-03
Huh?

---

### Post by Ramzy on 2010-10-24
What a joke.

Ubuntu 10.10, SSDD.

[img]http://img221.imageshack.us/img221/8012/img1858u.jpg[/img]

---

### Post by ronparent on 2010-10-24
That screen is typical of selecting the manual partitioning option during install and then neglecting to select a mount point on the partition you have selected to install to. After selecting the partitions and electing to 'change' it, in the ensuing window make sure '/' is selected as the mount point.

---

### Post by invisiblewave on 2011-02-26
> **ronparent said:**
> That screen is typical of selecting the manual partitioning option during install and then neglecting to select a mount point on the partition you have selected to install to. After selecting the partitions and electing to 'change' it, in the ensuing window make sure '/' is selected as the mount point.

I'm currently in the process of trying to solve this issue, and it's not possible to change the partition mount point.  For exactly the same reasons as the guy above, I want to create separate partitions for the os and the data, so the os can be reinstalled without affecting the data partition.  I've also tried it with a single partition with the same result.

Here's what happens:  You set up the partition table on both drives with two partitions, / and swap.  Next, you configure software RAID.  On return to the partition screen, it shows a logical RAID volume followed by the two physical drives, both with two partitions marked RAID (ie, no mount point specified).  If you attempt to change the partitions, it doesn't let you, it shows a screen saying they're RAID partitions and can't be changed.  The only way to change them is to reboot the installation and go back to the partition manager.  The partition tables are there, the RAID setup is still there, but at this point it will let you change the mount points on the partitions.  So, you change them all back, then it comes up with another error that it can't create the ext4 file system.

---

### Post by psusi on 2011-02-26
You use a partition to hold a filesystem, or as part of a raid array, not both.  In other words, when you changed the partition to be a raid component, it is no longer assigned to /, hence, the error telling you that you did not define where the root file system goes.

---

### Post by andreubun on 2011-02-27
I have the same problem: after the wubi installation the reboot from Win 7 to Ubuntu: No root file system is defined. 
If I reboot and choose ubuntu and then hit the ESC button the DEMO mode than Linux is working but not installed. 
In the grub.cfg is see:

menuentry "Normal mode" {
    linux /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash  boot=casper ro debian-installer/locale=nl_NL.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}

menuentry "Demo mode" {
    linux /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/installation.iso quiet splash boot=casper ro debian-installer/locale=nl_NL.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --  rootflags=syncio
    initrd /ubuntu/install/boot/initrd.lz
}

The ubuntu/disks I have the root.disk and swap.disk.
the subdirectory grub is empty. The installation of Wubi is not finished. 
In the ubuntu/install I see the installation.iso and the ./boot/grub/grub.cfg
This file is used for the reboot.

I need help to solve this problem

---

### Post by invisiblewave on 2011-03-03
Here's how I eventually solved this problem:

Remove RAID setup on motherboard (fake RAID).
Install Ubuntu using alternative install cd.

At the partition menu, create the partitions you want on both drives (in my case, each drive had /, /home & swap).

Take the Configure Software RAID option.

Create one RAID profile per pair of partitions (ie, 3 RAID profiles in my case), DON'T TRY TO CREATE ONE PROFILE FOR THE ENTIRE DISK, you have to do one RAID profile at a time.
So, for the first profile, I entered 2 for the raid devices and 0 for the spare drive.  It then shows a list of all my 6 partitions (3 on each physical drive).  Select the two / partitions (space bar selects), then continue.

Repeat the RAID profile creation for each other pair of partitions you have (/home and swap in my case).

After creating the third profile, select Delete Raid Profile to see the list of profiles you've created, there should be one for each pair of partitions (3 for me).
Don't delete any profiles, return to the RAID profile menu and select Finish.

This should take you back to the Partition menu which should now look somewhat different.  At the bottom of your screen you should see the two physical drives listed with their partitions, the partitions will all be marked 'RAID'.

Above the physical drives, there will be a logical RAID drive, with the partitions listed, so it'll look as if there is an extra drive on your system.  These are the partitions you now have to set up as 'normal' Linux partitions.  Select each partition in turn, and on each one change the type to ext4 (or whatever you're using), then change the mount point to the correct one (/, /home and swap, respectively, in my case).

When you've finished, your Partition menu should show what looks like 3 drives (assuming you're doing a straight mirror RAID 1 using two physical drives), the first one will show your Linux partitions with Linux mount points, the other two will show the same number of partitions each, but they'll all be marked RAID.
From this point, it's plain sailing, save the setup and continue installing as normal. 

Once Ubuntu is installed, sudo cat /proc/mdstat should show each of the profiles you set up, once per partition. This is what mine looks like md1 is the swap partition, md0 is the / partition, and md2 is the /home partition, the [2/2] indicates that the partitions are synched:


md1 : active raid1 sda5[0] sdb5[1]
      11070400 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      97654720 blocks [2/2] [UU]
      
md2 : active raid1 sda2[0] sdb2[1]
      867968960 blocks [2/2] [UU]
      
unused devices: <none>

Be aware that when testing your setup by pulling the plug on one of the drives and running in recovery on one drive, when you subsequently plug the drive back in, you'll need to add the drive back in to the array using mdadm, at which point it'll resynch, which takes all night (the [2/2] changes to [2/1] when running on one disk and stays that way until re-synched).

I hope this helps someone. I tried to make the instructions more detailed than any of the directions I found.

Ubuntu 10.10 64 bit.

---

