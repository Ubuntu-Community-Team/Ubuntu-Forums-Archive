---
title: "Switching from One HD to Two"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by yes9111 on 2007-11-30
Hi!

I have a 150 GB hard disk as my Primary Master disk, that was partitioned & configured so that it would dualboot Windows XP and Ubuntu.  (GRUB for the boot-loader)  Then I received a 500GB hard disk that I connected and comes up as the Secondary Master.  

In Windows, it's C: drive for the 150GB and I: (upper case i) for the new 500GB drive.
I have already backed up my files
so all I need is to make the 500GB hard drive the default drive to boot with Windows XP
and Ubuntu now taking the whole 150GB drive up.

Anyway to configure this so that I can select which one to boot using GRUB?
(Or some other method if there is one?)

Both disks are SATA btw.

---

### Post by Herman on 2007-11-30
>  (Or some other method if there is one?)Hello yes9111,
I am using a different approach and it's working really well for me so far. I have one drive with all my operating systems on it and the other drive has all the data in it.
I don't have Windows at all in this computer, I have Ubuntu Feisty and Ubuntu Gutsy, Debian and OpenSuSe.
Each operating system has a folder i my /home/username folder named DATA and the data hard drive is mounted in that in each system, so it's quite convenient to access.

Otherwise I recommend you read this thread: [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902"), and this one as well, [**Trying to Dual Boot, using two HD's**]("http://www.ubuntuforums.org/showthread.php?t=120994").Particularly note post #6. :)

You should check your Windows EULA before you copy Windows or re-install it to a different hard drive. I'm not sure, but I was under the impression that once you install Windows and register it to a hard drive, they'll have your hard disk ID number in their database files somewhere and you could get in trouble for that, (theoretically at least). It might make flashing lights and sirens go off at Microsoft headquarters next time you go to do a Windows Update! :lolflag:
I know all that legal stuff is boring reading. You need to be a lawyer to make much sense of it.  That;s one good reason not to have Windows in our computers at all. 

Regards, Herman :)

---

### Post by yes9111 on 2007-12-01
Lol. Thank you for the links
The problem with using one hard drive for data for both Windows and Linux is that Windows and Linux's path names are different.. ( C:\Documents and Settings VS /home/username/)

---

### Post by Herman on 2007-12-01
Oh, sorry, I forgot, you can't just mount anything where you want in Windows, you have to go into 'My Computer' and find the icon to open the drive you're looking for don't you? Yes, I suppose that would be quite inconvenient.

---

### Post by froy02 on 2007-12-01
What you want to do won't be easy. If it is just windows installed in one hard drive all you have to do is use the utility that came with your new hd to clone your windows XP and you boot with your new drive. your windows XP will be bot like nothing happened.
But  since you're dual boot the MBR is different, it has grub in there. So then you have restore the MBR then fix your XP with the installation CD.  That's just the problem with XP.
Now you have to modify the 150gb grub so that it would boot with choice of XP or ubuntu.  Not an easy task either.
It is actually better to have your OS's in 1 small drive and use the 500gb for data formatted as NTFS because ubuntu and XP can read both formats.
I only use an 80 gb HD for both XP and Ubuntu because all my data is on a 300 gb HD formatted ntfs.  It does not matter which OS I choose, I still access my 2nd HD.

Don't get me wrong, it could be done but it not be easy.

---

### Post by svetlin on 2007-12-02
> **froy02 said:**
> formatted as NTFS because ubuntu and XP can read both formats

or format as ext3 and install [http://www.fs-driver.org/]("http://www.fs-driver.org/")

From the site:
> extends the Windows NT/2000/XP/2003 operating system to include the Ext2 file system

---

### Post by bluedragon436 on 2007-12-02
I guess it is sort of a pain in the butt to do it this way, but on my desktop I have dual SATA HD's and I just use the boot option that is usually incorporated in the Bios to choose which HD (also which OS) I boot from, and both OS's can see the other so I can get to my music and such when using the other OS....  I am sure there is another, possibly even easier way, but this only takes an extra second for me to do so it will work just fine for me...

---

### Post by meierfra on 2007-12-02
> Anyway to configure this so that I can select which one to boot using GRUB?

Sure and it is fairly easy.  You just need to   edit one file and maybe reinstall grub. 
Boot from ubuntu, open a terminal (Applications->Accessories->Terminal) and post  the  output of 

```
sudo fdisk -l
```
and
```
 cat /boot/grub/menu.lst 
```
( both "l" are lowercase L)


With that information I can give you detailed instruction. If you are worried how much  is involved click on "DualTwo" in my signatures to see what the instruction might  look like.

---

### Post by yes9111 on 2007-12-02
Thank you for all your help :KS

I finally got the two drive dual boot to work. >=]
But I'm still curious about the OSes on one disk and the data on the other..
I don't think Windows can detect partitions on the drive - or can it?
So if I used the 500GB disk as a data drive, Would it then in windows be mounted as Documents and Settings and /home for Linux?
or would it be like only the \windows folder in the 150GB hard disk and everything but the /home directory in Linux?

> **bluedragon436 said:**
> I guess it is sort of a pain in the butt to do it this way, but on my desktop I have dual SATA HD's and I just use the boot option that is usually incorporated in the Bios to choose which HD (also which OS) I boot from, and both OS's can see the other so I can get to my music and such when using the other OS....  I am sure there is another, possibly even easier way, but this only takes an extra second for me to do so it will work just fine for me...

I tried to do this but because the 500GB (One with Windows installed) is the secondary master, it will have to write some startup files to the 150GB one (Primary Master).  So when I try and boot w/ the 500GB one, it won't detect the startup files which are actually located in the 150GB drive. 

It's all fixed now though - the Grub correctly detected Windows =D 
Help on the 500GB as data and 150GB as OSes would be great (how to mount etc..)

---

### Post by Herman on 2007-12-02
If you made a shared data partition somewhere that had a file system in it that Windows can recognize, such as FAT32 or NTFS, probably when you boot Windows you'll see that 'found new hardware' sign. Windows will probably want you to reboot to install the new hardware. After that you might find an icon for new drive in 'My Computer'. 
You could probably make a shortcut for it in your 'My Documents' folder if you wanted easier access to it, I guess.

In Ubuntu if the partition is already made before Ubuntu is installed, it will probably be automatically added to your /etc/fstab file and you will have an icon for it on your Desktop, which is quite convenient. Otherwise you would mount it yourself in any directory you like. Usually we mount other file systems in /mnt or /media. If it's mounted in /media then it will be given an icon on your Desktop.
If you need to mount it yourself, here's the web page I made about that, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").

It wouldn't really matter where the shared data partition is, on the same hard disk or another hard disk. Gutsy Gibbon can read and write to NTFS now, so it wouldn't matter if you made it NTFS or FAT32. I still prefer FAT23 because I still think it's a little more reliable and versatile, but many people seem to like NTFS for some reason.


Dual or multiple booting is great because we can learn about other operating systems. The problem is, when we keep data in two systems, it can become hard to keep track of our files. The biggest problem is knowing which files are the up to date ones and refraining from adding new information to an older file. Then when your files are combined at some later stage you lose the intermediate information you recorded if you have a file in both operating systems that has the same file name.

Regards, Herman :)

---

### Post by yes9111 on 2007-12-02
Thanks =D
Now I got another question
Some of my music files contain Asian language characters in the file names and in Windows I can't do anything with them, not even deleting them!
The Data Disk (500GB) is a Ext2 partition (I installed the Ext2 FS driver for MS XP)
Do I have to configure this in Ubuntu somehow so that the Ext2 filesystem can support asian text?  
Korean and Chinese to be exact

---

### Post by Herman on 2007-12-02
I have read bad reports about Windows support for ext file systems. I haven't tested it myself, but personally, from what I have read, you are taking a risk!

Most people would trust Linux's NTFS support a long time before they would trust Window's ext support.

The FAT32 file system is better established between both operating systems and would be much safer for you to trust your files with.

As for the Asian characters, I have no experience with those either, but I do remember that when installing Ubuntu with the 'Alternate' CD, when you choose your keyboard type, there are Asian looking characters in the list. I don't know how to change Ubuntu after is is already installed, but I would look somewhere in 'System'-->'Administration'-->'Keyboard', and try to find the settings in there somewhere.
If that doesn't work I would look in 'System'-->'Administration'-->'Synaptic Package Manager', and try to find the right fonts and any other appropriate software packages to be downloaded and installed to enable your Ubuntu operating system with that capacity. I haven't looked yet myself, perhaps I'm being optomistic here, but it would eb worth a look. 
Otherwise, post a new thread with the same question and someone who knows all about that might see it and offer you expert help.

I just found this link that might help you but I haven't got time to read it right now as my lunchbreak is almost over, 
**[[B]Ubuntu** CJK Chinese Japanese Korean Input Guide]("http://www.mrbass.org/linux/ubuntu/scim/")[/B]


Regards, Herman :)

---

### Post by Herman on 2007-12-03
> Some of my music files contain Asian language characters in the file names and in Windows I can't do anything with them, not even deleting them! I was presuming you have a taste for Chinese or Korean music, and the music files already had the asian file names before you copied them there.

If not then I would say that Windows has already corrupted your ext file system. The strange fonts can be a symptom of file system corruption.

I hope not.
Regards, Herman

---

### Post by svetlin on 2007-12-03
I think the problem is with Windows, not with the ext2. I can create, edit and read files with chinese names ( like &#38405;&#35272;&#38543;&#26102;&#26356;&#26032;&#30340;&#26032;&#38395;.txt, don't know what it means) in Kubuntu, but not in Windows.

---

### Post by bluedragon436 on 2007-12-08
I haven't had any issues running the setup like I have mine....I didn't do anything as far as startup files or anything....my 120gb has Windows and the 250gb has Ubuntu...and I can get to all of my files from Windows on Ubuntu doubt I can do the other way around...but so far everything is working just fine for me.....now I can run Ubuntu all the time and still be able to play games using Windows...on the same computer.... gaming is the only reason I still even have Windows....One day though Ubuntu will take over....can't wait!!!

---

