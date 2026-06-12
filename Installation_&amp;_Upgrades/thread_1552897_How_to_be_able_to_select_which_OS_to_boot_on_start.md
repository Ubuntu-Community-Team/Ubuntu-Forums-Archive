---
title: "How to be able to select which OS to boot on startup?"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by garycheng12 on 2010-08-14
I've included many questions to deal with in this thread because it's  easier for me to manage and so that I don't have to create multiple  threads. I will be constantly refreshing this thread to read updated  answers and will also be commenting on the thread. I will not abandon  the thread unless I marked it as **SOLVED**; that way, you won't feel  reluctant to post a lengthy answer (I assume it's lengthy since some of  my questions are lengthy) only to realize that I may have possibly  abandoned the thread and taking the valuable Ubuntu community for  granted =). ANYWAY... here is the background info leading to a chain of  questions that leave me stumped:

Previously, I installed Ubuntu 10.04 (32-bit) on an **external hard  drive** after I created 3 separate partitions: 
  4 gb for the swap partition (I have 4 gb of RAM and plan to use  hibernation), 
 12 gb for the root partition 
  9 gb for the home partition in my external hard drive (can I think of  this as the equivalent of a D drive?)

**Main question: _After installing Ubuntu on the external hard drive,  I am able to run it without problems. If I were to unplug the external  hard drive and restart the computer, the computer would boot into  Windows 7 automatically, which is normal. If I plugged in the hard drive  and then restarted the computer, it would automatically boot Ubuntu,  which is what it should do. However, how can I set up the boot loader  (is this what you call it?) such that I am able to SELECT which OS to  boot if I had my external hard drive plugged in? _****_It would  boot into Windows 7 automatically the user does not select an OS after 5  seconds. _****_ If it were not plugged in, then it would boot  into Windows automatically._ I don't know if GRUB has anything to do  with this (I have never played with dual booting nor boot loaders  before), then I prefer to use GRUB 2 as it seems to have significant  advantages over the older version (I generally prefer using up-to-date  applications as they almost always contain speed/security improvements).  **

Well, this is my first thread so I know I'm asking for a lot of  problems, but I feel that anyone who understands my problem will be able  to provide insight or solutions to more than one of the problems I've  listed which may or may not be relevant to the original purpose of the  thread. The following are completely random questions which I'm sure  have some quite obvious (as well as short) answers, but I literally have not utilized the  Terminal yet, so these newb-ish questions are justified =P.

- When should I choose primary over logistical for creating a partition?  When should I choose end over beginning for that partition to be  located at?

- In Windows, I have use an application that completely uninstalls a  program, meaning its registries are removed as well. I am paranoid when I  have an application installed that I don't need -- an application I  don't need will only take up space in the hard drive and slow down the  computer. When prompted with the updating/installing applications screen  for Ubuntu every time I boot it, is it ideal for the **average** **user**  to use most/all of these applications? If not, which ones are  recommended or essential?

- I had installed 3 main applications (is it unanimous with the term *packages*?),  and all 3 main applications required that I install additional  prerequisite applications (am I using the right term here?) in order for  the main applications to be installed. If I were to later uninstall the  main application, would these secondary prerequisite applications be  uninstalled as well? If not, then I don't need them -- they will take up  unnecessary space -- then how will I track these prerequisites and  delete them?

- Just to clarify: if I install an application and then uninstall it, it  would leave no **trace** or **impact on performance** of the  computer? On Windows, registries tied to the program, even with the  program uninstalled, can still lurk around and slow down the computer  (especially if it accumulates as a result of installing and uninstalling  certain applications). 

- Is there a way for me to increase my mouse sensitivity? For some reason, even after setting the acceleration and sensitivity settings to as high as it will go, it had no impact on the speed of the cursor. Do I need to install a driver for the mouse? Do I need to manually install drivers for every hardware? Is there a way to match the cursor settings in Ubuntu from Windows 7?

- When there is a next version of Ubuntu coming up, how do I install it? Will I be able to keep everything I have? 

- Can I backup settings in Ubuntu? Create an image of the OS so that I will be able to restore everything exactly the way it was?

I have more questions to come, but they cannot be asked unless some of  the questions posted on this thread are answered.   

**Thanks, guys. This thread took me 30 minutes to compile a concise  list of questions and I hope it will be worth the time asking!**

---

### Post by Peter-E on 2010-08-14
> Previously, I installed Ubuntu 10.04 (32-bit) on an **external hard  drive** after I created 3 separate partitions: 
  4 gb for the swap partition (I have 4 gb of RAM and plan to use  hibernation), 
12 gb for the root partition
Why? The installer can do that for you

 > (I am a Windows user, but can I think of  the root partition as the equivalent of    
          Program Files?),
Not only that but more like c:\ 
  > 9 gb for the home partition in my external hard drive (can I think of  this as the equivalent of a D drive?)
There are many users that contradict each other. I personally have this on my PC.
Two 320 GB hard drives. One has Windows and the other has Ubuntu
GRUB cannot boot Windows, it uses the boot prerequisites stored on the Linux drive. In my case removing the Linux drive renders the PC not bootable unless I recreate the original Master Boot Record Windows used to use.

> I have at least 300 gb more space on the external hard drive, but right   now I'm just trying to learn Ubuntu and see approximately how much  space  I actually need for the root partition and then eventually  expanding  the home partition if I get familiar with Ubuntu/Linux and  begin to use  it as much as I use Windows.

Please do not try this. Expanding a Linux partition is taking an awful lot of time. You rather ask yourself "What do I need the space for?"

> The partitions are all formatted to **ext4** (I did some research and  thought this was the ideal format for Ubuntu) -- I have an irrelevant  question: _Ubuntu  10.04 says its default file system is ext4, but  what's the point of  having a default file system if the user needs to  select their own file  system to use for Ubuntu anyway?_ 
I use ext4 by default, the only reason to use ext2 once was by installing Ubuntu Netbook Remix on a USB stick as replacement for a defective internal SSD. Ext2 was chosen because it lacks journalling so saves a lot of extra write actions. USB sticks and SSD's alike do not like many write actions. There are many more formats to choose from but I would sugget to read about them all first.

> _My other OS, Windows 7, uses NTFS and I was wondering if ext4 and   NTFS can exchange files, both read/write, cleanly,safely, and   efficiently._ If not, I plan to create a FAT32 partition to be able   to transfer files from NTFS or ext4 to FAT32 and use FAT32 as the medium   to transfer files between Ubuntu and Windows 7._ Are there any more   efficient ways of transferring  files from both file systems  flawlessly?  I prefer not creating a FAT32 partition because I really  want to be  able to transfer files over 4 gb._
Ubuntu can read and write NTFS, FAT and FAT32. Windows cannot read ext4 and does not even see the partition at all, unless you use specially developped utilities in Windows. The only one I know of that actually works is a plugin in the Total Commander of Christian Gisler but you have read access only and need to run Windows as administrator.

OK some answers to the best of my knowledge,
I think your post is way too long - you should have split it, despite what you said in the start.
Good luck!
Peter

---

### Post by jmfal on 2010-08-14
You have alot of ???`s

usb hdd boot/boot menu: restart pc, pc logo or mobo logo sreen will come up somewhere it will say: to enter setup/bios press (delete or something else).

it will only be there for about 5 sec., it might also say: to enter boot menu press f12 or someother key, if you have manual for mobo?pc it should tell how to enter either.

boot menu should list all boot options eg.: 1: 1st hdd
                                            2: 2nd hdd
                                            3: cddvd
                                            4: usb-card reader
                                            5: usb
If usb hdd is plugged into card reader select card reader (use arrow keys, up/down to change selections, press enter to make selection).

Ubuntu releases run at 6mo cycle 10.04 the latest, next 10.10, 11.04 etc.

good luck

---

### Post by garycheng12 on 2010-08-14
> **Peter-E said:**
> Why? The installer can do that for you

 
Not only that but more like c:\ 
  
There are many users that contradict each other. I personally have this on my PC.
Two 320 GB hard drives. One has Windows and the other has Ubuntu
GRUB cannot boot Windows, it uses the boot prerequisites stored on the Linux drive. In my case removing the Linux drive renders the PC not bootable unless I recreate the original Master Boot Record Windows used to use.



Please do not try this. Expanding a Linux partition is taking an awful lot of time. You rather ask yourself "What do I need the space for?"


I use ext4 by default, the only reason to use ext2 once was by installing Ubuntu Netbook Remix on a USB stick as replacement for a defective internal SSD. Ext2 was chosen because it lacks journalling so saves a lot of extra write actions. USB sticks and SSD's alike do not like many write actions. There are many more formats to choose from but I would sugget to read about them all first.


Ubuntu can read and write NTFS, FAT and FAT32. Windows cannot read ext4 and does not even see the partition at all, unless you use specially developped utilities in Windows. The only one I know of that actually works is a plugin in the Total Commander of Christian Gisler but you have read access only and need to run Windows as administrator.

OK some answers to the best of my knowledge,
I think your post is way too long - you should have split it, despite what you said in the start.
Good luck!
Peter


Yay, I am able to trim the original thread down a few lines... lol. I originally said I might expand the Linux home partition because I didn't want people to waste time questioning why I have so little space to store my personal data and then lecture about what a home partition actually is. 

Anyway, whatever is in the thread now are still remaining questions to everyone else reading this.

Right now, I'm just going to decide whether to have Ubuntu on ext4 and use a FAT32 partition as the medium to transfer files or have Ubuntu on NTFS, which seems like an obvious choice but I think ext4 is capable of much more.

---

### Post by Peter-E on 2010-08-14
> **How to be able to select which OS to boot on startup?**

Before I forget:D

There is a simple System management tool called Startup Manager that can be installed from the Ubuntu Software Centre. With it, you can set the preferred OS to boot when you start your PC. 

Peter

---

### Post by garycheng12 on 2010-08-14
> **jmfal said:**
> You have alot of ???`s

usb hdd boot/boot menu: restart pc, pc logo or mobo logo sreen will come up somewhere it will say: to enter setup/bios press (delete or something else).

it will only be there for about 5 sec., it might also say: to enter boot menu press f12 or someother key, if you have manual for mobo?pc it should tell how to enter either.

boot menu should list all boot options eg.: 1: 1st hdd
                                            2: 2nd hdd
                                            3: cddvd
                                            4: usb-card reader
                                            5: usb
If usb hdd is plugged into card reader select card reader (use arrow keys, up/down to change selections, press enter to make selection).


I understand that (it is the method I'm using right now), but this method requires me to manually unplug and replug the external hard drive to either boot Ubuntu or boot Windows 7. I use a dock for the external hard drive, so I am looking for a way  to select which OS to boot off a menu when prompt by the boot loader, much like using a system that is setup to dual-boot between two OS -- you have the ability to select the OS to boot off a menu. The problem is this is not really the traditional way to dual-boot because Ubuntu is on an external hard drive.

---

### Post by Peter-E on 2010-08-14
> Right now, I'm just going to decide whether to have Ubuntu on ext4 and  use a FAT32 partition as the medium to transfer files or have Ubuntu on  NTFS, which seems like an obvious choice but I think ext4 is capable of  much more. 	

You cannot install Linux on an NTFS partition!
Please read this article on Wikipedia about Linux partitions:
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Peter

---

### Post by garycheng12 on 2010-08-14
> **Peter-E said:**
> Before I forget:D

There is a simple System management tool called Startup Manager that can be installed from the Ubuntu Software Centre. With it, you can set the preferred OS to boot when you start your PC. 

Peter

In my scenario, I don't have the menu at all -- when my PC is restarted, Ubuntu from the already plugged in external hard drive is automatically booted (since the external hard drive has first priority set up by the bios, while my internal hard drive with Windows installed is 2nd priority). Does the Startup Manager EDIT the menu or does it CREATE the menu as well?? Either way, I am glad to know that the menu is highly customizable =).

---

### Post by garycheng12 on 2010-08-14
> **Peter-E said:**
> You cannot install Linux on an NTFS partition!
Please read this article on Wikipedia about Linux partitions:
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

Peter

Oh wow, that changes EVERYTHING lol. FAT32 works with Linux though, right? Oh well, I think the ext4 for Ubuntu gives it some performance boost over FAT32.

---

### Post by Peter-E on 2010-08-14
> **garycheng12 said:**
> Oh wow, that changes EVERYTHING lol. FAT32 works with Linux though, right? Oh well, I think the ext4 for Ubuntu gives it some performance boost over FAT32.

Again no, NTFS, Fat32 and FAT are propriety file systems of Microsoft. Linux can read them, write to them but not use them as a file system for the OS. Maybe I I should have given you this link;
[http://en.wikipedia.org/wiki/List_of_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems)
It was, however, available at the end of the page of my previous one.

Please read the page and amaze yourself on howmany different operating systems and corresponding file/disk systems there are.

> In my scenario, I don't have the menu at all -- when my PC is restarted,  Ubuntu from the already plugged in external hard drive is automatically  booted (since the external hard drive has first priority set up by the  bios, while my internal hard drive with Windows installed is 2nd  priority). Does the Startup Manager EDIT the menu or does it CREATE the  menu as well?? Either way, I am glad to know that the menu is highly  customizable =). 	

Which is correct, if you have set the BIOS to a boot order that accesses the USB drive prior to booting from the hard disk. 

Windows MUST boot from a primary partition, Linux can be booted from either a primary or an extended partition. In your case you won't see GRUB at all for it resides on the external disk. Normally, installing on Windows based systems, the MBR is overwritten by GRUB so a boot menu appears that let you choose between Ubuntu and Windows. The default is then Ubuntu with a countdown timer that waits 10 seconds by default to boot. When a key is pressed, the countdown stops and you are able to choose another OS. As I said before, GRUB stores the startup menu in Linux and calls a chainloader to boot Windows. In fact, the default scenario is: A PC with one disk running Windows is booted from an Ubuntu CD. During setup you can use a partitionig tool called Gparted to resize the Windows partiton, so empty and unallocated disk space emerges. You can then point to that unallocated space to install Linux. It creates 2 partitions, one for the OS and one for swap. You do not have to define the sizes, the swap size depends on the availble memory, like the windows pagefile.
The boot order can be changed in Ubuntu by either directly editing the GRUB menu settings using a text editor like gedit or by using the GUI driven application I mentioned before.

I hope this clarifies for you.

Best regards,
Peter

---

### Post by GaryRixon on 2010-08-14
Just use wubi. That has always worked for me, well it did back in the good old days when my xp machine still actually worked. Whenever you start up your machine (presuming you have installed wubi correctly) It will come up with the options to boot to either ubuntu or whichever version of windoze you are using.

Hope this Helps

---

