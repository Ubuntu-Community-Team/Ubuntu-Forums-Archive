---
title: "Install hangs up (plus an introduction)"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by mcompton1973 on 2006-11-17
ok, 
I am not a Linux guru at all.  I have been playing around with it for a few years (my first experience was mandrake Linux...from around '99 or 2k?)  Anyways I have always been a closet geek and now I am going back to school to finish my degree in Applications Engineering.  

I work for a mortgage company now that is about 25 people, and no real tech person at all.  We do most of our work via a remote terminal server.  In the past as they hired people they went to sams club or Office Depot and bought a computer for them.  There was no one person that was responsible for the computer software or anything else....so right now there are 28 computers, and I can locate 1 copy of Windows XP.  If someone has to reinstall Windows it is with that one copy.

Since Windows has done it's verifying software is right etc, we have a couple of computers that I think are being crippled when Windows notices that the software is not right.  (i.e. someone tried to update Widows Media Player....since then that computer will connect to the Internet for a couple of minutes right after a computer reboot...but then will seem to "loose the connection"  however even when you can not connect to the net you can still use remote terminal server...so it is not truly a connection issue...it is a software issue...I installed Firefox, and it still has the same problem.  

Rather than look at that is a challenge, I am using it as a chance to get the company to slowly start migrating to Linux on the desktop.  The server that we connect to is a service that we pay for which makes it less expensive than the special software licenses that we need and solves some other issues for us.  So really in the office allow e need is a computer that will allow us to go to the net (the terminal server limits graphics, and blocks sites that we actually need access to.)  and access to remote terminal server.

So why spend the money to upgrade windows, or replace missing licenses of windows when we can use....Ubuntu?  Now comes my problem.  I downloaded a CD at home.  Burned to to disk.  used it at home, and it worked.  Trying to load it here at the office, and on step 5 of 6 durring the install when I should be managing the partition sizes I see the partition tool load, and then it just sits there saying select a disk etc...but not showing me the radio buttons to choose a task...it just has been sitting there for a long time with the curser doing little circles like it is thinking....

any ideas on what I need to do?  did I miss something?  thoughts?

On this particular computer I am not going to be keeping Windows at all.  This machine windows got messed up and I was planning to just reformat entire disk and have nothing but Ubuntu.

---

### Post by wpshooter on 2006-11-17
Dear Mcompton:

I sure hope you have permission/authorization for what you are doing.  If not, you may find yourself unemployed.  

If your company does not have legit licenses for the copies of Microsoft O/S that they have installed on their computers, they are probably going to find themselves in hot water with both Microsoft and with their own clients when they are not able to service their clients needs when their computers no longer work.

As far as switching to Ubuntu/linux, I hope you have done a good bit of research to find that you are going to have the ability to run the software applications on a Ubuntu/linux system that will be usable by their employees and be able to perform the business functions that are needed to run their business.  I am afraid that you are going to find that the business application software base is not currently available to operate MOST businesses operating in this country, USA.  Of course, you will find many people on this and other Linux forums which will tell you how many software applications are available for Linux systems, but what they fail to tell you is that most of these "applications" are actually utility type programs and at that, ones that the majority of computer users are not going to have any idea how to operate without a major expense outlay for training.

Sounds like to me that if this company does not currently have a "PROFESSIONAL" IT person on staff, that the best thing you could do for this company is to relate to them the importance of their obtaining one, yesterday.

Good luck.

---

### Post by Herman on 2006-11-17
> and on step 5 of 6 durring the install when I should be managing the partition sizes I see the partition tool load, and then it just sits there saying select a disk etc...but not showing me the radio buttons to choose a task...it just has been sitting there for a long time with the curser doing little circles like it is thinking....
any ideas on what I need to do?  did I miss something?  thoughts?
On this particular computer I am not going to be keeping Windows at all. This machine windows got messed up and I was planning to just reformat entire disk and have nothing but Ubuntu. That usually means either the hard disk's firmware (BIOS) isn't supported by this partitioner yet, or the partitioner has detected some form of corruption in your partition table. By refusing to touch your disk, it's protecting you from a possible catastrophe, depending on what the actual problems really is. Proceed with caution.

I think it would be a good idea to run the LiveCD and find out what the output from 'sudo fdisk -lu' tells you, ```
sudo fdisk -lu
``` If, as you say, this computer is already beyond repair (software-wise), then perhaps it won't matter, but just the same, it's nice to try to see what's going on. The worst that can happen is you will have to re-install Windows again, which you would otherwise have to do anyway, by the sounds of things. I presume you have info backed up.

Regards, Herman

---

### Post by mcompton1973 on 2006-11-17
Part 1:


Yes I have permission.  :-)

The reality is that the only thing a computer here in the office needs to do is

a...a good working web browser.
b...the ability to connect to a remote terminal server.  and yes I was told on another forum that there are plenty of ways to access remote terminal server through Linux.

All of our companies software...all of our files etc are on the remote server.

As far as the licenses...we have the reciepts etc for all the computers that we have purchased...we just do not have the manuals and the back up XP disks that came with the computers...does that make since? 

As for clients information and all of that is different because that is all on the terminal server.  All of that is handled by a company that has all of our vendor software and all of that sent to them, and they record and make sure the licenses are taken care of etc etc etc.

I am not worried about that.  I am worried about using a situation here at work to help expose more people to Linux, and also saving the company money by not having them try to purchase new licenses, or upgrading to Vista when they can use Linux instead.

_______________
Part 2:

I am emailing this now using the liveCD of Ubuntu on the computer that I am trying to install on.

here is what it said:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63       80324       40131   de  Dell Utility
/dev/hda2   *       80325   117178109    58548892+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ideas?
format or partition from the liveCD outside of the installation?

---

### Post by Herman on 2006-11-17
A similar scenario exists in offices and institutions all around the world.  The Windows Install CDs seem to be missing or damaged in offices I've visited too. Employees can't always be trusted to take care of things like that, and things go wrong, especially when the main business involves something incidental to computers. A computer is just a tool of trade, tools don't always get looked after when more important business matters take up everyone's time and attention.

It makes sense for businesses and institutions to switch to Linux if Linux will do all that particular business or institution requires. In many ways, Linux is far superior for business use. One CD can be used to install software legally in as many computers as you like for free, that alone can save a lot of money. There are lots of other advantages of Linux, I won't repeat them all here, because we all know them already.
Just judging from forum statistics, (because those are  the only statistics accessible by me), it looks to me as if Ubuntu is really taking off. 

Sat 04 Nov 2006 13:14:03 EST, Members: 188,743, Active Members: 140,906
                                         _..............................................................+6837..........................._                    _+4810 _          
Sat 18 Nov 2006 06:51:55 EST, Members: 195,580, Active Members: 145,716

Due to continued hard work by the developers, the software has improved out of site in the past year or so, and the user base is beginning to 'snowball' as a result. New users who may be students now, will be able to find work easier in the future as Linux, and Ubuntu, continue to take over. Businesses will be looking for people with Linux technical skills and as the young people using Ubuntu now for helping with their studies move on into the business world they will bring their Linux knowledge with them. Some will possibly end up running businesses of their own too. Ubuntu is just getting started, just wait a little while, you'll see!

Regards, Herman :D

---

### Post by Herman on 2006-11-17
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63       80324       40131   de  Dell Utility
/dev/hda2   *       80325   117178109    58548892+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
``` Well, your fdisk output is normal, that's good.
>  ideas?
format or partition from the liveCD outside of the installation?Yes, maybe try with a different 'Parted based partitioner, such a QTParted from Knoppix or System Resuce CD, or , best of all, [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")

If the disk has been corrupted by viruses or an older version of a certian popular commercial disk partitioning software, those symptoms can occur. You might have to resort to trying to keep using that certain other brand of software, but sometimes it causes bootloader problems too, so it's best to stick with the 'Parted based partitioners if you can.

---

### Post by christhemonkey on 2006-11-17
Try partitioning the hard drive before hand, via the partition manager in System > Administration > Disk Partitioner (or the like), and then running the install and selecting to use the partitions you have just made.

---

