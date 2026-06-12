---
title: "Ubuntu partitioning"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by Jan Greeff on 2011-06-24
Apparently Ubuntu installs in a new partition every time which means that my hard drive is getting more and more fractioned every time I upgrade and I have a problem rescuing my emails and addresses every time. Why does Ubuntu not upgrade itself within the same partition like Windows does?

---

### Post by Bucky Ball on 2011-06-24
? Ubuntu *does* upgrade within the same partition. What exactly are you upgrading? Packages or the whole OS? If the latter, how are you doing it? Online upgrade or fresh install (which should go over your previous version on the same partition)?

Need further clarification, here. There are no partitions created unless you create them.

---

### Post by Jan Greeff on 2011-06-24
Thanks, this is good news but then I apparently misinterpret the options, what should I select if I want to upgrade on the same partition without losing any data?

---

### Post by dino99 on 2011-06-24
if your installation is like a standard one (see link joined) then your data inside /home are safe if you take care of not formatting it of course.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by owiknowi on 2011-06-24
just another tip; back up your /home/yourname or other personal data stored on the local hdd, to an external medium before upgrading or installing a new os...
ubuntu normally does a great job upgrading but chances are (see murphy's law)

---

### Post by Bucky Ball on 2011-06-24
Backup always a good idea, but ...

1/ Again, how are you upgrading? Are you using update manager and clicking 'New release available' and backing up from internet? This will upgrade your current running system on the partition it is on, or;

2/ Are you booting from disk and upgrading by *clean install*? As in, you are installing a new release from scratch? You can manual partition this way and install the new release over the old one on the same partition or you can create a new partition and install the new release there, in which case you will have both installs appear in the grub list at boot. 

In 2/ just make sure your /home partition (if you have one, if not, advisable) is not set to format and Ubuntu will find and use it, retaining all your data.

---

### Post by Jan Greeff on 2011-06-25
Thanks, I am upgrading from a CD, but when it asks for partitioning options, I get lost. It seems to give options to create new partitions or to install to the whole disc or to use the whole partition, in both latter cases warning that there will be loss of data. 

The last time I tried to upgrade, the process destroyed the boot record on the second hard drive on my computer, so any upgrade makes me nervous.   

What do you mean by "both installs appear in the grub list at boot" ?

---

### Post by Bucky Ball on 2011-06-25
It also gives the option to manual partition (this might be what you mean by 'create partitions'). That is what you want to do.

Set to install on the existing / partition, make sure your /home partition (if you have one) is not set to format, only /. 

**BE WARNED**: If you do not have a separate /home partition this install will wipe out everything in the / partition (including your /home directory if it is there).

While you are manual partitioning, you might want to clean up the extra partitions that have been created and get things in order. You can also do this first by booting from the Live CD and using the partition editor (Gparted). That way everything will be ready to go when you get to partitioning during the install (which, incidentally, uses Gparted, too).

My main point: **Have a plan** before you get into manual partitioning. This may require a pencil and paper to make a diagram or two of your hard drive and how you are going to partition it (and what is already there you want to keep).

Last tip: Open the partition editor from a LiveCD and have a good look, get familiar with it before you start to install and partition. As you make changes, it lists them in a panel at the bottom of the GUI. In other words, nothing is changed until you apply your list of changes so you have a good chance to triple check they are the changes you want to make. If they aren't, you have the chance to cancel and start again. 

Good luck ... ;)

PS: I would advise 10.04 LTS for a new comer. Smoother ride while you learn the ropes and you can upgrade to a newer release anytime you're ready (LTS release also supported until April 2013).

---

### Post by Jan Greeff on 2011-06-26
Hi Bucky Ball, many thanks for the trouble you went to to help.

I don't want any partitions, all I want is to upgrade my 10.04 to 10.10 on the current (unpartitioned) hard drive without losing any data.

---

### Post by oldfred on 2011-06-26
If you have an install, then you do not have an unpartitioned drive?? At the least you have / (root) and swap as two partitions with /home that has your user setting & data inside the /. If you do an upgrade from inside your existing install (System, Adminstration, Update Manager), it will update you to the next version. Many of us like complete new installs. I had upgraded in place for 3 years every 6 months and had lots of cruft. A clean install then eliminated all the left over bits of stuff from older installs.

But if doing a clean install you should have /home separate or well backed up to reuse or reinstall. Otherwise you lose your data & settings. If you have installed lots of applications you can also make a list to reinstall the newer versions easily.

Post this to see your existing partitions.

```
sudo fdisk -lu
```If you want to backup installed apps:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by Jan Greeff on 2011-06-26
This is the result from sudo fdisk -lu:

I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2c81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   306626559   153312256   83  Linux
/dev/sda2       306628606   312580095     2975745    5  Extended
/dev/sda5       306628608   312580095     2975744   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bbb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   184906650    92452301+  83  Linux
/dev/sdb2       184907774   312580095    63836161    5  Extended
/dev/sdb5       306442240   312580095     3068928   82  Linux swap / Solaris
/dev/sdb6       184907776   301389823    58241024   83  Linux
/dev/sdb7       301391872   306440191     2524160   82  Linux swap / Solaris

Partition table entries are not in disk order
jan@jan-desktop:~$ 

I have no idea what this means. 

Also "from lovinglinux - use dpkg to list installed apps" - what is "lovinglinux"? Perhaps I am just too illiterate to be trying my hand at Linux. 

Seems like you are suggesting that clean install is the way to go to get rid of bugs - makes sense.

---

### Post by oldfred on 2011-06-26
If you follow the link you will see lovinglinux is a user who posted the instructions. I try to reference a user where I get good info from.

You are showing three installs of Linux with lots of partitions?

sda1, sdb1 & sdb6. What installs do you have and what are you booting into? What do you want to keep or how do you want to configure you system. You do have two drives so you can do a lot.

If you want us to see all the details of your installs. Download this and run the script:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Jan Greeff on 2011-06-27
Hi oldfred and thanks. 

I am currently booted on 10.04, and have 10.10 on my other drive that I can also boot to. There is also another version (I think also 10.10) on the other partition but the boot record on that one was apparently disabled somehow by a previous upgrade. 

What I would like to do (after having seen what the forum recommends) is to transfer all my data to the 10.10 on the other drive, then use the current drive to backup. When the next upgrade is done, I can probably do it on the backup drive. Does this make sense? What pitfalls should I beware of?

---

### Post by oldfred on 2011-06-27
While I prefer the clean install I also rotate installs and keep several old ones now that my larger hard drive has space. I just have 20-25GB root partitions with /home still inside them. I think have data in a separate /mnt/data partition that I use to link all the standard folders into my /home so it looks like a full install with my data in the normal places in home.

With new installs backup is important. I backup everything in /home but that is 1GB in my system which is mostly .wine for Picasa that I have not yet moved into my data partition. I also use the dpkg to reinstall my apps and have made a couple of system settings in /etc and make copies of those into a folder in my /home so I back those up. Others suggest a full backup of /etc, but I still have my old install that I can go back to if I have to for some setting (twice so far). After doing the same thing over & over with new installs, I listed history to a text file and converted it to a simple bash file to redo everything.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
I have added a few things:
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
I do not worry about these but others may have them with data files not in /home.
Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

---

### Post by Jan Greeff on 2011-06-27
On my previous install of 10.10, the boot of the backup drive was disabled. This scared me, so should I always disconnect the second drive when upgrading on the first one or is there a way to avoid this problem?

---

### Post by oldfred on 2011-06-27
Many suggest disconnecting drive for those who are very concerned. I alway do manual install and never have the issue as then I get a choice on where to install grub2's boot loader and know to do that. Otherwise grub likes to install to sda as that is the default for most systems. I like to keep different installs on different drives and have the boot loader on the same drive. Then each drive is independent and if one failed the other could boot.

If you do disconnect then to find the other systems you have to run this:
sudo update-grub

Lots of details on how to install to a second drive:
Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

